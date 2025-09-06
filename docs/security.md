

# 🔒 Seguridad y Cumplimiento Técnico

Este documento recoge las medidas mínimas y progresivas de seguridad para LinkAidly, tanto en el plano técnico como en el de cumplimiento normativo.

---

## 1. 📜 Principios generales
- **Privacidad por diseño y por defecto**: solo se recogen los datos imprescindibles.
- **Transparencia**: los usuarios deben saber qué datos se usan y con qué fin.
- **Cumplimiento normativo**: RGPD, LOPDGDD y LSSI como referencias principales.

---

## 2. 💻 Seguridad en el desarrollo
- Uso de **repositorio privado** en fases iniciales.
- **Ramas protegidas** y revisión mínima de PRs antes de merge.
- **Secret scanning** (Gitleaks) y análisis estático (Semgrep) en cada push.
- Variables sensibles gestionadas con **.env** (excluidas del repo).

---

## 3. 🏗️ Seguridad en la infraestructura
- Hosting en **Vercel** con HTTPS obligatorio (Let’s Encrypt).
- **Cloudflare** como proxy y capa adicional de seguridad (WAF, DDoS).
- HSTS activado una vez validado el despliegue estable.
- DNS protegidos con registros mínimos (A, AAAA, CNAME).

---

## 4. 🌐 Seguridad en la aplicación
- Uso de **Next.js** con middlewares para cabeceras CSP, X-Frame-Options, X-Content-Type-Options.
- Formularios conectados con servicios de terceros (ej. Formspree) con validación anti-spam.
- Tokens y claves externas nunca expuestas en el cliente.
- Pruebas de accesibilidad que garanticen foco visible y navegación con teclado.

---

## 5. ⚖️ Cumplimiento y datos personales
- Email de contacto → gestionado bajo el dominio oficial.
- Listas de correo → deben incluir opción de baja clara (unsubscribe).
- Cookies → solo las estrictamente necesarias (analítica opcional y ética con Plausible).
- Registro y tratamiento de datos documentado en `docs/privacy.md`.

---

## 6. 🛣️ Roadmap de seguridad
- [x] HTTPS activo desde el primer despliegue.
- [x] Secret scanning y Semgrep en GitHub.
- [x] HSTS forzado en producción.
- [ ] Revisiones de código externas (auditoría ligera).
- [ ] Monitoreo de logs de errores y accesos.

---
## 📚 Referencias externas
- [OWASP Top 10](https://owasp.org/www-project-top-ten/)
- [RGPD — Reglamento General de Protección de Datos](https://gdpr-info.eu/)
- [LOPDGDD — Agencia Española de Protección de Datos](https://www.aepd.es/)
- [Next.js Security Docs](https://nextjs.org/docs/app/building-your-application/configuring/security)
- [Cloudflare Security](https://developers.cloudflare.com/fundamentals/security/)
