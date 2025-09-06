

# ADR-0007: Licencia (Propietaria — Todos los derechos reservados)

- Fecha: 2025-09-07
- Estado: Aceptada

## Contexto
Al definir la estrategia legal del proyecto, se evaluó la opción de licencias de código abierto (MIT, GPL, Apache) frente a mantener el proyecto bajo un modelo cerrado.

El objetivo principal es **proteger la propiedad intelectual de LinkAidly** y evitar que terceros puedan reutilizar, copiar o comercializar el código sin autorización.

## Decisión
Adoptar una **licencia propietaria** de “Todos los derechos reservados”.

- Se crea un archivo `LICENSE` en la raíz con texto restrictivo.
- Se actualiza `web/package.json` a `"license": "Proprietary"`.
- Se reemplaza el badge de MIT en `README.md` por **All Rights Reserved**.
- Se deja claro que cualquier uso requiere autorización explícita.

## Consecuencias

**Positivas**
- Protección legal fuerte de la propiedad intelectual.
- Se minimiza riesgo de copia o uso indebido del código.
- Coherencia en toda la documentación y metadatos del repo.

**Negativas**
- Menor facilidad para atraer colaboradores externos.
- Incompatibilidad con ecosistemas open source que exigen licencias libres.
- Cualquier colaboración debe gestionarse con acuerdos privados.

## Estado
Aceptada y aplicada desde septiembre de 2025.

## Referencias
- [All Rights Reserved vs. Open Source](https://choosealicense.com/no-permission/)
- Documento maestro del proyecto: *Proyecto LinkAidly V1.pdf*
- `LICENSE` en la raíz del repo