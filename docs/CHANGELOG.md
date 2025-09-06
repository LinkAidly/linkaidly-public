# Changelog — LinkAidly

Este archivo sigue el formato [Keep a Changelog](https://keepachangelog.com/es-ES/1.0.0/) y Versionado Semántico.

## [Unreleased]
### Added
- Estructura inicial de documentación (`/docs`).
- Configuración de Next.js + Tailwind v4.
- Páginas legales (Privacidad, Cookies, Términos).
- SEO/OG básico en `layout.tsx`.
- `sitemap.ts` y referencia en `robots.ts`.
- `/.well-known/security.txt` publicado.
- PWA mínima (manifest + Service Worker básico).

### Planned — 0.2.0 (MVP)
- 🎮 **Misiones**: primera misión jugable con slug dinámico (`/mision/[slug]`).
- 🎓 **Cápsulas**: contenido cultural educativo con imágenes y fuentes verificadas.
- 💸 **Donaciones**: integración inicial de métodos de donación con validación por allowlist.
- 📊 **Transparencia**: secciones con KPIs simulados y bucketización de métricas.
- 🗺️ **Mapa interactivo**: prototipo básico con clics y zonas.
- 🔐 **Seguridad reforzada**: CSP afinado, headers adicionales y validación extendida.
- 🧪 **Testing**: configuración inicial de tests automáticos en CI.

### Changed
- Refactor de componentes de UI para unificar estilos con tokens.
- Ajustes en `ThemeProvider` y `ThemeToggle` para consistencia entre dark/light mode.
- Mejoras en documentación de ADRs y `docs/*` siguiendo la guía de estilo.

### Fixed
- Corrección de warnings de TypeDoc eliminando enlaces no resueltos.
- Ajustes en `robots.ts` y `sitemap.ts` para mejorar indexación.
- Corrección de estilos en modo oscuro en botones y links.

## [0.1.0] - 2025-09-07
### Added
- Primera versión del proyecto publicada como *Coming Soon*.
- Despliegue en Vercel con dominio `linkaidly.org`.
- Infraestructura documentada en `/docs` (architecture, infra, security, process).
- ADRs iniciales (0001–0006) y plantilla de ADR.
- Estilo consistente en documentación (`styleguide.md`).
- Configuración de Typedoc + TSDoc para API en `/web/docs/api`.

[Unreleased]: https://github.com/LinkAidly/linkaidly/compare/v0.1.0...HEAD
[0.1.0]: https://github.com/LinkAidly/linkaidly/releases/tag/v0.1.0