


# ADR-0004: Analítica ética (Plausible)

- Fecha: 2025-09-07
- Estado: Aceptada

## Contexto
El proyecto necesita **medir interacciones básicas** (clics en donaciones, apertura de cápsulas, inicio de misiones) para evaluar el impacto y mejorar la experiencia.  
Requisitos:
- Respetar la privacidad de los usuarios (sin cookies, sin fingerprinting).
- Evitar el uso de Google Analytics u otras herramientas invasivas.
- Integración sencilla en Next.js.

Alternativas iniciales consideradas:
- Google Analytics → muy completo, pero invasivo y no alineado con principios éticos.
- Matomo → opción open source, pero requiere infraestructura propia.
- Fathom → buena opción, pero modelo de pago por suscripción.
- Plausible → ligero, sin cookies, ético, fácil integración.

## Decisión
Adoptar **Plausible Analytics** con integración ligera vía script en el layout y helpers tipados en `lib/analytics.ts`.

Eventos definidos inicialmente:
- `action_click` → clic en acción.
- `donation_open` → apertura de método de donación.
- `card_impression` → impresión de tarjeta.

## Consecuencias
**Positivas**
- Cumplimiento con GDPR/LOPDGDD (sin necesidad de banner de cookies).
- Métricas suficientes para el MVP.
- Sencilla integración en Next.js.
- Transparencia hacia los usuarios.

**Negativas**
- Métricas más limitadas que GA.
- Dependencia de servicio externo (aunque ético y europeo).

## Estado
Aceptada e implementada en el MVP.

## Referencias
- [Plausible Analytics](https://plausible.io/)
- Documento maestro del proyecto: *Proyecto LinkAidly V1.pdf*