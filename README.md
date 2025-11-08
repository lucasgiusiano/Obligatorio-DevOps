🧭 Estrategia de control de versiones – GitFlow

Este documento describe la estrategia de ramificación, flujo de trabajo y convenciones que seguimos en el proyecto StockWiz DevOps Transformation, basada en el modelo GitFlow.
El objetivo es asegurar un ciclo de desarrollo ordenado, colaborativo y con despliegues controlados en múltiples ambientes (Dev, Test, Prod).

📂 Estructura de ramas

La estrategia GitFlow define cinco tipos principales de ramas, cada una con un propósito claro:

Tipo de rama	Convención	Propósito
main	main	Contiene el código estable y desplegado en producción.
develop	develop	Código integrado y probado, listo para el próximo release.
feature	feature/<nombre>	Desarrollo de nuevas funcionalidades o mejoras.
release	release/<versión>	Preparación de una nueva versión antes del despliegue a producción.
hotfix	hotfix/<nombre>	Correcciones urgentes directamente sobre producción.
🧩 Flujo de trabajo diario

Crear una nueva rama de feature

git checkout develop
git pull origin develop
git checkout -b feature/<nombre-feature>


Ejemplo:

git checkout -b feature/agregar-tests-login


Desarrollar la funcionalidad

Commits frecuentes y descriptivos:

git commit -m "feat: agrega validación de usuario en login"
git commit -m "test: añade pruebas unitarias al login service"


Abrir un Pull Request (PR)

Desde feature/<nombre> hacia develop.

Solicitar revisión a otro miembro del equipo.

El PR debe incluir:

Descripción breve del cambio.

Issue/tarea relacionada del tablero Kanban.

Checklist de verificación (tests, lint, build).

Merge aprobado a develop

Solo se hace merge tras aprobación de al menos 1 reviewer.

El merge debe ser tipo squash o rebase para mantener el historial limpio.

🚀 Ciclo de releases

Preparar un release

git checkout develop
git pull origin develop
git checkout -b release/v1.2.0


Actualizar versión en package.json, CHANGELOG.md o documentación.

Realizar pruebas integrales en ambiente de Test.

Merge de release

Si todo está correcto:

git checkout main
git merge --no-ff release/v1.2.0
git tag -a v1.2.0 -m "Release versión 1.2.0"
git checkout develop
git merge --no-ff release/v1.2.0
git push origin main develop --tags

🧯 Correcciones urgentes (Hotfix)

Crear una rama desde main:

git checkout main
git checkout -b hotfix/fix-error-pago


Aplicar el cambio, probar y hacer merge:

git commit -m "fix: corrige error en módulo de pagos"
git checkout main
git merge --no-ff hotfix/fix-error-pago
git tag -a v1.2.1 -m "Hotfix: corrección de pagos"
git checkout develop
git merge --no-ff hotfix/fix-error-pago
git push origin main develop --tags

🏷️ Tags y Releases

Tags: identifican versiones estables listas para producción.
Ejemplo: v1.2.0, v1.2.1.

Releases: se crean automáticamente o manualmente desde GitHub/GitLab, adjuntando changelog y artefactos relevantes.

🔁 Buenas prácticas

Nunca hacer commit directo en main ni develop.

Siempre trabajar en ramas feature/* y abrir PRs.

Mantener los commits limpios y descriptivos.

Borrar ramas feature una vez mergeadas.

Ejecutar los pipelines CI/CD antes de hacer merge.

Documentar cambios significativos en CHANGELOG.md.

📊 Flujo resumido
feature/*  →  develop  →  release/*  →  main
                ↑          ↓           ↓
             hotfix/*  →  develop  →  main
