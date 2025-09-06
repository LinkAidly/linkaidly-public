# 🧑‍💻 Notas técnicas — LinkAidly

Este archivo recoge notas técnicas vivas, decisiones puntuales y cambios relevantes del proyecto.  
Actualizar con cada cambio importante para mantener un historial claro y accesible.

---

## 🟢 Decisiones iniciales
- **Framework:** Next.js 15 + TypeScript + TailwindCSS.  
- **Gestión de estado:** useState para interactividad mínima en el MVP.  
- **Repositorio:** GitHub privado con ramas `main` (producción) y `dev` (integración).  
- **Deploy:** Vercel conectado a `main` y `dev`.  

## 📌 Cambios relevantes
- [x] 2025-08-18: Instalado scaffold de Next.js en subcarpeta `/web`.
- [x] 2025-08-18: Integración de Tailwind v4 y tokens de diseño (colores, tipografía Montserrat).
- [x] 2025-08-18: Configuración inicial de Cloudflare para dominio `linkaidly.org` con subdominio `dev.linkaidly.org`.
- [x] 2025-08-20: Configurado SEO/OG en `layout.tsx`.
- [x] 2025-08-21: Añadido `sitemap.ts` y referencia en `robots.ts`.
- [x] 2025-08-22: Creado `/.well-known/security.txt`.
- [x] 2025-08-23: Documentación actualizada de PWA (MVP con SW).

## ⏳ Pendiente
- [x] Integrar sistema de captura de emails (Formspree o alternativa).
- [ ] Añadir Plausible para analítica ética.
- [ ] Definir licencia definitiva (MIT, GPL, propietario).
- [ ] Configurar CI/CD más robusto con tests automáticos.

---
## 📚 Referencias externas
- [Next.js Docs](https://nextjs.org/docs)
- [TailwindCSS Docs](https://tailwindcss.com/docs)
- [Cloudflare Docs](https://developers.cloudflare.com/)
- [Plausible Analytics](https://plausible.io/docs)
- [Formspree](https://formspree.io/)
