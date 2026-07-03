# Matemáticas aplicadas X 

**Departamento de Ciencias Físicas, Exactas & Energía / FIDCA**

## Presentación

Este Jupyter Book reúne el material académico del curso **[nombre del curso]** de la **Universidad Icesi**. Su propósito es ofrecer a los estudiantes un recurso organizado, interactivo y reproducible para el estudio de los conceptos, métodos y aplicaciones abordados durante el curso.

El libro integra explicaciones conceptuales, ejemplos desarrollados, cuadernos computacionales y actividades prácticas diseñadas para apoyar el aprendizaje autónomo y el trabajo en clase. A través de los Notebooks de Jupyter, los estudiantes podrán ejecutar código, explorar resultados, modificar ejemplos y fortalecer la comprensión de los temas desde una perspectiva aplicada.

Este material se actualizará durante el semestre de acuerdo con el avance del curso y las necesidades académicas identificadas en el proceso de enseñanza-aprendizaje.

La labor editorial de este Jupyter Book es realizada por **Angela Villota** y **Aníbal Sosa**, quienes apoyan la organización, revisión y adecuación del material académico.

## Uso de esta plantilla

Este repositorio funciona como plantilla para construir Jupyter Books de cursos de **Matemáticas Aplicadas**. Para crear el libro de un curso real, conserva la estructura base y reemplaza los campos marcados con corchetes, por ejemplo `[nombre del curso]`, `[docente]`, `[semestre]` y `[tema]`.

Para instrucciones detalladas de adaptación, publicación y manejo de imágenes, consulta [`GUIA_USO_TEMPLATE.md`](GUIA_USO_TEMPLATE.md).

La estructura base del curso está pensada alrededor de cuatro componentes:

- `Jornadas/`: planeación y organización de sesiones, semanas o módulos.
- `Notebooks/`: cuadernos computacionales que se publican en el libro.
- `Entregas/`: talleres, tareas, seguimientos, instrucciones y rúbricas.
- `Proyecto/`: lineamientos del proyecto aplicado del curso.

## Estructura del repositorio

- `myst.yml`: configuración principal del libro y tabla de contenido.
- `README.md`: página inicial del Jupyter Book.
- `Jornadas/`: materiales guía para cada jornada o tema.
- `Notebooks/`: Notebooks base del curso.
- `Proyecto/`: instrucciones, avances y rúbricas del proyecto aplicado.
- `Entregas/`: actividades evaluables y lineamientos de entrega.
- `_static/`: logos y estilos institucionales.

## Cómo adaptar esta plantilla

1. Cambia el título del curso, la descripción, autores, repositorio y Binder en `myst.yml`.
2. Edita la sección `Presentación` de este archivo con la información real del curso.
3. Organiza las sesiones en `Jornadas/` y enlaza los Notebooks correspondientes.
4. Ubica los cuadernos computacionales en `Notebooks/`.
5. Usa `Entregas/` para instrucciones de talleres, tareas, seguimientos o reportes.
6. Usa `Proyecto/` para la descripción del proyecto aplicado, avances y rúbrica.
7. Agrega cada página o Notebook nuevo a la sección `toc` de `myst.yml`.
8. Antes de publicar, limpia salidas pesadas, rutas locales y datos sensibles.

## Desarrollo local

Instala las dependencias:

```bash
python -m pip install -r requirements.txt
```

Construye o sirve el libro con MyST:

```bash
myst build --html
myst start
```

## Recomendaciones editoriales

- Usa un título claro por cuaderno: tema, jornada y resultado de aprendizaje.
- Incluye objetivos, conceptos previos, ejemplos, ejercicios y cierre.
- Separa texto conceptual, código y actividades evaluables.
- Evita rutas locales de Colab o Google Drive dentro de Notebooks publicados.
- Borra salidas grandes, imágenes embebidas innecesarias y datos sensibles.
- Mantén una nomenclatura consistente para Notebooks y entregas.
- Documenta los datos necesarios para ejecutar cada actividad.

## Contacto editorial

- **Angela Villota**: apvillota@icesi.edu.co
- **Aníbal Sosa**: uasosa@icesi.edu.co
