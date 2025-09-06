


# ADR-0005: Allowlist de dominios externos

- Fecha: 2025-09-07
- Estado: Aceptada

## Contexto
El proyecto incluye enlaces a recursos externos (donaciones, acciones, campañas).  
Riesgos detectados:
- Posible redirección a dominios maliciosos.
- Pérdida de confianza si se muestran enlaces inseguros.
- Requisitos de seguridad del Nivel 11 (CSP, validación estricta).

Alternativas iniciales consideradas:
- Lista abierta sin validación → insegura.
- Validación manual caso por caso → lenta y propensa a errores.
- Allowlist centralizada → más segura y fácil de mantener.

## Decisión
Implementar una **allowlist de dominios** centralizada en `lib/allowlist.ts`.  
- Cada enlace externo debe validarse con `isAllowedURL`.
- Dominios no listados → bloqueados por defecto.
- El contenedor decide si mostrar el link como clicable o no.

## Consecuencias
**Positivas**
- Prevención de enlaces a sitios no verificados.
- Cumplimiento de estándares de seguridad.
- Mantenimiento sencillo: basta actualizar la lista en un solo archivo.

**Negativas**
- Requiere revisar periódicamente la lista de dominios.
- Dependencia en un archivo único (riesgo de error humano si no se valida correctamente).

## Estado
Aceptada e implementada en MVP.

## Referencias
- `lib/allowlist.ts`
- Documento maestro del proyecto: *Proyecto LinkAidly V1.pdf*