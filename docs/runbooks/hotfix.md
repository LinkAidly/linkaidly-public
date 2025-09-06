


# Runbook: Hotfix en producción

## 🎯 Objetivo
Resolver un incidente **crítico en producción** de forma segura y rápida, minimizando el impacto en usuarias/os y garantizando trazabilidad.

---

## 🧭 Criterios para abrir un hotfix
- Caída total o parcial del sitio.
- Error crítico que impide una acción principal (donar, ver misiones, etc.).
- Vulnerabilidad de seguridad explotable.
- Reversión urgente de una funcionalidad.

Si la incidencia no es crítica, seguir el flujo normal (`feature/*` → PR a `dev`).

---

## 🪜 Pasos

### 1) Preparación
1. Crear issue `HOTFIX: <resumen>` y etiquetar `hotfix` + severidad.
2. Crear rama desde `main`:
   ```bash
   git checkout main && git pull --rebase
   git checkout -b hotfix/<descripcion-corta>
   ```

### 2) Implementación
1. Reproducir el problema y escribir una prueba mínima (si es posible).
2. Aplicar el fix (cambios mínimos, sin refactors).
3. Validar localmente:
   ```bash
   npm ci
   npm run lint && npm run build
   npm run docs
   ```

### 3) PR directo a `main`
1. Abrir PR `hotfix/<descripcion>` → `main` (no a `dev`).
2. Solicitar revisión rápida.
3. Asegurar CI en verde (build, lint, docs).

### 4) Deploy a producción
1. Al hacer merge en `main`, Vercel despliega automáticamente.
2. Verificar en Vercel que el deploy está **Ready**.
3. **Smoke test** en `https://linkaidly.org`.

### 5) Back‑merge a `dev`
Para no perder el fix en la rama de trabajo:
```bash
# Opción A: merge
git checkout dev && git pull --rebase
git merge --no-ff hotfix/<descripcion-corta>

# Opción B: cherry-pick del commit del hotfix
# git log para obtener el SHA
git cherry-pick <sha_del_hotfix>
```
Empujar `dev` y abrir PRs pendientes que se basen en `dev`.

### 6) Cierre
1. Cerrar issue `HOTFIX` con referencia al PR y despliegue.
2. Actualizar `docs/CHANGELOG.md` (sección `Fixed`).
3. Crear tag si procede:
   ```bash
   git checkout main && git pull --rebase
   git tag vX.Y.Z -m "hotfix: <descripcion>"
   git push origin vX.Y.Z
   ```

---

## 🔁 Rollback rápido
Si el fix empeora la situación:
1. En Vercel → *Deployments*, **Promote** el despliegue anterior a producción.
2. Reabrir el issue y documentar el rollback.
3. Preparar nuevo hotfix con la causa corregida.

---

## 🧯 Troubleshooting
- **Build falla en CI** → Revisa dependencias, tipos TS y warnings de TypeDoc.
- **Error persiste en prod** → Verificar caché del navegador/edge, revisar logs.
- **Regresión en otra parte** → Minimiza el fix, añade test de humo.
- **Problema de DNS/SSL** → Verificar configuración en Cloudflare/Vercel.

---

## ✅ Checklist
- [ ] Issue `HOTFIX` creado y etiquetado.
- [ ] Rama `hotfix/*` creada desde `main`.
- [ ] Lint + build + docs OK.
- [ ] PR a `main` revisado y con CI verde.
- [ ] Deploy en Vercel **Ready** y smoke tests OK.
- [ ] Back‑merge a `dev` hecho (merge o cherry‑pick).
- [ ] CHANGELOG actualizado y tag opcional creado.

---

## 📚 Referencias
- [Vercel — Deployments](https://vercel.com/docs/deployments)
- [Git — Cherry-pick](https://git-scm.com/docs/git-cherry-pick)
- [Keep a Changelog](https://keepachangelog.com/es-ES/1.0.0/)