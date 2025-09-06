# 🏗️ Infraestructura del proyecto LinkAidly

## 🌐 Visión general
La infraestructura de LinkAidly está diseñada para ofrecer un despliegue ágil y seguro, facilitando la escalabilidad futura y la integración con servicios externos. Actualmente, se basa en tecnologías modernas de hosting y gestión de dominios, con una arquitectura sencilla que permite una rápida iteración y desarrollo.

## 🚀 Hosting y despliegue
El proyecto se aloja en Vercel, aprovechando su integración nativa con GitHub:
- Rama `main` → producción.
- Rama `dev` → desarrollo/staging.
- Cada push a estas ramas genera despliegues automáticos.
- Las ramas `feature/*` generan *previews* para pruebas antes de integrar.

## 🌍 Dominio y DNS
- Dominio principal gestionado en Dinahosting.
- Configuración adicional en Cloudflare (rendimiento + seguridad).
- Subdominios:
  - `dev.` → entorno de desarrollo.
  - `beta.` → preproducción.
- HTTPS automático y políticas HSTS activadas.

## 💾 Almacenamiento de datos
Actualmente, LinkAidly no utiliza una base de datos tradicional; la información se almacena en archivos JSON estáticos dentro del repositorio. En el futuro, se prevé la integración de servicios como Supabase para gestionar datos de forma dinámica y escalable, facilitando funcionalidades más avanzadas y personalizadas.

## 📧 Correo electrónico
- Cuenta principal: `contact@linkaidly.org` (Dinahosting).
- Aliases temporales mediante iCloud para comunicaciones específicas.
- Posible creación de cuentas adicionales según el crecimiento.

## 📊 Analítica y monitorización
Para el seguimiento del rendimiento y uso, se planea implementar Plausible como herramienta de analítica web, complementada con los logs proporcionados por Vercel. Esto permitirá obtener métricas claras y respetuosas con la privacidad sobre la interacción de los usuarios con la plataforma.

## 📈 Escalabilidad futura
La arquitectura está pensada para ser modular, facilitando la integración de APIs externas y servicios adicionales. Se aprovechará la CDN de Cloudflare para optimizar la distribución de contenido y mejorar la experiencia del usuario a nivel global, asegurando que la plataforma pueda crecer sin comprometer la calidad del servicio.

---
## 📚 Referencias externas
- [Vercel Docs](https://vercel.com/docs)
- [Cloudflare Docs](https://developers.cloudflare.com/)
- [Dinahosting](https://dinahosting.com/)
- [Supabase Docs](https://supabase.com/docs)
- [Plausible Analytics](https://plausible.io/docs)
