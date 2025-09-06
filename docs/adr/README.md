

# ADR — Arquitectural Decision Records

Este directorio contiene las decisiones arquitectónicas tomadas en el proyecto **LinkAidly**.  
Cada ADR documenta una decisión clave, su contexto, alternativas consideradas y el resultado final.

## Índice de ADRs

- [ADR-0001: Frontend framework (Next.js + App Router)](ADR-0001-frontend-framework.md)
- [ADR-0002: Styling (Tailwind + tokens)](ADR-0002-styling.md)
- [ADR-0003: Documentación API (TypeDoc + TSDoc)](ADR-0003-docs-api.md)
- [ADR-0004: Analítica ética (Plausible)](ADR-0004-analytics.md)
- [ADR-0005: Allowlist de dominios externos](ADR-0005-allowlist.md)
- [ADR-0006: Seguridad mínima (baseline)](ADR-0006-security-baseline.md)
- [ADR-0007: Licencia (Propietaria — Todos los derechos reservados)](ADR-0007-license.md)

## Convenciones

- **Formato**: plantilla simplificada basada en [MADR](https://adr.github.io/madr/).
- **Estado**: `Proposed | Accepted | Superseded | Deprecated`.
- **Ubicación**: cada ADR se guarda en este directorio (`/docs/adr`).
- **Numeración**: incremental con prefijo `ADR-XXXX`.

## Guía rápida para añadir un ADR

1. Copiar la plantilla `adr-template.md`.
2. Completar:
   - Título de la decisión.
   - Contexto y problema.
   - Alternativas consideradas.
   - Decisión tomada.
   - Consecuencias.
3. Hacer commit con mensaje:
   ```
   docs(adr): añadir ADR-00X sobre <tema>
   ```