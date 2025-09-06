


# Runbook: Alta de nuevo dominio o subdominio

## 🎯 Objetivo
Dar de alta un dominio o subdominio en **LinkAidly** asegurando que queda correctamente configurado en Dinahosting, Cloudflare y Vercel.

## 🪜 Pasos

1. **Registrar dominio o subdominio**
   - Entra en [Dinahosting](https://dinahosting.com/).
   - Añade el dominio o subdominio al panel de gestión.

2. **Configurar DNS en Cloudflare**
   - Accede al [panel de Cloudflare](https://dash.cloudflare.com/).
   - Añade los registros necesarios:
     - `A` o `CNAME` apuntando a Vercel.
     - `TXT` de verificación si lo solicita Vercel.
   - Habilitar HTTPS automático.

3. **Asignar dominio en Vercel**
   - Entra en el proyecto **LinkAidly** en [Vercel](https://vercel.com/).
   - Añadir el dominio o subdominio en *Settings > Domains*.
   - Verificar que el estado aparezca como `Valid Configuration`.

4. **Verificar resolución**
   - Abrir el dominio en el navegador.
   - Comprobar certificados SSL activos.
   - Revisar que la web despliegue correctamente.

## ✅ Checklist
- [ ] Dominio registrado en Dinahosting.
- [ ] DNS configurado en Cloudflare.
- [ ] Dominio asignado en Vercel.
- [ ] HTTPS activo y certificado válido.
- [ ] Acceso confirmado en navegador.

## 📚 Referencias
- [Dinahosting](https://dinahosting.com/)
- [Cloudflare Docs](https://developers.cloudflare.com/)
- [Vercel Docs](https://vercel.com/docs/concepts/projects/domains)