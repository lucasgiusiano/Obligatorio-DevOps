Perfecto, aquí tienes el contenido **completo dentro de un solo bloque markdown**, tal cual podrías copiarlo directamente en tu `README.md` sin modificaciones:

---

````markdown
# Estrategia de Control de Versiones: Git Flow

Para el desarrollo de este proyecto se utiliza la **estrategia Git Flow**, una metodología ampliamente adoptada que facilita el trabajo colaborativo y el versionado ordenado del código.  
Esta estrategia permite desarrollar nuevas funcionalidades de forma aislada, mantener un flujo claro de integración y generar versiones estables y trazables.

---

## 🌿 Ramas principales

- **`main`**  
  Contiene el código en estado **estable y listo para producción**.  
  Cada versión liberada se etiqueta con un tag (`v1.0.0`, `v1.1.0`, etc.).

- **`develop`**  
  Contiene el código en estado **integrado y en pruebas**.  
  Todas las nuevas funcionalidades se fusionan aquí antes de ser promovidas a producción.

---

## 🌱 Ramas de soporte

- **`feature/<nombre-feature>`**  
  Se crean desde `develop` para desarrollar nuevas funcionalidades o mejoras.  
  Una vez completada la tarea, se abre un **Pull Request (PR)** hacia `develop`.  
  Ejemplo:  
  ```bash
  git checkout develop
  git pull
  git checkout -b feature/agregar-autenticacion
  ```

* **`release/<versión>`**
  Se crean desde `develop` cuando se prepara una nueva versión estable.
  Permiten realizar ajustes menores, pruebas finales y generación de documentación antes del despliegue.
  Ejemplo:

  ```bash
  git checkout develop
  git checkout -b release/1.2.0
  ```

* **`hotfix/<nombre-fix>`**
  Se crean desde `main` para resolver errores críticos en producción.
  Luego se fusionan tanto en `main` como en `develop` para mantener la coherencia.
  Ejemplo:

  ```bash
  git checkout main
  git pull
  git checkout -b hotfix/corregir-error-pago
  ```

---

## 🔁 Flujo de trabajo general

1. Crear una rama `feature` desde `develop`.
2. Desarrollar la funcionalidad y hacer commits descriptivos.
3. Abrir un **Pull Request** hacia `develop` y solicitar revisión de código.
4. Una vez aprobado el PR, fusionar (`merge`) y eliminar la rama `feature`.
5. Cuando se completa un conjunto de funcionalidades, crear una rama `release` desde `develop`.
6. Realizar pruebas y ajustes; luego fusionar en `main` y etiquetar la versión.
7. Si se detectan errores críticos en producción, crear un `hotfix` desde `main`.

---

## 🧩 Pull Requests (PRs) y Revisiones

Cada PR debe cumplir con los siguientes criterios:

* Estar asociado a una tarea del tablero (Kanban/Scrum).
* Incluir una descripción clara de los cambios realizados.
* Pasar los tests automáticos del pipeline CI/CD antes del merge.
* Contar con **al menos una revisión de código** de otro integrante del equipo.

---

## 🏷️ Tags y Releases

Cada despliegue a producción se identifica con un **tag semántico** siguiendo la convención:

```
v<MAJOR>.<MINOR>.<PATCH>
```

Ejemplos:

* `v1.0.0` → Primera versión estable.
* `v1.1.0` → Nueva funcionalidad agregada.
* `v1.1.1` → Corrección menor o parche.

### Creación de un tag y release:

```bash
git checkout main
git pull
git tag -a v1.3.2 -m "Release versión 1.3.2 - mejora de rendimiento en checkout"
git push origin v1.3.2
```

Los tags se utilizan para generar **releases** que reflejan los hitos principales del proyecto.
Estos releases se documentan en el repositorio con sus notas de versión y cambios más relevantes.

---

## 📦 Recomendaciones de Buenas Prácticas

* Mantener ramas cortas y bien definidas.
* Realizar commits atómicos y descriptivos.
* Sincronizar frecuentemente con `develop` para evitar conflictos.
* No realizar merges directos a `main` sin pasar por `release` o `hotfix`.
* Usar PRs como instancia de revisión y control de calidad del código.

---

## 📈 Resumen visual del flujo Git Flow

```
main ──────●─────────────●───────────────●──────────────▶
             ↖ hotfix     ↖ release       ↖ release
develop ────●──────●──────●───────────────●──────────────▶
              ↖feature1    ↖feature2       ↖feature3
```

---

## 🎯 Objetivo

Mantener un flujo de desarrollo **controlado, colaborativo y trazable**, asegurando versiones estables, integraciones predecibles y una mejor calidad en los despliegues continuos.

