# Learning Cat web site

Página web dedicada a añadir apuntes sobre lenguajes, frameworks, herramientas... utilizadas en el proyecto Kairos.

Construida con **HUGO** utilizando ficheros **Markdown** y alojada con **GitHub Pages**

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

El proyecto está dividido en dos ramas:

- **Rama master**: Rama general del proyecto que contiene el código fuente del proyecto. Se hará commit de todos los cambios que se produzcan en el código fuente y que se quieran preservar.

- **Rama gh-pages**: Esta rama contiene el código generado por el comando `hugo` en la carpeta `public`, dicho código es una conversión del código fuente en una página web estática con ficheros html, css, multimedia, etc ... La carpeta public está ignorada para publicarse con la rama master del código fuente, lo que permite tener el código fuente separado de la página web generada. De esta manera mantenemos por separado el histórico, lo que permite poder realizar cambios en el fuente agenos a la construcción de web.

GitHub Pages está configurado para que tome la rama `gh-pages` como el fuente de publicación de la página web.

- ### Desplegar

    Al tener por separado el código fuente del código generado para publicar, si necesitamos desplegar algún cambio que hayamos realizado en la rama `master` podremos ejecutar el siguiente comando:

    ```console
    sh deploy.sh "Mensaje informativo de los cambios"
    ```

Este comando ejecuta un script que se encuenra en la raíz del fuente y sigue la siguient secuencia:

 - Comprueba que no haya cambios sin commitear en la rama master, en cuyo caso mostrará un mensaje indicándolo y no continuará con el script. 
 - Borrará la carpeta public si existe alguna en el proyecto, y volverá a generarla con el comando hugo.
 - Hará commit de los camabios en la rama `gh-pages`con el mensaje que le hemos pasado en el comando.
 - Hará push de los cambios quedando ya desplegados en github.

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
  - Se tendrá que especificar en el template:
    - El título de la sección `title`: Dará nombre a la subsección en el menú y también proporcionará el título en el contenido de la misma.
    - El orden que ocupará dentro de la sección padre `weight`
  - No se deberá añadir el parámetro de `chapter`.

  - Template de ejemplo:

    ```markdown
    +++
    title = "Instalar y ejecutar"
    weight = 1
    +++

    ## Instalar Python

    - sudo apt-get update
    - sudo apt-get install python3.6


    ## Comprobar versión de Python instalada

    - python3.6 -V
    ```

El árbol de carpetas y ficheros para las nuevas secciones quedaría así:

    content
    ├── _index.md //Fichero de portada principal de la web</span>
    └── [seccion-padre] //Carpeta de sección-padre Ej: python
        ├── _index.md //Fichero de portada de sección-padre
        └── [seccion-hija] //Carpeta de sección-hija Ej: install-run
            └── _index.md //Fichero de contenido de sección-hija

    

Se pueden hacer divisiones más profundas en el árbol siguiendo el mismo procedimiento.

### Enlcaces de interés

- [**Página oficial de HUGO**](https://gohugo.io/)
- [**Documentación GitHub Pages**](https://pages.github.com/)
- [**Documentación sobre template utilizado**](https://learn.netlify.com/en/)
- [**Documentación de Markdown**](https://daringfireball.net/projects/markdown/syntax)
- [**Editor de Markdown online**](https://stackedit.io/)
