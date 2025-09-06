# Arquitectura — LinkAidly (MVP → Escalado)

> **Estado:** MVP en producción  
> **Última actualización:** 2025‑08‑19  
> **Alcance:** Describe cómo está construida la app hoy (MVP) y el camino de escalado previsto. Complementa a `docs/infra.md`, `docs/security.md` y `docs/tech-notes.md`.

---

## 1) Vista rápida

- **Frontend**: Next.js 15 (App Router) + TypeScript + Tailwind v4, ubicado en `web/`.
- **Hosting**: Vercel (prod desde `main`, preview desde PRs).
- **DNS/WAF/CDN**: Cloudflare (DNS; proxy desactivado en registros hacia Vercel).
- **Analítica**: Plausible (cookieless; pendiente de alta; integración vía <script> en `app/layout.tsx` cuando se active).
- **PWA**: `manifest.json` + `public/sw.js` (PWA mínima en MVP; ver sección 8).
- **Contenido**: estático en `web/public/data/*.json` (misiones, acciones, donaciones, transparencia).
- **Seguridad básica**: cabeceras en Next (`CSP`, `HSTS` via Cloudflare, `X-Frame-Options: DENY`, etc.).

---

## 2) Diagrama (alto nivel)

```
Usuario (móvil/desktop)
        │
        ▼
   Cloudflare DNS ───────────────> Vercel (SSR/SSG/ISR Next.js)
        │                                   │
        │ (futuro) CDN/Workers              ├── Static assets (/.next/static, /public)
        │                                   └── JSON de contenido (/public/data/*.json)
        │
        └─ Subdominios: 
             • linkaidly.org  → prod (main)
             • dev.linkaidly.org → preproducción (dev)
             • beta.linkaidly.org → alternativo/ensayos (opcional)
```

---

## 3) Estructura relevante del repositorio

```
/web
  /public
    /data
      actions.json
      donations.json
      missions.json
      transparency.json
    /img
    manifest.json
    sw.js
  /src
    /app
      layout.tsx
      page.tsx            # Coming soon
      /etica/page.tsx     # Marco ético (modal/section)
      globals.css         # (antes en /styles; ahora aquí)
    /components
      Button.tsx
      ThemeToggle.tsx
  next.config.mjs
  package.json
/docs
  README.md
  architecture.md
  infra.md
  security.md
  tech-notes.md
```

---

## 4) Flujo de petición (MVP)

1. **DNS**: Cloudflare resuelve `A/AAAA` (o CNAME) hacia Vercel. Proxy **apagado** (naranja → gris) para evitar conflicto de certificados.
2. **TLS**: Vercel sirve HTTPS (Let’s Encrypt). En Cloudflare, SSL/TLS en **Full (strict)**.
3. **Render**:
   - Rutas estáticas (`/`) se **prerenderizan** (Static).
   - Rutas futuras (juego/mapa) podrán usar SSG/ISR.
4. **Assets**: `.next/static` + `/public/*` cacheados por Vercel/CDN.
5. **PWA**: con Service Worker básico (`sw.js` en `/public`):
   - Cache‑first para shell y assets estáticos.
   - Network‑first para `/data/*.json`.
6. **Analítica**: eventos ligeros a Plausible (sin PII). *Pendiente de integración*.

---

## 5) Entornos y ramas

