
# 🔒 Seguridad en LinkAidly (versión pública)

**Fecha:** 2025-09-06  
**Ámbito:** medidas básicas de seguridad aplicadas en la plataforma LinkAidly.  
Este documento resume cómo protegemos la plataforma y los datos de quienes la usan, en un lenguaje claro y accesible.

---

## 1) Principios generales
- **Privacidad por diseño:** recogemos solo los datos estrictamente necesarios.  
- **Transparencia:** explicamos de forma abierta qué datos tratamos y con qué fin (ver `docs/privacy.md`).  
- **Cumplimiento legal:** seguimos el RGPD y la normativa española de protección de datos.  

---

## 2) Medidas técnicas básicas
- Toda la web funciona bajo **HTTPS** (cifrado seguro).  
- El dominio usa **Cloudflare** como capa de seguridad adicional (protección frente a ataques).  
- Se aplican cabeceras de seguridad (CSP, X-Frame-Options, etc.) para reducir riesgos comunes.  
- No se exponen claves ni tokens sensibles en el navegador.  

---

## 3) Protección de formularios y correos
- Los formularios (ej. suscripción por correo) se validan para evitar spam.  
- Cualquier comunicación incluye siempre opción de baja sencilla.  

---

## 4) Analítica ética
- Usamos **Plausible Analytics**, que no requiere cookies ni identifica personas.  
- Solo medimos visitas de forma agregada para mejorar la plataforma.  

---

## 5) Roadmap de seguridad
- ✅ HTTPS activo desde el primer día.  
- ✅ Auditorías internas y escaneos para detectar secretos en el código.  
- 🔜 Revisión externa independiente de la seguridad.  
- 🔜 Monitoreo de errores y accesos en producción.  

---

## 6) Canales de reporte
Si detectas un problema de seguridad en LinkAidly, por favor repórtalo de forma responsable:  
- **Contacto:** `contact@linkaidly.org`  
---

👉 Estas medidas son proporcionales a un proyecto en fase inicial (MVP) y se reforzarán conforme la plataforma crezca.
