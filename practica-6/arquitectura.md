
# Arquitectura del repositorio ISW2-Practicas

## 1. Descripción general

El repositorio ISW2-Practicas tiene como objetivo organizar y almacenar las actividades académicas desarrolladas durante la asignatura de Ingeniería de Software II.

Su estructura permite mantener las prácticas separadas, documentar los trabajos realizados y utilizar Git y GitHub para administrar los cambios y el historial del proyecto.

## 2. C4 Nivel 1: Diagrama de contexto

El diagrama de contexto representa la interacción entre los usuarios y el repositorio, identificando los actores principales y los sistemas externos.

```mermaid
C4Context
    title C4 Nivel 1 - Contexto del sistema

    Person(estudiante, "Estudiante", "Desarrolla y entrega las prácticas académicas.")
    Person(docente, "Docente", "Consulta y evalúa los entregables.")

    System(repo, "ISW2-Practicas", "Repositorio académico que almacena prácticas, documentación y entregables.")

    System_Ext(github, "GitHub", "Plataforma de alojamiento y colaboración.")

    Rel(estudiante, repo, "Desarrolla y organiza las prácticas")
    Rel(estudiante, github, "Publica cambios y administra versiones")
    Rel(github, repo, "Almacena el repositorio remoto")
    Rel(docente, github, "Consulta y revisa los entregables")
```

### Justificación

El estudiante representa al usuario principal del sistema, encargado de desarrollar y organizar las prácticas. GitHub proporciona el entorno para almacenar el repositorio y gestionar los cambios mediante ramas y Pull Requests.

El docente interactúa con la plataforma para consultar los entregables y evaluar el trabajo realizado. Este nivel permite identificar el propósito del repositorio y sus principales relaciones externas.

## 3. C4 Nivel 2: Diagrama de contenedores

El diagrama de contenedores representa la organización interna del repositorio y los principales elementos que lo componen.

```mermaid
C4Container
    title C4 Nivel 2 - Contenedores del sistema

    Person(estudiante, "Estudiante", "Administra el repositorio.")

    System_Boundary(repo, "ISW2-Practicas") {
        Container(readme, "README.md", "Markdown", "Contiene información general e identificación del propietario.")
        Container(practicas, "Carpetas de prácticas", "Directorios", "Almacenan los ejercicios y entregables académicos.")
        Container(arquitectura, "arquitectura.md", "Markdown y Mermaid", "Documenta la arquitectura mediante diagramas C4.")
        Container(git, "Control de versiones", "Git", "Gestiona commits, ramas e historial de cambios.")
    }

    System_Ext(github, "GitHub", "Alojamiento remoto del repositorio.")

    Rel(estudiante, readme, "Consulta y actualiza")
    Rel(estudiante, practicas, "Desarrolla y organiza")
    Rel(estudiante, arquitectura, "Documenta")
    Rel(estudiante, git, "Realiza commits y crea ramas")
    Rel(git, github, "Sincroniza mediante push y pull")
    Rel(github, practicas, "Almacena los entregables")
    Rel(github, arquitectura, "Almacena la documentación")
```

### Justificación

El repositorio está organizado en cuatro componentes principales:

- **README.md:** contiene información general e identificación del propietario.
- **Carpetas de prácticas:** permiten separar y organizar los ejercicios académicos.
- **arquitectura.md:** documenta la estructura y las relaciones del sistema mediante diagramas C4.
- **Git:** permite controlar las versiones, registrar modificaciones y trabajar mediante ramas independientes.

GitHub funciona como plataforma de almacenamiento remoto y permite integrar cambios mediante Pull Requests.

## 4. Conclusión

La arquitectura propuesta permite comprender la estructura y funcionamiento del repositorio ISW2-Practicas desde una perspectiva externa e interna. La separación de las prácticas y la utilización del control de versiones facilitan la organización, mantenimiento y evaluación de los entregables académicos.
