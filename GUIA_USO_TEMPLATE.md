# Guia de uso de la plantilla

Esta guia describe el protocolo recomendado para crear un Jupyter Book de curso a partir de esta plantilla. La plantilla esta pensada para cursos de Matematicas Aplicadas y conserva una estructura comun para facilitar el mantenimiento entre cursos.

## 1. Crear un nuevo repositorio

1. En GitHub, usa este repositorio como plantilla para crear un nuevo repositorio del curso.
2. Usa un nombre claro para el repositorio, por ejemplo `Matematicas-Aplicadas-III` o `Calculo-Vectorial`.
3. Clona el nuevo repositorio en tu computador:

```bash
git clone https://github.com/Icesi-MA/NOMBRE-DEL-REPO.git
cd NOMBRE-DEL-REPO
```

## 2. Ajustar la configuracion del libro

Edita `myst.yml` y reemplaza los valores de la plantilla por los del curso real:

```yaml
project:
  title: Matematicas Aplicadas III
  description: "Material interactivo y reproducible para el curso Matematicas Aplicadas III de la Universidad Icesi."
  authors:
    - name: "Editores: Nombre docente"
  github: https://github.com/Icesi-MA/NOMBRE-DEL-REPO
  jupyter:
    binder:
      repo: Icesi-MA/NOMBRE-DEL-REPO
      ref: main

site:
  options:
    logo_text: Matematicas Aplicadas III
```

Revisa especialmente estos campos:

- `project.title`
- `project.description`
- `project.authors`
- `project.github`
- `project.jupyter.binder.repo`
- `site.options.logo_text`

## 3. Editar la pagina inicial

Edita `README.md` con la informacion real del curso:

- nombre del curso;
- departamento o unidad academica;
- presentacion del curso;
- docentes o equipo editorial;
- forma de uso del libro;
- enlaces institucionales necesarios.

El `README.md` es la pagina inicial del Jupyter Book. Evita dejar marcadores como `[nombre del curso]`, `[docente]`, `[semestre]` o `[tema]` antes de publicar.

## 4. Conservar la estructura base

La estructura del repositorio debe mantenerse asi:

```text
Jornadas/
Notebooks/
Entregas/
Proyecto/
plantillas/
_static/
```

Usa cada carpeta con este criterio:

- `Jornadas/`: planeacion, sesiones, semanas o modulos del curso.
- `Notebooks/`: cuadernos computacionales publicados en el libro.
- `Entregas/`: talleres, tareas, seguimientos, reportes y rubricas.
- `Proyecto/`: descripcion, avances, entregables y rubrica del proyecto aplicado.
- `plantillas/`: archivos de referencia para crear nuevos contenidos.
- `_static/`: estilos, logos, imagenes y archivos estaticos del libro.

No agregues `plantillas/` como seccion visible de la tabla de contenido. Es una carpeta de referencia para quienes editan el curso.

## 5. Crear nuevos contenidos

Para crear una nueva seccion en Markdown:

1. Duplica `plantillas/seccion_base.md`.
2. Renombra el archivo y ubicalo en `Jornadas/`, `Entregas/` o `Proyecto/`.
3. Ajusta titulo, objetivos, instrucciones y recursos.
4. Agrega la pagina a la tabla de contenido si debe aparecer publicada.

Para crear un nuevo Notebook:

1. Duplica `plantillas/cuaderno_base.ipynb`.
2. Renombra el archivo con una convencion clara.
3. Ubicalo en `Notebooks/`.
4. Edita titulo, objetivos, explicaciones, codigo y ejercicios.
5. Limpia salidas pesadas antes de confirmar cambios.

Convenciones sugeridas:

```text
Notebooks/ma3_00_introduccion.ipynb
Notebooks/ma3_01_integrales_dobles.ipynb
Jornadas/jornada_01_integracion_multiple.md
Entregas/taller_01_integrales_dobles.md
Proyecto/proyecto_aplicado.md
```

## 6. Protocolo para imagenes

Las imagenes deben guardarse como archivos del repositorio, no pegadas como salidas embebidas en los Notebooks. Esto mantiene el repositorio liviano y facilita que las imagenes funcionen en GitHub Pages, Binder y builds locales.

### Carpeta recomendada

Usa esta estructura:

```text
_static/images/
```

Si el curso usa muchas imagenes, crea subcarpetas:

```text
_static/images/intro/
_static/images/jornadas/
_static/images/notebooks/
_static/images/proyecto/
```

### Nombres de archivos

