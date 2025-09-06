


# Runbook — Rotación de Credenciales

Este runbook define el proceso estándar para rotar **credenciales y secretos** en el proyecto LinkAidly. La rotación periódica garantiza que claves comprometidas no se mantengan activas y reduce el riesgo de accesos no autorizados.

---

## Alcance
- Variables de entorno en **Vercel** (producción, preview, desarrollo).
- Claves de **Cloudflare** (API tokens).
- Accesos a **Dinahosting** (dominio y correo).
- Tokens de **GitHub** (actions, dependabot).
- Cuentas externas asociadas (ej. Plausible, Zoho Mail).

---

## Frecuencia
- **Trimestral**: Vercel, Cloudflare y GitHub.
- **Semestral**: Dinahosting, correos.
- **Inmediata**: si hay indicio de compromiso.

---

## Procedimiento

### 1. Preparación
- Avisar al equipo (Slack/Telegram interno).
- Abrir issue en GitHub con etiqueta `security` → título: "Rotación de credenciales Q[trimestre]-[año]".
- Confirmar lista de credenciales a rotar (checklist).

### 2. Rotación en Vercel
1. Entrar en **Vercel Dashboard** → Project Settings → Environment Variables.
2. Regenerar claves necesarias (ej. `NEXT_PUBLIC_API_KEY` si aplica).
3. Actualizar secretos y guardar.
4. Desplegar nuevo build para validar.

### 3. Rotación en Cloudflare
1. Acceder a **Cloudflare Dashboard** → My Profile → API Tokens.
2. Revocar token antiguo → crear uno nuevo con permisos mínimos necesarios.
3. Sustituir en Vercel/GitHub si se usa en pipelines.
4. Probar acceso a DNS y WAF.

### 4. Rotación en Dinahosting
1. Cambiar contraseña de la cuenta principal.
2. Revisar accesos a correos (SPF, DKIM, DMARC siguen intactos).
3. Documentar nueva clave en gestor seguro (Bitwarden recomendado).

### 5. Rotación en GitHub
1. Revisar sección **Settings → Developer settings → Tokens**.
2. Revocar tokens antiguos y crear nuevos con permisos mínimos.
3. Si aplica a **GitHub Actions**, actualizar `secrets` en repositorio.
4. Validar workflows tras commit de prueba.

### 6. Cuentas externas
- **Plausible**: regenerar clave de API si aplica.
- **Zoho Mail**: cambiar contraseña de administrador si está en uso.
- Otras plataformas: seguir política equivalente.

---

## 7. Validación
- Confirmar que builds en `main` y `dev` funcionan.
- Revisar que no hay errores en logs de Vercel ni bloqueos en Cloudflare.
- Probar envío/recepción de correos oficiales.

---

## 8. Documentación
- Actualizar issue con lista de credenciales rotadas y fecha.
- Cerrar issue con comentario: "Rotación completada — [fecha]".
- Registrar rotación en `/docs/security-log.md`.

---

## Checklist
- [ ] Vercel — variables rotadas y probadas.
- [ ] Cloudflare — token API actualizado.
- [ ] Dinahosting — contraseña cambiada.
- [ ] GitHub — tokens/secrets regenerados.
- [ ] Cuentas externas revisadas.
- [ ] Issue en GitHub cerrado.
- [ ] Log actualizado en `/docs/security-log.md`.

---

## Notas
- Nunca guardar credenciales en texto plano o commits.
- Usar **gestor de contraseñas** (Bitwarden recomendado).
- En caso de emergencia (compromiso activo), **rotar inmediatamente todas las credenciales** y comunicar públicamente si procede.