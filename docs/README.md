# Índice de la documentación de LinkAidly

Este directorio reúne la **documentación global del proyecto LinkAidly**, independiente del código del frontend.  
Aquí se documentan la infraestructura, procesos, seguridad, arquitectura y backlog, sirviendo como referencia tanto técnica como organizativa.

Bienvenido a la documentación de LinkAidly. A continuación, encontrarás un índice con los principales documentos que hemos creado, junto con una breve descripción de su contenido.

## 🔗 Enlaces rápidos
- 📚 **API del frontend (TypeDoc):** [/web/docs/api/](/web/docs/api/)

- [architecture.md](architecture.md)  
  Describe la arquitectura general del sistema, incluyendo componentes clave, flujos de datos y tecnologías utilizadas.

- [infra.md](infra.md)  
  Explica la infraestructura técnica del proyecto, incluyendo servidores, servicios en la nube y configuración de red.

- [security.md](security.md)  
  Describe las medidas de seguridad implementadas y el cumplimiento con normativas aplicables.

- [process.md](process.md)  
  Detalla los procesos operativos y metodologías de trabajo que seguimos para el desarrollo y gestión del proyecto.

- [privacy.md](privacy.md)  
  Contiene las políticas de privacidad y consideraciones legales relacionadas con el manejo de datos de los usuarios.

- [backlog.md](backlog.md)  
  Lista de tareas, funcionalidades y mejoras pendientes para futuras versiones del proyecto.

- [tech-notes.md](tech-notes.md)  
  Apuntes técnicos y decisiones de diseño relevantes, incluyendo cambios de configuración y notas de implementación.
  
- [CHANGELOG.md](CHANGELOG.md)  
  Registro de cambios del proyecto, siguiendo buenas prácticas de versionado semántico.

- [design/](design/)  
  Carpeta que contiene materiales de diseño (logos editables, paletas de colores, tipografías, etc.).  
  Aquí se guardan las versiones de referencia que no se usan directamente en la web (por ejemplo, los logos no-solid en texto Montserrat).


## 🧭 Convenciones de documentación
- **Fuente de la verdad**: 
  - **Código/API** → documentación autogenerada con TypeDoc en `/web/docs/api/` (no duplicar aquí). 
  - **Arquitectura/procesos/seguridad** → esta carpeta `/docs`.
- **Estilo**: seguir la guía en [`docs/styleguide.md`](styleguide.md) (estructura, tono, enlaces, ejemplos).
- **ADRs**: decisiones de arquitectura en [`docs/adr/`](adr/) con índice en [`docs/adr/README.md`](adr/README.md).
- **Tech notes vs ADRs**: 
  - `tech-notes.md` → apuntes temporales o notas de implementación.
  - `adr/*` → decisiones estables con contexto y consecuencias.
- **Changelog**: usar `CHANGELOG.md` (Keep a Changelog + SemVer) para cambios relevantes de docs.
- **Idioma**: español claro, evitar jerga innecesaria; ejemplos concretos y breves.

## 🤝 Cómo contribuir a la documentación
1. Crea rama: `docs/<tema>` (o usa `feature/*` si va unido a código).
2. Edita los `.md` con commits atómicos y mensajes claros (Conventional Commits recomendado).
3. Abre PR a `dev` y señala qué documentos cambian y por qué.
4. Tras revisión, se mergea a `main`. 

---

## 📌 Notas
- La documentación aquí es **viva**: puede actualizarse en paralelo al desarrollo.
- Para detalles específicos del frontend (estructura de `/web`), ver el README dentro de `web/`.