Usa nombres cortos, descriptivos y sin espacios:

```text
integral_doble_region.png
campo_vectorial_ejemplo.svg
modelo_crecimiento_poblacional.jpg
```

Evita:

```text
Captura de pantalla 2026-07-02 a la(s) 10.12.18 AM.png
imagen final FINAL nueva.png
```

### Formatos recomendados

- Usa `.png` para capturas, diagramas con texto o imagenes de interfaz.
- Usa `.jpg` o `.jpeg` para fotografias.
- Usa `.svg` para logos, iconos o diagramas vectoriales.
- Evita imagenes muy pesadas. Como criterio practico, intenta mantener cada imagen por debajo de `1 MB` cuando sea posible.

### Como referenciar imagenes desde Markdown

Desde `README.md`, que esta en la raiz:

```md
![Descripcion de la imagen](_static/images/nombre_imagen.png)
```

Desde archivos dentro de `Jornadas/`, `Entregas/`, `Proyecto/` o `Notebooks/`:

```md
![Descripcion de la imagen](../_static/images/nombre_imagen.png)
```

Ejemplo desde un Notebook en `Notebooks/`:

```md
![Region de integracion](../_static/images/notebooks/integral_doble_region.png)
```

### Imagenes generadas por codigo

Si una figura se genera con Python, hay dos opciones:

1. Mantener el codigo que genera la figura y limpiar la salida antes de publicar.
2. Guardar la figura como archivo en `_static/images/` y referenciarla desde Markdown.

Ejemplo:

```python
fig.savefig("../_static/images/notebooks/integral_doble_region.png", dpi=150, bbox_inches="tight")
```

Si el Notebook esta en `Notebooks/`, la ruta anterior guarda la imagen en la carpeta compartida `_static/images/notebooks/`.

### Que evitar

Evita confirmar al repositorio:

- salidas de Notebook con imagenes base64 muy grandes;
- capturas pegadas directamente en celdas Markdown si quedan embebidas en el `.ipynb`;
- imagenes con rutas locales como `/Users/...`, `C:\...` o Google Drive;
- imagenes duplicadas en varias carpetas;
- archivos temporales como `.DS_Store`.

Antes de hacer commit, revisa que las rutas de imagen sean relativas y funcionen desde el libro construido.

## 7. Protocolo para Notebooks

Antes de publicar un Notebook:

1. Verifica que el titulo y los objetivos esten completos.
2. Ejecuta las celdas necesarias para comprobar que el codigo funciona.
3. Limpia salidas grandes o innecesarias.
4. Elimina rutas locales, tokens, datos sensibles o credenciales.
5. Usa datos pequenos o documenta como obtener los datos externos.
6. Revisa que todas las imagenes usen rutas relativas.

Si el Notebook debe conservar resultados, deja solo las salidas necesarias para la lectura del estudiante.

## 8. Desarrollo local

Instala dependencias:

```bash
python -m pip install -r requirements.txt
```

Sirve el libro localmente:

```bash
jupyter book start
```

Tambien puedes construir HTML:

```bash
jupyter book build --html
```

Antes de publicar, revisa:

- que no haya errores de build;
- que el logo y los estilos carguen correctamente;
- que la tabla de contenido tenga las secciones esperadas;
- que las imagenes se vean en notebooks y paginas Markdown;
- que no aparezca `plantillas/` como seccion del libro.

## 9. Publicacion en GitHub Pages

En el repositorio del curso:

1. En GitHub, entra a `Settings > Pages`.
2. Selecciona `Source: GitHub Actions`.
3. Confirma que el workflow `.github/workflows/deploy.yml` exista.
4. Haz push a `main`.
5. Revisa el workflow en `Actions`.

La URL esperada normalmente sera:

```text
https://icesi-ma.github.io/NOMBRE-DEL-REPO/
```

## 10. Lista rapida antes de publicar

- `myst.yml` tiene el titulo real del curso.
- `myst.yml` tiene el repositorio real en `github` y `binder.repo`.
- `README.md` no contiene marcadores sin reemplazar.
- `Notebooks/` contiene solo cuadernos que deben publicarse.
- `plantillas/` no aparece en la tabla de contenido.
- Las imagenes estan en `_static/images/`.
- Las rutas de imagenes son relativas.
- No hay `.DS_Store`, `_build/`, salidas pesadas o archivos temporales en el commit.
- El libro corre localmente con `jupyter book start`.
- GitHub Pages esta configurado para desplegar con GitHub Actions.
