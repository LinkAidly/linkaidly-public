# Arquitectura — LinkAidly (visión de alto nivel)

> **Estado:** MVP en producción  
> **Última actualización:** 2025‑09‑06  
> **Alcance:** Resumen público de cómo está construida la plataforma hoy y el camino de evolución. Documento de **alto nivel**, sin detalles operativos internos.

---

## 1) Vista rápida

- **Frontend:** Next.js 15 (App Router) + React 19 + TypeScript + Tailwind CSS v4.  
- **Alojamiento:** Vercel (build y despliegues automáticos).  
- **DNS/CDN:** Cloudflare (DNS; posibilidad de CDN/edge más adelante).  
- **Analítica ética:** Plausible (cookieless).  
- **PWA:** Manifest + Service Worker sencillo.  
- **Contenido (MVP):** ficheros JSON curados (misiones, donaciones, acciones, transparencia).  
- **Sin cuentas de usuario:** minimización de datos por diseño.

---

## 2) Diagrama (alto nivel)

```
Usuario (web)
   │
   ▼
 DNS (Cloudflare) ──▶ Hosting (Vercel - Next.js)
                           ├─ Páginas y componentes
                           ├─ Assets estáticos
                           └─ Contenido JSON curado
```

> En el futuro se contempla un **backend ligero** (por ejemplo, Postgres gestionado con Supabase) para pasar de JSON estático a datos persistentes con revisiones y auditoría.

---

## 3) Principios de diseño

- **Simplicidad primero:** MVP sin complejidad innecesaria.  
- **Transparencia y ética:** decisiones técnicas alineadas con el propósito social.  
- **Accesibilidad:** contrastes, foco visible, semántica.  
- **Privacidad por defecto:** no se recopilan datos personales; analítica sin PII.  
- **Evolución incremental:** cambios pequeños y verificables, con documentación (ADR).

---

## 4) Contenido y modelos (MVP)

En el MVP el contenido se sirve desde JSON curado y versionado. Ejemplos de entidades:

- **Misiones** (`missions.json`): minijuegos/retos con metadatos (zona, tipo, textos educativos).  
- **Donaciones** (`donations.json`): enlace verificado, notas de revisión y caducidad.  
- **Acciones** (`actions.json`): acciones cívicas (contacto institucional, campañas).  
- **Transparencia** (`transparency.json`): movimientos/entradas con fecha, objetivo y método.

> El uso de JSON facilita la curaduría y permite migrar después a base de datos sin rehacer lógica.

---

## 5) PWA (resumen)

- **Manifest** con nombre, iconos e identificación básica.  
- **Service Worker** sencillo: cache de shell y estáticos; red para datos recientes.  
- Objetivo: **mejorar la experiencia en móvil** y ofrecer funcionamiento básico sin conexión.

---

## 6) Seguridad (resumen)

- Cabeceras de seguridad y políticas de permisos conservadoras.  
- Política de **Contenido Seguro (CSP)** para limitar orígenes.  
- **Sin iframes de terceros** no necesarios (clickjacking).  
- **security.txt** publicado para canalizar reportes responsables.  

Más detalle en `docs/security.md`.

---

## 7) Despliegue y flujos

- Despliegues automáticos tras cambios verificados.  
- Previsualizaciones por rama para revisión antes de publicar.  
- Rollback sencillo a despliegues previos cuando sea necesario.

---

## 8) Roadmap técnico (resumen)

**Fase 1 — MVP**  
- Páginas públicas, paleta/tipografía, cápsulas y minijuegos iniciales.  
- Contenido JSON curado y validado.

**Fase 2 — Contenido y juego**  
- Mapa + 1–3 misiones modulares.  
- Cápsulas culturales asociadas.  
- Verificación y caducidad de campañas.

**Fase 3 — Servicios**  
- Migración JSON → **BBDD gestionada** (p. ej., Supabase en UE).  
- Backoffice ligero para revisión de campañas/cápsulas.

**Fase 4 — Comunidad**  
- Aportes moderados (UGC) y panel de métricas.

---

## 9) Decisiones y referencias

Decisiones técnicas documentadas como ADR (Architecture Decision Records):

- **Next.js + Vercel** por velocidad de entrega y previews → ver [ADR‑0001](adr/ADR-0001-frontend-framework.md)  
- **Tailwind v4** con tokens en CSS → ver [ADR‑0002](adr/ADR-0002-styling.md)  
- **Documentación técnica** con TypeDoc + TSDoc → ver [ADR‑0003](adr/ADR-0003-docs-api.md)  
- **Analítica ética** con Plausible → ver [ADR‑0004](adr/ADR-0004-analytics.md)  
- **Allowlist** de dominios externos (donaciones/acciones) → ver [ADR‑0005](adr/ADR-0005-allowlist.md)  
- **Seguridad de base** (CSP/HTTPS/validación) → ver [ADR‑0006](adr/ADR-0006-security-baseline.md)

---

## 10) Enlaces útiles

- **Seguridad y cumplimiento:** `docs/security.md`  
- **Guía de estilo de contenido:** `docs/styleguide.md`  
- **Design system (identidad visual):** `docs/design-system.md`