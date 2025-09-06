


# 🤝 Guía de contribución — LinkAidly

¡Gracias por tu interés en contribuir a **LinkAidly**!  
Este documento explica cómo colaborar de forma ordenada y consistente.

---

## 🚀 Flujo de trabajo con ramas
- **main** → rama de producción (deploy estable en [linkaidly.org](https://linkaidly.org)).
- **dev** → rama de integración y staging (deploy en [dev.linkaidly.org](https://dev.linkaidly.org)).
- **feature/*** → nuevas funcionalidades.
- **fix/*** → correcciones de bugs.
- **chore/*** → tareas de mantenimiento o mejoras internas.
- **docs/*** → cambios en documentación.

---

## ✅ Checklist para PRs
Antes de abrir un Pull Request hacia `dev`:
1. El código compila (`npm run build`) y pasa linting (`npm run lint`).
2. Los comentarios TSDoc están actualizados (para TypeDoc).
3. Se ha actualizado documentación en `/docs` si corresponde.
4. Se añaden tests o casos de prueba manuales si aplica.
5. El título y la descripción del PR son claros y explicativos.

---

## 📝 Convención de commits
Se recomienda usar [Conventional Commits](https://www.conventionalcommits.org/es/v1.0.0/):

- `feat:` → nueva funcionalidad.
- `fix:` → corrección de bug.
- `docs:` → cambios en documentación.
- `chore:` → tareas varias, mantenimiento.
- `refactor:` → refactor de código sin cambio funcional.
- `test:` → añadir o modificar tests.

Ejemplo:
```
feat(actions): añadir validación con allowlist en ActionCardContainer
```

---

## 📚 Documentación
- **API interna** → autogenerada con TypeDoc en `/web/docs/api/`.
- **Procesos y arquitectura** → en `/docs/` (incluye ADRs y notas técnicas).
- **Estilo de docs** → ver [`docs/styleguide.md`](docs/styleguide.md).

---

## 🔒 Seguridad
- No incluir secretos ni claves en el repo.
- Usar `.env.local` para credenciales en desarrollo.
- Reportar vulnerabilidades de forma privada (ver [`SECURITY.md`](SECURITY.md)).

---

Gracias por ayudar a que LinkAidly crezca 🌱