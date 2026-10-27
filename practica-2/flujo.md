# Práctica 2: Comparación de flujos de ramas

## 1. GitFlow

GitFlow es una estrategia de trabajo con Git que utiliza varias ramas para organizar el desarrollo. Incluye ramas como `main`, `develop`, `feature`, `release` y `hotfix`. Permite separar el desarrollo de funcionalidades de la preparación de versiones y las correcciones urgentes. Puede ser útil en proyectos que manejan lanzamientos planificados.

## 2. Trunk-based development

Trunk-based development es una estrategia en la que los desarrolladores integran sus cambios frecuentemente en una rama principal compartida. Se trabaja con cambios pequeños y ramas de corta duración, utilizando pruebas y revisiones para mantener la calidad del código. Esto ayuda a detectar conflictos temprano y facilita la integración continua.

## 3. ¿Cuál elegiría para una aplicación web?

Para una aplicación web moderna, elegiría trunk-based development si el equipo cuenta con pruebas automatizadas, integración continua y revisión de código. Este enfoque permite integrar cambios con frecuencia y detectar errores rápidamente. Además, se pueden utilizar feature flags para controlar funcionalidades que todavía no están listas. Sin embargo, GitFlow también puede ser apropiado cuando el proyecto necesita ciclos de lanzamiento planificados y una separación más marcada entre las etapas de desarrollo. La elección depende de las necesidades del equipo y del proyecto.
