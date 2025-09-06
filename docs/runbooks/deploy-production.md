


# Runbook: Despliegue a producción

## 🎯 Objetivo
Ejecutar un **deploy seguro** a producción (Vercel) desde la rama `main`, con validaciones previas y verificación posterior.

---

## 🧭 Requisitos previos
- Acceso a **GitHub** (repo LinkAidly), **Vercel** (proyecto web) y **Cloudflare** (DNS).
- Variables de entorno configuradas en Vercel (Production) — nada sensible en el repo.
- `node` y `npm` instalados localmente.

---

## 🪜 Pasos

### 1) Pre‑deploy (local / CI)
1. Actualiza y valida `dev`:
   ```bash
   git checkout dev
   git pull --rebase
   npm ci
   npm run lint && npm run build
   npm run docs
   ```
2. Revisa que el TypeDoc no tenga warnings críticos y que los tests (si existen) pasen.
3. Verifica **Plausible** (eventos principales presentes en `lib/analytics.ts`).
4. Verifica **SEO/OG** en `app/layout.tsx` y `app/sitemap.ts`.

### 2) Merge de `dev` → `main`
1. Crea un PR de `dev` hacia `main` (asegúrate de que CI esté en verde).
2. Etiqueta versión en CHANGELOG (`docs/CHANGELOG.md`) y crea tag si procede:
   ```bash
   git checkout main && git pull --rebase
   git tag vX.Y.Z -m "release: vX.Y.Z"
   git push origin vX.Y.Z
   ```

### 3) Despliegue en Vercel
1. Al mergear a `main`, Vercel **despliega automáticamente**.
2. En Vercel → *Project* → *Deployments* verifica que el último deploy está **Ready**.
3. Revisa variables de entorno de Production en *Settings > Environment Variables*.

### 4) Verificación post‑deploy
1. **Smoke test** en `https://linkaidly.org`:
   - Landing carga sin errores.
   - Enlaces principales (Mapa, Impacto, Misión, Donar) funcionan.
   - Páginas legales accesibles.
2. **SEO**
   - `robots.txt` y `sitemap.xml` accesibles.
   - Etiquetas OG/meta presentes en el HTML.
3. **Seguridad**
   - Certificado TLS válido.
   - Cabeceras (CSP, HSTS) activas.
4. **Analítica**
   - Verifica hits en Plausible.

### 5) Comunicación
- Anota la release en `docs/CHANGELOG.md` y comparte el enlace de producción.
- Si aplica, publica nota breve en redes.

---

## 🔁 Rollback
Si detectas un problema severo:
1. En Vercel → *Deployments*, selecciona el **deploy previo** y pulsa **Promote to Production**.
2. Abre un issue/PR con etiqueta `hotfix` y documenta la causa.

---

## ✅ Checklist
- [ ] `dev` actualizado y build OK.
- [ ] TypeDoc sin warnings relevantes (`npm run docs`).
- [ ] SEO/OG revisado.
- [ ] Variables de entorno comprobadas en Vercel (Production).
- [ ] Merge `dev` → `main` confirmado.
- [ ] Deploy en Vercel en estado **Ready**.
- [ ] Smoke tests en producción OK.
- [ ] Plausible registra eventos.
- [ ] CHANGELOG actualizado.

---

## 🧯 Troubleshooting
- **404 en páginas** → Revisar rutas del App Router y `sitemap.ts`.
- **OG no aparece en redes** → Revalidar el caché del crawler (Facebook Debugger / Twitter Validator), confirmar `<meta>` en HTML.
- **CSP bloquea recursos** → Ajustar directivas en cabecera; validar en consola.
- **Eventos Plausible no llegan** → Confirmar script y dominio en `lib/analytics.ts` y en Plausible.
- **Certificado inválido** → Revisar configuración de dominio en Vercel y DNS en Cloudflare.

---

## 📚 Referencias
- [Vercel — Deployments](https://vercel.com/docs/deployments)
- [Next.js — Production Checklist](https://nextjs.org/docs/advanced-features/measuring-performance)
- [Cloudflare — DNS](https://developers.cloudflare.com/dns/)
- [Plausible Analytics](https://plausible.io/docs)