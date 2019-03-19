# Learning Cat web site

Página web dedicada a añadir apuntes sobre lenguajes, frameworks, herramientas... útiles para el proyecto Kairos.

Construida con **HUGO** utilizando ficheros **Markdown** vitaminados y alojada con **GitHub Pages**

## Arrancar en local

```console
hugo server
```

## Generar el fuente

El comando a continuación generará el fuente de la web dentro de la carpeta `public`

```console
hugo
```

## Actualizaciones en el proyecto

El proceso normal de subida de los cambios efectuados en el proyecto al repositorio será como la habitual.

La subida de cambios en el proyecto no implica el despliegue del mismo. Si queremos desplegar los cambios efectuados tendremos que seguir los siguientes pasos.

- ### Desplegar

    Se hará uso del script de despliegue que incluye el proyecto,habrá que ejecutarlo poniendo seguido de un mensaje que será el que figure como commit.

    ```console
    /.deploy.sh "Mensaje informativo de los cambios"
    ```

    Este script genera código fuente de la web en una carpeta llamada `public`. GitHub Pages está configurado para que coja el fuente de la web estática de dicha carpeta.

## Añadir nuevas secciones

Dentro de la carpeta content del proyecto habrá que crear otra carpeta que contendrá los ficheros markdown de la nueva sección.
Los nombres de las carpetas no soportan camelCase, las palabras que conformen en nombre de las carpetas tendrán que estar separadas por un guión medio.

- ### Página principal de la sección

  - Página principal de la sección (otorga el título a la sección)

  - Se creará un fichero llamado _index.md dentro de la nueva carpeta de la sección que será su portada.

  - Template de ejemplo:

    ```markdown
    +++
    title = "Python"
    weight = 1
    pre = "<i class='fab fa-python'></i> "
    chapter = true
    +++

    ### Entorno y lenguaje

    # Python

    En este capítulo se hablará sobre cómo instalar y ejecutar python en un sistema unix, así como un manual sobre el lenguaje.

    > ##### <i class='fab fa-python'></i>  Web oficial:  https://www.python.org/
    ```

  - El orden en el que se coloca la sección viene dado por el parámetro `weight` que figura en la portada

  - El parámetro `pre` sirve para añadir un elemento html justo antes del título.

  - El parámetro `title` es el que da nombre a la sección, aparecerá como título dentro del contenido de la misma y también en la barra de navegación.

- #### Subsecciones
  - Se creará una carpeta que contendrá el archivo de la subsección. Dicho archivo tendrá que tener el nombre _index.md

  - Template de ejemplo:

    ```markdown
    +++
    title = "Instalar y ejecutar"
    +++

    ## Instalar Python

    - sudo apt-get update
    - sudo apt-get install python3.6


    ## Comprobar versión de Python instalada

    - python3.6 -V
    ```

  - Se pueden incluir otros parámetros como en la portada en caso de ser necesarios, por ejemplo para añadir un orden determinado a las subsecciones o elemento html antes del título. No se deberá añadir el parámetro de `chapter`.

El árbol de carpetas y ficheros para las nuevas secciones quedaría así:

    content
    ├── [seccion-padre] //Carpeta de sección-padre Ej: python
    │   ├── [seccion-hija] //Carpeta de sección-hija Ej: install-run
    │   │   └── _index.md //Fichero de contenido de sección-hija
    │   └── _index.md //Fichero de portada de sección-padre
    └── _index.md //Fichero de portada principal de la web

Se pueden hacer divisiones más profundas en el árbol siguiendo el mismo procedimiento.

### Enlcaces de interés

- [**Página oficial de HUGO**](https://gohugo.io/)
- [**Documentación GitHub Pages**](https://pages.github.com/)
- [**Documentación sobre template utilizado**](https://learn.netlify.com/en/)
- [**Documentación de Markdown**](https://daringfireball.net/projects/markdown/syntax)
- [**Editor de Markdown online**](https://stackedit.io/)