- **main → producción** (`linkaidly.org`)
- **dev → preproducción** (`dev.linkaidly.org`)
- **feature/*** → PRs con previews de Vercel

Regla: _feature → PR a `dev`_ ; cuando esté listo, `dev → main`.

---

## 6) Configuración (variables y secretos)

> **Estado actual:** no se requiere `.env` para el MVP (sin integraciones con secretos). El archivo `.env.example` queda **planificado** para fases futuras.

Archivo `web/.env.example` (crear si no existe):

```
# Analítica (si se autoalojara Plausible en el futuro)
PLAUSIBLE_DOMAIN=linkaidly.org
PLAUSIBLE_API_URL=https://plausible.io   # o tu dominio self-host

# (Futuro) Back-end
NEXT_PUBLIC_API_BASE=https://api.linkaidly.org
```

> **Nota:** no subir `.env`. Mantener secretos en **Vercel → Project Settings → Environment Variables** (Production / Preview / Development).

---

## 7) Datos y esquemas (MVP)

Cada JSON bajo `web/public/data` debe cumplir un esquema estable para facilitar migración a BBDD (p. ej. Supabase) sin sorpresas.

**7.1 `missions.json`** (ejemplo mínimo)

```json
[
  {
    "id": "gaza-agua-01",
    "zone": "Gaza",
    "type": "agua",
    "title": "Traer agua segura",
    "time_limit_s": 90,
    "assets": { "sprite": "jarra.webp", "obstacles": 3 },
    "copy": {
      "intro": "Arrastra la jarra desde el pozo hasta la casa evitando obstáculos.",
      "success": "¡Misión completada!",
      "fail": "Inténtalo de nuevo. Evita los obstáculos."
    }
  }
]
```

**7.2 `donations.json`** (con caducidad y allowlist en cliente)

```json
[
  {
    "id": "ong-001",
    "org_name": "Entidad legal",
    "purpose": "Agua y alimentos",
    "url": "https://ejemplo.org/campana",
    "qr": "/img/qr/ong-001.png",
    "reviewed_at": "2025-09-12",
    "expires_at": "2025-11-12",
    "notes": "Verificada públicamente"
  }
]
```

**7.3 `actions.json`**

```json
[
  {
    "id": "act-001",
    "title": "Carta a tu representante",
    "description": "Pide la entrada de ayuda humanitaria.",
    "url": "https://ejemplo.org/carta",
    "source": "Colectivo verificado",
    "active_until": "2025-12-31"
  }
]
```

**7.4 `transparency.json`**

```json
[
  {
    "date": "2025-09-01",
    "target": "Alias Gaza Cocina",
    "amount_estimate": 2500,
    "method": "Transferencia",
    "notes": "Estimación agregada"
  }
]
```

> **Validación**: ver `docs/security.md` para ejemplos de validación con Zod y allowlist de dominios de donación/acción.

---

## 8) PWA

- **manifest.json** con `name`, `short_name`, `icons 192/512`, `theme_color`, `background_color`.
- **Service Worker (`/public/sw.js`)**:
  - Implementado en el MVP.
  - Cache‑first para shell y assets estáticos.
  - Network‑first para `/data/*.json`.
  - Las peticiones `POST` y rutas `/api/*` no se cachean.
  - Aviso de actualización disponible (banner) cuando haya nuevo SW.

---

## 9) Seguridad (resumen — ver `docs/security.md` para detalle)

- **CSP** estricta (solo `self` + analytics).  
- **Frame-ancestors 'none'** (anti‑clickjacking).  
- **Referrer-Policy**: `strict-origin-when-cross-origin`.  
- **Permissions-Policy**: sin geoloc/cámara/micrófono.  
- **HSTS** vía Cloudflare (activar tras verificar HTTPS estable).  
- **Sanitización** de copys e imágenes sin EXIF.  
- **security.txt** publicado en `/.well-known/security.txt`.  
- Más detalle y roadmap en `docs/security.md`.

---

## 10) Despliegue

- **Automático** vía Vercel:
  - PR → Preview.
  - `dev` → `dev.linkaidly.org`.
  - `main` → `linkaidly.org`.
- **Rollback**: desde Vercel → “Promote previous deploy”.
- **Export estático** (futuro espejo): `next export` a un bucket/CDN, si se requiere.

---

## 11) Monitorización

- **Uptime**: UptimeRobot sobre `linkaidly.org` y `dev.linkaidly.org`.
- **Rendimiento**: Vercel Analytics + Lighthouse CI (futuro).
- **Errores cliente**: Sentry (pendiente).
- **Eventos**: Plausible con `mission_started`, `mission_completed`, `donate_click`, `action_click`.

---

## 12) Roadmap técnico (resumen)

**Fase 1 — MVP**
- Coming‑soon estable, paleta/typo aplicada, ruta de “Marco ético”.
- DNS + HTTPS + HSTS.
- JSON de contenido base.
- Documentación inicial (estos docs).

**Fase 2 — Contenido y juego**
- Mapa + 1–3 misiones en Phaser (escenas modulares).
- Cápsulas culturales asociadas.
- Donaciones/acciones con verificación y caducidad.

**Fase 3 — Servicios**
- Migración JSON → **Supabase** (Postgres + Auth + Storage) en UE.
- Backoffice ligero para revisión de campañas/cápsulas.
- Rate‑limit y políticas RLS.

**Fase 4 — Comunidad**
- UGC (cápsulas de diáspora) con moderación previa.
- Panel de métricas internas.

---

## 13) Decisiones de arquitectura (ADR-lite)

- **Next.js + Vercel** por velocidad de entrega y previews (2025‑08). → ver [ADR-0001](adr/ADR-0001-frontend-framework.md)
- **Tailwind v4 con tokens en CSS** para rapidez y consistencia. → ver [ADR-0002](adr/ADR-0002-styling.md)
- **Documentación API con TypeDoc + TSDoc**. → ver [ADR-0003](adr/ADR-0003-docs-api.md)
- **Analítica ética con Plausible**. → ver [ADR-0004](adr/ADR-0004-analytics.md)
- **Allowlist de dominios externos** para enlaces de donación/acción. → ver [ADR-0005](adr/ADR-0005-allowlist.md)
- **Seguridad mínima (baseline)** con CSP, HTTPS y validación Zod. → ver [ADR-0006](adr/ADR-0006-security-baseline.md)
- **JSON estático** para MVP; minimizar complejidad inicial.
- **Cloudflare solo DNS** (sin proxy a Vercel) para evitar problemas de TLS.
- **Sin cuentas de usuario** en MVP (minimización de datos).

> Revisión trimestral de estas decisiones; ver también ADRs en `docs/adr/`.

---

## 14) Checklists

**Pre‑merge a `main`**
- [ ] Lint + build OK en CI.
- [ ] Previsualización de Vercel sin errores.
- [ ] Accesibilidad básica (focus visible, contraste).
- [ ] SEO/OG verificado (título, descripción, `og:image`).
- [ ] Imagen social `public/og_default.png` válida (1200×630, < 300 KB).
- [ ] `sitemap.xml` y `robots.txt` accesibles en producción.
- [ ] `/.well-known/security.txt` publicado y vigente.
- [ ] Revisados enlaces externos (donaciones/acciones).
- [ ] Changelog breve en PR.

**Post‑deploy**
- [ ] Smoke test en móvil y desktop.
- [ ] Headers de seguridad verificados.
- [ ] Sin errores en consola.
- [ ] Uptime monitor OK.

---

## 15) Enlaces

- Infraestructura: `docs/infra.md`  
- Seguridad y cumplimiento: `docs/security.md`  
- Notas técnicas / ADR: `docs/tech-notes.md`

---

## 📚 Referencias externas
- [Vercel docs](https://vercel.com/docs)
- [Cloudflare docs](https://developers.cloudflare.com/)
- [Supabase docs](https://supabase.com/docs)
- [OWASP Top 10](https://owasp.org/www-project-top-ten/)
