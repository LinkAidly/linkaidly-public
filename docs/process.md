# ⚙️ Process — LinkAidly

> **Objetivo:** Documentar *cómo trabajamos* para que el proyecto avance sin fricción, con calidad y con foco ético. Esta guía es corta, accionable y viva.

---

## 0️⃣ TL;DR del flujo diario

1. Crea una rama desde `dev`: `feat/...`, `fix/...`, `docs/...`, `chore/...`.
2. Haz commits pequeños con mensajes claros.
3. Abre Pull Request (PR) → destino `dev`. La CI debe pasar.
4. Revisa el checklist del PR y pide revisión (o autorrevisión si estás solo).
5. **Merge a `dev`** (squash/merge según lo acordado).
6. Cuando `dev` esté estable, **release a `main`** mediante rama `release/x.y.z`.
7. Vercel despliega automáticamente; verifica en `dev.linkaidly.org` (staging) y `linkaidly.org` (prod).
8. Documenta el cambio relevante en `/docs/CHANGELOG.md`.

---

## 🌿 Ramas y convención

- **`main`**: producción (Vercel → `linkaidly.org`).
- **`dev`**: integración y pruebas (Vercel → `dev.linkaidly.org`).
- Ramas de trabajo:  
  - `feat/<breve-descripcion>` — funcionalidad nueva  
  - `fix/<bug-o-incidencia>` — corrección  
  - `docs/<tema>` — documentación  
  - `chore/<tarea>` — mantenimiento y tooling  
  - `refactor/<pieza>` — cambios internos sin feature  
  - `hotfix/<critico>` — parche urgente en producción

**Regla:** nunca merges directos `dev → main` sin `release/*`.  
**Workflow recomendado:**

```txt
feat/* → PR a dev → merge
fix/*  → PR a dev → merge
release/x.y.z (desde dev) → PR a main → merge
hotfix/* (desde main) → PR a main → merge → back-merge a dev
```

---

## 📝 Commits y PRs

### Mensajes de commit (estilo simple)
```
feat(map): primer pin interactivo en Gaza
fix(ci): corrige caché de npm en workflow
docs(process): añade definición de hecho
```

### Reglas para PR
- Mantén el PR **pequeño y enfocado** (ideal < 300 líneas de diff neto).
- Debe compilar y pasar CI.
- Actualiza docs si el cambio afecta a usuarios, seguridad o procesos.

**Plantilla de PR:** se usa la del repo (`.github/pull_request_template.md`).

---

## ✅ Definición de Ready / Hecho

**Definition of Ready (DoR)**
- Hay issue o nota con **qué** y **por qué**.
- Aceptación clara (2–4 bullets).
- Impacto en seguridad/ética considerado (si aplica).

**Definition of Done (DoD)**
- Código compilando, sin *lint errors*.
- Tests relevantes pasan (cuando existan).
- Accesibilidad AA respetada en cambios UI visibles (contraste, foco, labels).
- **Docs** actualizadas (si procede).
- Previsualización de Vercel revisada y enlazada en el PR.

---

## 🏷️ Releases y versionado

- **Versionado Semántico**: `MAJOR.MINOR.PATCH`
  - `MAJOR`: cambios incompatibles
  - `MINOR`: funcionalidades nuevas compatibles
  - `PATCH`: hotfixes y arreglos pequeños
- Flujo:
  1. Crea `release/x.y.z` desde `dev`.
  2. Sube `CHANGELOG.md` con sección `x.y.z` (Added/Changed/Fixed).
  3. PR → `main`. Tras merge, crea **tag** `vX.Y.Z`.

> Nota: cuando haya *actions* para releases, se añadirá auto-tag.

---

## 🌐 Entornos

- **Local**: desarrollo en tu máquina.
- **Staging**: `dev.linkaidly.org` (Vercel apuntando a `dev`).
- **Prod**: `linkaidly.org` (Vercel apuntando a `main`).
- **Previews**: cada PR genera una URL temporal en Vercel.

---

## 🤖 CI y calidad

---

## 🧪 Testing

