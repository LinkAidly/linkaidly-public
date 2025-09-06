

# ADR-0002: Styling (Tailwind + tokens)

- Fecha: 2025-09-07
- Estado: Aceptada

## Contexto
El proyecto requería un sistema de **estilos consistente, escalable y fácil de mantener**.  
Criterios buscados:
- Rapidez en prototipado inicial.
- Tokens reutilizables (colores, tipografía).
- Compatibilidad con dark/light mode.
- Evitar CSS-in-JS complejo para este MVP.

Alternativas iniciales consideradas:
- CSS Modules → simples, pero poca escalabilidad en un proyecto grande.
- Styled Components / Emotion → potentes, pero sobrecarga en runtime y complejidad añadida.
- Vanilla Extract → muy tipado, pero curva de aprendizaje alta y comunidad más pequeña.
- TailwindCSS → sistema utilitario maduro, flexible, con soporte para tokens.

## Decisión
Adoptar **TailwindCSS v4** como motor de estilos, con tokens definidos en `globals.css`.  
Tokens iniciales:
- Colores base: `olive`, `arena`.
- Tipografía: `Montserrat`.
- Espaciados y radios consistentes.

## Consecuencias
**Positivas**
- Desarrollo rápido con clases utilitarias.
- Tokens centralizados en `globals.css` permiten mantener consistencia.
- Fácil soporte para dark/light mode.
- Gran comunidad y documentación.

**Negativas**
- Verbosidad en las clases de los componentes.
- Posible sobrecarga visual en el código JSX.
- Dependencia de Tailwind para mantener consistencia.

## Estado
Aceptada y aplicada en todas las páginas y componentes.

## Referencias
- [TailwindCSS v4](https://tailwindcss.com/)
- Documento maestro del proyecto: *Proyecto LinkAidly V1.pdf*