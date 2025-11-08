## Estrategia de Control de Versiones: Git Flow

Para el desarrollo de este proyecto se utiliza la **estrategia Git Flow**, una metodología ampliamente adoptada que facilita el trabajo colaborativo y el versionado ordenado del código.  
Esta estrategia permite desarrollar nuevas funcionalidades de forma aislada, mantener un flujo claro de integración y generar versiones estables y trazables.

---

### 🌿 Ramas principales

- **`main`**  
  Contiene el código en estado **estable y listo para producción**.  
  Cada versión liberada se etiqueta con un tag (`v1.0.0`, `v1.1.0`, etc.).

- **`develop`**  
  Contiene el código en estado **integrado y en pruebas**.  
  Todas las nuevas funcionalidades se fusionan aquí antes de ser promovidas a producción.

---

### 🌱 Ramas de soporte

- **`feature/<nombre-feature>`**  
  Se crean desde `develop` para desarrollar nuevas funcionalidades o mejoras.  
  Una vez completada la tarea, se abre un **Pull Request (PR)** hacia `develop`.  
  Ejemplo:  
  ```bash
  git checkout develop
  git pull
  git checkout -b feature/agregar-autenticacion

  🔁 Flujo de trabajo general

Crear una rama feature desde develop.

Desarrollar la funcionalidad y hacer commits descriptivos.

Abrir un Pull Request hacia develop y solicitar revisión de código.

Una vez aprobado el PR, fusionar (merge) y eliminar la rama feature.

Cuando se completa un conjunto de funcionalidades, crear una rama release desde develop.

Realizar pruebas y ajustes; luego fusionar en main y etiquetar la versión.

Si se detectan errores críticos en producción, crear un hotfix desde main.

🧩 Pull Requests (PRs) y Revisiones

Cada PR debe:

Estar asociado a una tarea del tablero (Kanban/Scrum).

Incluir una descripción clara de los cambios realizados.

Pasar los tests automáticos del pipeline CI/CD antes del merge.

Contar con al menos una revisión de código de otro integrante del equipo.

🏷️ Tags y Releases

Cada despliegue a producción se identifica con un tag semántico:
v<MAJOR>.<MINOR>.<PATCH> (por ejemplo: v1.3.2).

MAJOR: cambios incompatibles.

MINOR: nuevas funcionalidades retrocompatibles.

PATCH: correcciones o mejoras menores.

Ejemplo de creación de un tag y release:

git checkout main
git pull
git tag -a v1.3.2 -m "Release versión 1.3.2 - mejora de rendimiento en checkout"
git push origin v1.3.2

📦 Recomendaciones

Mantener ramas cortas y bien definidas.

Realizar commits atómicos y descriptivos.

Sincronizar frecuentemente con develop para evitar conflictos.

No realizar merges directos a main sin pasar por release o hotfix.

Usar PRs como instancia de revisión y control de calidad del código.

Resumen visual del flujo Git Flow:

main ──────●─────────────●───────────────●──────────────▶
             ↖ hotfix     ↖ release       ↖ release
develop ────●──────●──────●───────────────●──────────────▶
              ↖feature1    ↖feature2       ↖feature3