- **Framework**: se usa [Vitest](https://vitest.dev/) con [React Testing Library](https://testing-library.com/docs/react-testing-library/intro/) y `jest-dom`.
- **Ubicación de tests**:
  - Archivos unitarios: junto al archivo fuente como `*.test.ts` o `*.test.tsx`.
  - Alternativamente: en `/src/__tests__/` para pruebas de integración o ejemplos.
- **Ejecución**:
  - Local: `npm run test` (modo CI) o `npm run test:ui` (modo interactivo).
  - CI: se ejecutan automáticamente en cada PR a `dev` y en `main` vía workflow.
- **Convenciones**:
  - Usar `describe/test/expect` en lugar de `it`.
  - Preferir pruebas de comportamiento (qué ve el usuario) a pruebas de implementación.
  - Importar siempre `@testing-library/jest-dom` vía `vitest.setup.ts`.
- **Objetivo mínimo (MVP)**:
  - Cada componente UI crítico debe tener al menos un test de render básico.
  - Cada función en `/lib` debe tener al menos un test que valide input/output esperado.

- Workflows activos:
  - `ci.yml` — build, lint, test (si hay scripts).
  - `secret-scan.yml` — Gitleaks (evitar secretos).
  - `semgrep.yml` — reglas de seguridad/estilo en CI.
  - `branch-name.yml` — naming de ramas (`feat/`, `fix/`, etc.).

**Política de CI:**
- No se mergea si la CI falla.
- Falsos positivos: documenta el motivo en el PR y añade regla local si procede.

---

## 🔒 Seguridad y ética en el proceso

- **Revisión ética rápida** para nuevas cápsulas/contenidos:
  - Dignidad, no sensacionalismo, fuentes citadas.
  - Licencia válida registrada en `/docs/licenses.csv`.
- **Enlaces de donación/acción**: deben estar en **allowlist** y con `reviewed_at`/`expires_at`.
- **Secretos**: nunca en el repo. Usa `Vercel > Project > Settings > Environment Variables`.

---

## 💻 Estándares de código (extracto)

- **Next.js App Router** + TypeScript estricto.
- **Tailwind v4** con tokens en `globals.css`.
- Accesibilidad:
  - Controles focusables y *focus ring* visible.
  - Texto mínimo `16px`, contraste AA.
  - No transmitir significado solo por color.
- Componentes compartidos en `/web/src/components/`.
- Datos estáticos en `/web/public/data/*.json` (MVP).

---

## 🗂️ Gestión de issues y etiquetas

- **Tipos**: `bug`, `feature`, `docs`, `chore`, `refactor`, `ci`, `test`, `style`, `release`, `hotfix`.
- **Status**: `triage`, `in-progress`, `blocked`, `ready-for-review`, `done`.
- **Prioridad**: `p0`, `p1`, `p2`.

**Ciclo del issue:**
1. Crear con contexto y criterios de aceptación.
2. Asignar a una rama `feat/...` o `fix/...`.
3. PR enlazado (`Closes #ID`).
4. Cerrar al merge en `dev` o release.

---

## 📅 Cadencia y rituales (ligero)

- **Plan semanal (30 min)**: elige 2–3 objetivos realistas, no más.
- **Retro quincenal (15 min)**: qué funcionó, qué bloquearon, qué se cambia.
- **Revisión mensual (30–45 min)**: métricas clave (Plausible), riesgos, próximos milestones.

---

## 🚨 Incidentes y hotfix

- **Severidad**:  
  - `S1` caída / rotura pública  
  - `S2` bug significativo sin bypass  
  - `S3` menor / cosmético
- **Actuación**:
  - `S1/S2`: corta `hotfix/*` desde `main` → PR a `main` → deploy → *back-merge* a `dev`.
  - Comunica en `status` (si aplica) y añade post-mortem corto en `/docs/incidents/YYYY-MM-DD.md`.

---

## ✅ Plantillas y checklists

### Checklist PR (resumen)
- [ ] Compila y pasa CI
- [ ] Cambios accesibles (AA) si hay UI
- [ ] Sin secretos (`.env`, tokens)
- [ ] Previsualización revisada
- [ ] Docs/CHANGELOG si corresponde

### Checklist release
- [ ] Rama `release/x.y.z` creada desde `dev`
- [ ] `CHANGELOG.md` actualizado
- [ ] Verificado en `dev.linkaidly.org`
- [ ] Merge a `main` y tag `vX.Y.Z`
- [ ] Post en redes (si aplica)

---

## 👋 Onboarding exprés (para colaborar)

1. Clonar repo, instalar Node LTS con **nvm**.
2. `cd web && npm i && npm run dev`
3. Rama `feat/...` y abre PR a `dev`.
4. Leer `/docs/architecture.md` y esta guía.

---

## 🛠️ Mantenimiento de esta guía

- Se versiona junto al código.
- Cambios sustanciales → PR con etiqueta `docs`.
- Revisión mínima **mensual**.

---

**Última revisión:** <!-- actualizar fecha al editar --> 
- 23/08/2025

---

## 📚 Referencias externas
- [Conventional Commits](https://www.conventionalcommits.org/es/v1.0.0/)
- [SemVer](https://semver.org/lang/es/)
- [Keep a Changelog](https://keepachangelog.com/es-ES/1.0.0/)
- [Next.js Docs](https://nextjs.org/docs)
- [Vercel Docs](https://vercel.com/docs)
