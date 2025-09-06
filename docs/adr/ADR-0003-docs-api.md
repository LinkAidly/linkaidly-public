


# ADR-0003: Documentación API (TypeDoc + TSDoc)

- Fecha: 2025-09-07
- Estado: Aceptada

## Contexto
El proyecto necesita **documentación clara y consistente de la API interna (tipos, funciones, contenedores, componentes)**.  
Requisitos:
- Que se genere automáticamente desde el código para evitar desincronización.
- Compatible con TypeScript y tipados fuertes.
- Exportable en formato Markdown para integrarse con el repositorio.

Alternativas iniciales consideradas:
- JSDoc → estándar clásico, pero menos integrado con TS moderno.
- Docusaurus Docs → buena UI, pero duplicaría la escritura (no extrae de TS).
- Typedoc → extrae directamente de TS y soporta plugins de salida en Markdown.
- TSDoc → convención estandarizada compatible con Typedoc.

## Decisión
Adoptar **Typedoc** con el plugin de salida en **Markdown**, y escribir la documentación en formato **TSDoc** dentro del código.  
Resultado:
- Documentación autogenerada en `/web/docs/api/`.
- Comentarios TSDoc en todos los archivos de `/src`.

## Consecuencias
**Positivas**
- Fuente única de verdad: el código mismo.
- Formato Markdown simple, versionado en el repo.
- Cohesión entre tipos, funciones y contenedores.
- Fácil de integrar en GitHub Pages o similares si se desea.

**Negativas**
- Disciplina: requiere mantener los comentarios TSDoc actualizados.
- Limitación visual: la salida Markdown es sobria (no un site bonito como Docusaurus).

## Estado
Aceptada y en uso desde la fase de documentación inicial.

## Referencias
- [TypeDoc](https://typedoc.org/)
- [TSDoc](https://tsdoc.org/)
- Documento maestro del proyecto: *Proyecto LinkAidly V1.pdf*