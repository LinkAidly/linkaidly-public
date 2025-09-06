


# ADR-0001: Frontend framework (Next.js + App Router)

- Fecha: 2025-09-07
- Estado: Aceptada

## Contexto
El proyecto necesitaba un **framework moderno de frontend** que permitiera:
- Renderizado híbrido (SSR + SSG).
- Integración directa con Vercel.
- Escalabilidad a medio plazo (misiones, cápsulas, donaciones).
- Comunidad activa y soporte continuado.

Alternativas iniciales consideradas:
- Create React App (obsoleto y sin mantenimiento).
- Astro (excelente para contenido estático, pero menos adecuado para app interactiva).
- Remix (interesante, pero no tan integrado con Vercel).
- Vue/Nuxt (opción válida, pero el equipo está alineado con React).

## Decisión
Adoptar **Next.js 15 con App Router** como framework base del frontend.

## Consecuencias
**Positivas**
- Integración nativa con Vercel.
- Soporte de React Server Components.
- Documentación abundante y ecosistema maduro.
- Facilita patrones escalables (layouts, server actions, metadata).

**Negativas**
- Curva de aprendizaje del App Router.
- Dependencia fuerte del ecosistema Vercel/React.
- Posibles breaking changes en futuras versiones.

## Estado
Aceptada y en uso desde la fase *Coming Soon*.

## Referencias
- [Next.js documentation](https://nextjs.org/docs)
- [App Router introduction](https://nextjs.org/docs/app)
- Documento maestro del proyecto: *Proyecto LinkAidly V1.pdf*