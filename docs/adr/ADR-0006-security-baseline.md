

# ADR-0006: Security baseline

- Fecha: 2025-09-07
- Estado: Aceptada

## Contexto
El proyecto debe cumplir un **mínimo de seguridad técnica y operativa** desde el MVP.  
Se identificaron riesgos clave:
- Exposición a XSS / inyecciones.
- Enlaces externos maliciosos.
- Tráfico sin HTTPS.
- Validación insuficiente de datos.

Normas de referencia: OWASP Top 10, RGPD/LOPDGDD, buenas prácticas de Next.js.

## Decisión
Adoptar una **línea base de seguridad** con medidas mínimas:

- **Validación estricta**:  
  - Uso de Zod en `lib/*` para validar datos de JSONs y props.  
  - Tipos en `src/types/*` como contratos.  

- **Enlaces externos seguros**:  
  - Allowlist de dominios en `lib/allowlist.ts`.  
  - `rel="noopener noreferrer"` en enlaces externos.  

- **Cabeceras y HTTPS**:  
  - Forzar HTTPS (Cloudflare + Vercel).  
  - Configurar CSP, HSTS, X-Frame-Options, etc.  

- **Gestión de secretos**:  
  - Variables de entorno solo en Vercel / `.env.local`.  
  - No exponer claves en el repo.  

- **Analítica ética**:  
  - Plausible (sin cookies, sin fingerprinting).  

## Consecuencias
**Positivas**
- Reducción de riesgo de XSS y fugas de datos.  
- Confianza del usuario en la plataforma.  
- Cumplimiento con normativa básica (RGPD, LOPDGDD).  

**Negativas**
- Requiere mantenimiento constante (listas, cabeceras).  
- Complejidad añadida en despliegue (configuración Cloudflare + Vercel).  

## Estado
Aceptada y aplicada en el MVP.

## Referencias
- [OWASP Top 10](https://owasp.org/www-project-top-ten/)  
- Documento maestro del proyecto: *Proyecto LinkAidly V1.pdf*