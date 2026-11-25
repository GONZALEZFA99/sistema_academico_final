# BITÁCORA DE PROMPTS — SISTEMA ACADÉMICO

**Proyecto:** Sistema Académico Universitario  
**Tecnologías:** Python 3.12, Django, SQLite, Bootstrap 5, HTML, CSS y JavaScript  
**Herramienta de apoyo:** ChatGPT (inteligencia artificial)  
**Metodología:** Desarrollo incremental, pruebas y corrección de errores.

---

## 1. Introducción

El presente documento registra los principales prompts y solicitudes utilizados durante el desarrollo del proyecto Sistema Académico Universitario.

La inteligencia artificial se utilizó como herramienta de apoyo para orientar la programación, explicar conceptos, implementar funcionalidades y solucionar problemas encontrados durante el desarrollo.

El trabajo se realizó progresivamente, mediante la creación de modelos, formularios, vistas, rutas, plantillas HTML y pruebas de funcionamiento.

**Nota:** Los prompts incluidos son ejemplos representativos y resúmenes de las solicitudes realizadas durante el desarrollo; no constituyen una transcripción literal de todas las conversaciones.

## 2. Prompt inicial: definición del proyecto

**Solicitud realizada:**

> Actúa como un profesor de Django que me guía paso a paso en un proyecto escolar. El proyecto se llama sistema_academico y utiliza las aplicaciones core y academico. Trabajaremos con Python 3.12, SQLite, Bootstrap 5 y vistas basadas en clases. Explica cada modificación y entrega el código archivo por archivo.

**Objetivo:** Establecer las tecnologías, la arquitectura y las reglas para desarrollar el proyecto.

**Resultado:** Se organizó la aplicación `core` para componentes reutilizables y `academico` para la lógica del sistema universitario.

## 3. Prompt: creación de modelos y relaciones

**Solicitud representativa:**

> Ayúdame a desarrollar los modelos del sistema académico utilizando herencia de ModeloBase y relaciones entre universidad, facultad, carrera, semestre, período, curso, profesor, estudiante, sección, matrícula y nota.

**Objetivo:** Implementar las entidades y relaciones de la base de datos.

**Resultado:** Se trabajó con los 11 modelos académicos, sus relaciones y las migraciones de Django.

**Verificación:** Se ejecutaron los comandos `makemigrations`, `migrate` y `check`.

## 4. Prompt: desarrollo de los CRUD

**Solicitud representativa:**

> Necesito crear los CRUD completos de cada modelo utilizando únicamente vistas basadas en clases. Incluye ListView, CreateView, UpdateView y DeleteView, además de formularios, rutas y plantillas HTML.

**Objetivo:** Permitir registrar, consultar, actualizar y eliminar información académica.

**Resultado:** Se implementaron los siguientes módulos:

1. Universidad
2. Facultad
3. Carrera
4. Semestre
5. Período
6. Curso
7. Profesor
8. Estudiante
9. Sección
10. Matrícula
11. Nota

Se incorporaron formularios Django, mensajes de confirmación y pantallas de eliminación.

## 5. Prompt: diseño profesional de las interfaces

**Solicitud representativa:**

> Quiero que las pantallas del Sistema Académico tengan un diseño profesional, uniforme y entendible, utilizando Bootstrap 5, colores institucionales y formularios organizados.

**Objetivo:** Mejorar la presentación visual y la experiencia de navegación.

**Resultado:** Se aplicó una identidad visual azul institucional, tarjetas informativas, tablas responsivas, buscadores y botones de acciones.

## 6. Prompt: filtros y exportación de reportes

**Solicitud representativa:**

> Agrega filtros, selección de columnas y exportaciones a Excel y PDF. El usuario debe poder personalizar los campos que desea visualizar.

**Objetivo:** Facilitar las consultas y la generación de reportes.

**Resultado:** Se utilizó el componente reutilizable `FiltroCamposMixin`, ubicado en `core`, para compartir funcionalidades entre los módulos.

**Tecnologías utilizadas:** `openpyxl` para Excel y `xhtml2pdf` para PDF.

## 7. Prompt: validación de matrículas

**Solicitud representativa:**

> Revisa las validaciones de matrícula para impedir que un estudiante se inscriba dos veces en la misma sección, que se exceda el cupo disponible o que se matricule en una asignatura incompatible con su carrera.

**Objetivo:** Mantener la consistencia de los registros académicos.

**Resultado:** Se revisaron y reforzaron las reglas de matrícula y la protección de las relaciones con otros modelos.

**Problema identificado:** Una eliminación de matrícula podía afectar las calificaciones relacionadas.

**Corrección:** Se incorporaron medidas de protección para evitar la eliminación accidental de registros académicos dependientes.

## 8. Prompt: registro y cálculo de notas

**Solicitud representativa:**

> Implementa el CRUD de notas con tres calificaciones entre 0 y 100. Calcula automáticamente el promedio e indica si el estudiante está aprobado o reprobado. La aprobación debe ser con un promedio mayor o igual a 70.

