[![CI](https://github.com/LinkAidly/linkaidly/actions/workflows/ci.yml/badge.svg)](../../actions/workflows/ci.yml)
[![Dependabot](https://img.shields.io/badge/dependabot-enabled-brightgreen.svg)](../../network/updates)
![License: All Rights Reserved](https://img.shields.io/badge/License-All%20Rights%20Reserved-red.svg)

# 🌿 LinkAidly

**LinkAidly** es una iniciativa digital que combina **juego, cultura y acción solidaria**.  
El objetivo es transformar la atención en **apoyo real** a Palestina y otras causas sociales, con un enfoque de **transparencia, ética y accesibilidad**.

## 📖 Tabla de contenidos
- [🚀 Propósito](#-propósito)
- [📌 Roadmap](#-roadmap)
- [⚖️ Marco ético y legal](#️-marco-ético-y-legal)
- [🗂️ Organización del repo](#️-organización-del-repo)
- [🛠️ Stack técnico](#️-stack-técnico)
- [🤝 Contribución](#-contribución)
- [🧪 Testing y scripts](#-testing-y-scripts)
- [📚 Documentación adicional](#-documentación-adicional)
- [📄 Licencia](#-licencia)

---

## 🚀 Propósito
- Ofrecer una plataforma segura y sencilla donde las personas puedan:
  - **Jugar misiones** educativas.
  - Aprender con **cápsulas culturales**.
  - Apoyar mediante **donaciones verificadas** y **acciones legales**.
- Dar visibilidad a ONGs y colectivos con pocos recursos tecnológicos.

---

## 📌 Roadmap

### ✅ Coming Soon (ya online)
- Landing page con información del proyecto.  
- Páginas legales: Privacidad, Cookies, Términos.  
- Captación de mails con formulario de suscripción.  
- Enlace a redes sociales (Instagram).  

### 🚧 MVP (próxima entrega)
- Mapa interactivo con 2–3 misiones simples.  
- Pantalla de impacto con CTAs (donar / acciones).  
- Sección de transparencia con datos simulados.  
- Cápsulas culturales como contenido educativo.  

### 🔜 Post-MVP
- Internacionalización (i18n).  
- Optimización SEO / PWA.  
- Escalado técnico y nuevas misiones.  

---

## ⚖️ Marco ético y legal
- Principios de **transparencia, accesibilidad e inclusión**.  
- Cumplimiento de **RGPD / LOPDGDD / LSSI**.  
- Donaciones solo a entidades verificadas.  
- Políticas legales accesibles: Términos, Privacidad, Cookies.  
- Transparencia en créditos (atribución de recursos).  
- Sin *dark patterns*, sin explotación de datos.  

---

## 🗂️ Organización del repo
- `main` → rama de producción (deploy estable).  
- `dev` → rama de integración y pruebas.  
- `docs/` → documentación técnica y operativa (procesos, arquitectura, seguridad).  
- `web/` → aplicación Next.js (landing + futuras pantallas).  
- `public/` → assets estáticos (iconos, imágenes, JSONs públicos).  

---

## 🛠️ Stack técnico
- [Next.js 15](https://nextjs.org/) con App Router.  
- [TypeScript](https://www.typescriptlang.org/).  
- [TailwindCSS v4](https://tailwindcss.com/) con tokens en `globals.css`.  
- [next-themes](https://github.com/pacocoursey/next-themes) para soporte claro/oscuro.  
- [TypeDoc](https://typedoc.org/) para documentación automática de la API.  
- Despliegue en [Vercel](https://vercel.com/) con dominio gestionado en Cloudflare/Dinahosting.  

---

## 🤝 Contribución
- Trabajar siempre en ramas `feature/*`, `chore/*` o `fix/*`.  
- PRs hacia `dev` para revisión e integración.  
- `dev` se mergea a `main` tras validación y despliegue.  
- Más detalles en la carpeta [`/docs`](./docs).  

---

## 🧪 Testing y scripts
Comandos principales:
- `npm run dev` → iniciar en desarrollo.
- `npm run build` → build de producción.
- `npm run check` → lint + type-check + build.
- `npm run docs` → generar documentación de API en `/docs/api`.

---

## 📚 Documentación adicional
- [Arquitectura](./docs/architecture.md)
- [Procesos de desarrollo](./docs/process.md)
- [Seguridad](./docs/security.md)
- [Backlog](./docs/backlog.md)
- [ADRs](./docs/adr/README.md)

---

🌍 [linkaidly.org](https://linkaidly.org)  
📧 contact@linkaidly.org

---

## 📄 Licencia
Este proyecto no es de código abierto.  
Todos los derechos reservados © 2025 LinkAidly.  
Para cualquier uso o colaboración, contactar previamente a los administradores.