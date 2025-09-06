# Git – Cheat Sheet (LinkAidly)

> ℹ️ Nota: Todos los comandos se ejecutan desde la **raíz del repo** salvo que se indique explícitamente (ej. `/web`).

---

## Ver / inspeccionar
```bash
# Ramas locales
git branch 

# Ramas locales y remotas
git branch -a

# Estado de seguimiento (muestra ahead/behind)
git branch -vv

# Últimos commits con grafo
git log --oneline --decorate --graph --all -n 5

# Diferencias entre tu copia local y el remoto (sin salida = sincronizado)
git diff origin/main..main
git diff origin/dev..dev
```

---

## Cambiar de rama y actualizar
```bash
git checkout main && git pull
git checkout dev  && git pull
# (Alternativa moderna)
git switch main && git pull
git switch dev  && git pull
```
---

## Sincronizar todo (traer y limpiar referencias remotas antiguas)
```bash
git fetch --all --prune
```
---

## Alinear `dev` con `main` (cuando quieres que queden idénticas)
> ⚠️ Úsalo solo si **no** tienes trabajo sin subir en `dev`.

```bash
git checkout dev
git fetch origin
git reset --hard origin/main
git push --force-with-lease
```
---

## Comparar ramas entre sí (qué tiene una que no tenga la otra)
```bash
# Commits que están en dev pero no en main
git log main..dev --oneline

# Commits que están en main pero no en dev
git log dev..main --oneline
```
---

## Crear y publicar una rama nueva
```bash
# Crea desde la rama actual
git checkout -b 'nuevo-nombre-rama'
# (o) git switch -c new/branch-naming

# Añadir cambios y commit
git add .github/ruta/archivo
git commit -m "new: comment"

# Publicar la rama en remoto y setear tracking
git push -u origin 'nombre-rama'
```
---

## Renombrar una rama que no cumple la convención
```bash
# estando en la rama actual (git branch -a)
# Renombrar local
git branch -m 'nuevo-nombre-rama'

# borrar la rama antigua en remoto
git push origin --delete 'my-old-branch'

# subir la nueva rama al remoto
git push -u origin 'nuevo-nombre-rama'
```
---

## Borrar ramas (limpieza)
```bash
# Borrar rama local ya mergeada
git branch -d 'nombre-rama'

# Borrar rama remota
git push origin --delete 'nombre-rama'

# Limpiar referencias remotas obsoletas
git fetch --all --prune
```
---

## Comprobar web antes de pushear (Opcional local) 
```bash
# Desde /web
cd web
npm run lint
npm run build
```

## Pasar de una rama a dev
```bash
git checkout dev
git pull origin dev   # asegúrate de traer la última
git merge 'nombre-rama'
git push origin dev
```

## Pasar de la rama dev a main
```bash
git checkout main
git pull origin main
git merge dev
git push origin main
```
---

## Notas rápidas (para evitar líos)

### 📌 Flujo de ramas
```
feature/*  →  dev  →  main
```

- **Flujo acordado:**  
  - PRs hacia `dev` → *Squash and merge*.  
  - Para publicar: PR `dev → main` → *Merge commit* (así el grafo “se cierra” solo).

- **Si usas Squash también en `dev → main`:**  
  luego resetea `dev` a `main` (comando arriba) para dejar la historia limpia.

- **Cuando compares:**  
  confía en *Files changed* (o `git diff`) más que en “X commits ahead/behind”;  
  ese contador refleja SHAs, no necesariamente contenido distinto.

- **Si un comando te falla con “ambiguous argument…”**:  
  revisa que no haya un **typo** en el nombre de la rama (p. ej., `devgit`)  
  o usa `--` para separar rutas de revisiones.


---
## 🔧 Aliases útiles (opcional)

```bash
# Alias para status
git config --global alias.st status

# Alias para log en grafo
git config --global alias.lg "log --oneline --decorate --graph --all"
```

---
## 🛠️ Troubleshooting rápido

- **Conflictos de merge**  
  ```bash
  git merge --abort
  ```
- **Deshacer último commit (sin perder cambios)**  
  ```bash
  git reset --soft HEAD~1
  ```
- **Guardar cambios temporales y recuperarlos**  
  ```bash
  git stash
  git stash pop
  ```