**Objetivo:** Automatizar los resultados académicos.

**Resultado:** Se incorporaron las calificaciones `n1`, `n2` y `n3`, el promedio y el estado académico.

También se implementó una vista previa del promedio en el formulario mediante JavaScript.

**Criterio aplicado:**

Promedio = (Nota 1 + Nota 2 + Nota 3) / 3.

- Promedio mayor o igual a 70: Aprobado.
- Promedio menor a 70: Reprobado.

## 9. Prompt: implementación del panel principal

**Solicitud realizada:**

> Necesito que al levantar el servidor aparezca una página de inicio que esté conectada con todos los CRUD para poder acceder a ellos desde un solo lugar.

**Objetivo:** Centralizar el acceso a los módulos.

**Resultado:** Se creó un Dashboard con tarjetas de navegación y estadísticas de estudiantes, cursos, matrículas y notas.

**Problema encontrado:** Al abrir la dirección principal del sistema aparecía un error `404 Page not found`.

**Causa:** La ruta de inicio se había agregado en `academico/urls.py` en lugar de `sistema_academico/urls.py`.

**Solución:** Se corrigió la ubicación de la ruta principal y se comprobó que el Dashboard cargara correctamente.

## 10. Prompt: autenticación y navegación

**Solicitud realizada:**

> Revisa profesionalmente todo el proyecto, agrega un login y coloca un botón para volver al inicio en las pantallas de los CRUD.

**Objetivo:** Mejorar la seguridad y la navegación.

**Resultado:** Se implementó un inicio de sesión propio del Sistema Académico, cierre de sesión y navegación entre el Dashboard y los módulos.

Se revisó la protección de las vistas mediante `LoginRequiredMixin`.

## 11. Prompt: revisión integral y pruebas

**Solicitud representativa:**

> Analiza el proyecto completo, revisa los modelos, formularios, vistas, rutas, validaciones, seguridad, reportes y operaciones CRUD. Corrige los problemas encontrados y entrega una versión mejorada.

**Objetivo:** Identificar errores funcionales y verificar la estabilidad del sistema.

**Resultado:** Se realizaron comprobaciones de Django y pruebas automatizadas de autenticación, rutas, operaciones CRUD y reportes.

En la revisión de la versión corregida se obtuvo un resultado de **17 pruebas automatizadas superadas**. Estas pruebas complementan, pero no sustituyen, las pruebas manuales de uso.

## 12. Prompt: datos de prueba

**Solicitud representativa:**

> Necesito registrar automáticamente los datos académicos establecidos en la guía mediante un comando de Django, evitando ingresar todos los registros manualmente.

**Objetivo:** Disponer de información para comprobar y demostrar el funcionamiento del sistema.

**Resultado:** Se utilizó el comando `python manage.py poblar_datos`.

Se comprobó la generación de:

- 15 estudiantes.
- 25 matrículas.
- 25 registros de notas.
- Instituciones, facultades, carreras, cursos, profesores, períodos y secciones relacionados.

## 13. Problemas adicionales y soluciones

| Problema encontrado | Solución aplicada |
|---|---|
| Error 404 en la página principal | Corrección de la ruta en el archivo principal de URLs |
| Necesidad de proteger las pantallas | Implementación y revisión de autenticación |
| Posibilidad de matrículas incompatibles | Validaciones de relaciones, carrera y cupos |
| Riesgo al eliminar datos relacionados | Protección de registros dependientes |
| Falta de navegación entre módulos | Dashboard y enlaces para volver al inicio |
| Base de datos vacía en una nueva instalación | Migraciones y comando `poblar_datos` |
| Dificultad para publicar cambios en GitHub | Configuración de Git, commits y publicación del repositorio |

## 14. Control de versiones

Durante el desarrollo se utilizó Git y GitHub para conservar diferentes avances del proyecto.

Se realizaron operaciones de inicialización del repositorio, preparación de archivos, creación de commits y publicación de versiones.

También se utilizó `.gitignore` para excluir archivos temporales, entornos virtuales y respaldos privados.

El código final se publicó en el repositorio:

https://github.com/GONZALEZFA99/sistema_academico_final

## 15. Conclusiones

El desarrollo del Sistema Académico permitió aplicar conceptos relacionados con programación orientada a objetos, relaciones de bases de datos, formularios, vistas basadas en clases, autenticación y generación de reportes.

La utilización de inteligencia artificial facilitó la identificación de errores, el análisis de alternativas y la explicación del código implementado.

El proceso se desarrolló de manera incremental, comprobando las funcionalidades antes de continuar con nuevas modificaciones.

Finalmente, se obtuvo un sistema académico con 11 módulos CRUD, panel principal, autenticación, validaciones y herramientas de consulta y exportación.

**Observación:** Esta bitácora resume los principales prompts y correcciones del proyecto. Las comprobaciones funcionales y la defensa del código deben acompañarse de la explicación del estudiante.