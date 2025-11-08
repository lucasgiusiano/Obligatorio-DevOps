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

- **`release/<versión>`**  
Se crean desde develop cuando se prepara una nueva versión estable.
Permiten realizar ajustes menores, pruebas finales y generación de documentación antes del despliegue.
Ejemplo:

```bash
git checkout develop
git checkout -b release/1.2.0
```

- **`hotfix/<nombre-fix>`** 
Se crean desde main para resolver errores críticos en producción.
Luego se fusionan tanto en main como en develop para mantener la coherencia.
Ejemplo:

```bash
git checkout main
git pull
git checkout -b hotfix/corregir-error-pago
