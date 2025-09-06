


# Runbook — Revisión periódica de seguridad

## 🎯 Objetivo
Realizar una revisión de seguridad programada en el proyecto **LinkAidly** para detectar riesgos, validar configuraciones y mantener cumplimiento normativo.

---

## 📅 Frecuencia
- **Mensual**: revisión rápida (logs, dependencias).
- **Trimestral**: revisión completa (cabeceras, allowlist, analítica).
- **Anual**: auditoría externa ligera recomendada.

---

## 🪜 Pasos

### 1. Dependencias
- [ ] Ejecutar `npm audit` en `/web`.
- [ ] Revisar PRs de `dependabot`.
- [ ] Eliminar librerías no usadas.

### 2. Configuración de seguridad en Vercel
- [ ] Validar HTTPS forzado.
- [ ] Revisar cabeceras en producción (CSP, HSTS, X-Frame-Options).
- [ ] Confirmar variables de entorno seguras y sin secretos expuestos.

### 3. DNS y Cloudflare
- [ ] Revisar configuración DNS.
- [ ] Validar certificados TLS activos.
- [ ] Revisar reglas de seguridad en Cloudflare (firewall, rate limiting).

### 4. Allowlist y enlaces externos
- [ ] Revisar `lib/allowlist.ts`.
- [ ] Añadir dominios nuevos solo si han sido verificados.
- [ ] Eliminar dominios obsoletos.

### 5. Analítica y privacidad
- [ ] Validar que Plausible sigue sin usar cookies ni fingerprinting.
- [ ] Confirmar cumplimiento RGPD/LOPDGDD en `docs/privacy.md`.

### 6. Logs y monitorización
- [ ] Revisar logs de errores en Vercel.
- [ ] Confirmar que no se almacenan datos sensibles.
- [ ] Verificar alertas básicas (si Plausible/Cloudflare detecta anomalías).

---

## ✅ Checklist global
- [ ] Dependencias revisadas.
- [ ] Vercel (HTTPS + cabeceras) revisado.
- [ ] Cloudflare (DNS + TLS + reglas) revisado.
- [ ] Allowlist actualizada.
- [ ] Privacidad confirmada.
- [ ] Logs y alertas revisados.
- [ ] Informe generado en `/docs/security-log.md`.

---

## 📚 Referencias
- [OWASP Top 10](https://owasp.org/www-project-top-ten/)
- [Next.js Security Docs](https://nextjs.org/docs/app/building-your-application/configuring/security)
- [Cloudflare Security](https://developers.cloudflare.com/fundamentals/security/)
- [Plausible Privacy](https://plausible.io/data-policy)