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
- Los ADRs (registros de decisiones técnicas) se mantienen en el repositorio privado de LinkAidly.
- La API técnica se documenta en repositorios internos, no en este repositorio público.

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

## ✅ Checklist antes de commitear docs
1. ¿El documento tiene título y descripción inicial?
2. ¿La estructura es clara (secciones, listas)?
3. ¿El tono es claro, inclusivo y profesional?
4. ¿Los enlaces funcionan (relativos o externos)?
5. ¿Los ejemplos están formateados correctamente?
6. ¿Si aplica, se actualizó el índice en docs/README.md?

---

Gracias por mantener la documentación clara y consistente 🌿