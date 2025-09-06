# ✍️ Guía de estilo para documentación — LinkAidly

Esta guía define cómo escribir documentación en **LinkAidly** para mantener consistencia, claridad y profesionalidad.

---

## 📂 Estructura de documentos
- Cada documento debe comenzar con un **título claro** (`#`).
- Incluir una breve **descripción o propósito** en las primeras líneas.
- Dividir en secciones con encabezados (`##`, `###`).
- Usar listas numeradas o con guiones para mayor claridad.
- Finalizar con referencias si aplica.

---

## 🗣️ Tono y lenguaje
- Escribir en **español claro y directo**.
- Evitar jerga innecesaria; explicar acrónimos la primera vez que aparezcan.
- Mantener un tono **inclusivo y profesional**.
- Preferir frases activas: “El sistema valida…” en vez de “Es validado por el sistema…”.

---

## 🔗 Enlaces y referencias
- Usar enlaces relativos dentro del repo (`[ver ADR](adr/ADR-0001-frontend-framework.md)`).
- Para enlaces externos, incluir siempre el protocolo completo (`https://`).
- Referenciar la documentación de API autogenerada como:  
  “📚 Ver la [API del frontend](../web/docs/api/) para detalles técnicos.”

---

## 💻 Snippets y ejemplos
- Para comandos de terminal:
  ```bash
  npm run dev
  ```
- Para código TypeScript:
  ```ts
  export interface Mission {
    id: string;
    title: string;
  }
  ```
- Añadir ejemplos concretos siempre que faciliten la comprensión.

---

## 📝 Convenciones
- Formato de fechas: `YYYY-MM-DD`.
- Títulos de ADRs: `ADR-XXXX: <decisión>`.
- Changelog: seguir [Keep a Changelog](https://keepachangelog.com/es-ES/1.0.0/).
- Versionado: [SemVer](https://semver.org/lang/es/).

---

## 🧪 Estilo de tests
- **Ubicación**: los tests deben ir junto al archivo (`*.test.ts` o `*.test.tsx`) o en `/src/__tests__/` para integración.
- **Nomenclatura**: usar sufijo `.test.ts[x]` siempre en minúsculas.
- **Framework**: se utiliza Vitest con React Testing Library.
- **Sintaxis**:
  - Usar `describe`, `test` y `expect` (no `it`).
  - Preferir pruebas de comportamiento visibles para el usuario.
- **Matchers**: se extienden con `@testing-library/jest-dom`.
- **Buenas prácticas**:
  - Evitar snapshots extensos, preferir asserts específicos.
  - Nombrar los tests en español claro: `"muestra saludo"`, `"renderiza ActionCard con título"`.
  - Cada componente UI debe tener al menos un test de render básico.

---

## ✅ Checklist antes de commitear docs
1. ¿El documento tiene título y descripción inicial?
2. ¿La estructura es clara (secciones, listas)?
3. ¿El tono es claro, inclusivo y profesional?
4. ¿Los enlaces funcionan (relativos o externos)?
5. ¿Los ejemplos están formateados correctamente?
6. ¿Si aplica, se actualizó el índice en `docs/README.md` o `docs/adr/README.md`?

---

Gracias por mantener la documentación clara y consistente 🌿