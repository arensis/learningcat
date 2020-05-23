# Learning Cat web site

Página web dedicada a añadir apuntes sobre lenguajes, frameworks, herramientas...

Construida con **HUGO** y **HUGO-LEARN-TEMPLATE** utilizando ficheros **Markdown** y alojada con **GitHub Pages**

## Submodulo del template de HUGO

El template de HUGO es necesario tanto para arrancar el servidor en local como para desplegar ya que dispone de toda la organización del contenido y estilos de la web.
El template se ha añadido como un submodulo de git, por tanto para poder arrancar el servidor y desplegar es necesario haberlo inicializado y actualizado.

En caso de encontrar en el arranque / despliegue errores sobre el template, tratar de inicializar y actualizar el submodulo de git.

- Inicializar el submodulo

  ```console
  git submodule init
  ```

- Actualizar el submodulo para que se posicione en el commit configurado del repositorio

  ```console
  git submodule update
  ```

- Cambiar el commit al que apunta el submodulo en el repositorio

  1. Entrar en la carpeta que contiene el submodulo `themes/hugo-theme-lear`

  2. Situarse en la rama que tiene como último commit el que se quiere que apunte el submodulo o directamente en el commit al que se quiere que apunte el submodulo

  3. Volver a la raíz del proyecto para indexar y hacer commit de los cambios

## Arrancar en local

El comando a continuación levantará un servidor web que permite cambios en caliente.

```console
hugo server
```

## Renderizar

El comando a continuación ejecutará el renderizado del proyecto, que es una conversión del código fuente en una página web estática con ficheros html, css, multimedia, etc ..., y se volcará el resultado en la carpeta  `public` del repositorio.

```console
hugo
```

## Actualizaciones en el proyecto

El proyecto está dividido en dos ramas, lo que nos permite tener por separado el código fuente del renderizado con históricos diferentes:

- **Rama master**: Rama principal del proyecto que contiene el código fuente. Se hará commit de todos los cambios que se produzcan y que se quieran preservar. La carpeta public está ignorada para no incluir el renderizado dentro del repositorio.

- **Rama gh-pages**: Rama de despliegue y publicación del proyecto. Contiene el código renderizado por el comando `hugo`, está configurada con GitHub Pages como fuente de publicación de la página web, por tanto todos los cambios que se hagan en esta rama se publicarán automáticamente por github pages.

- ### Desplegar

    Para desplegar podremos ejecutar un script sh que se encuentra en la raíz el proyecto añadiéndo el mensaje que queremos que aparezca como mensaje del commit:

    ```console
    sh deploy.sh "Mensaje informativo de los cambios"
    ```

    Este comando sigue la siguient secuencia:
      - Comprueba que no haya cambios sin commitear en la rama master, en cuyo caso mostrará un mensaje indicándolo y no continuará con el script.
      - Borrará la carpeta public si existe alguna en el proyecto, y volverá a generarla con el comando hugo.
      - Hará commit de los camabios en la rama `gh-pages`con el mensaje que le hemos pasado en el comando.
      - Hará push de los cambios quedando ya desplegados en github.

## Añadir nuevas secciones

Dentro de la carpeta content del proyecto habrá que crear otra carpeta que contendrá los ficheros markdown de la nueva sección.
Los nombres de las carpetas no soportan camelCase, las palabras que conformen en nombre de las carpetas tendrán que estar separadas por un guión medio.

- ### Página principal de la sección

  - Página principal de la sección (otorga el título a la sección)

  - Se creará un fichero llamado `_index.md` dentro de la nueva carpeta de la sección que será su portada.

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

  - El orden en el que se coloca la sección viene dado por el parámetro `weight` que figura en la portada, deberá ser un número único entre todas las secciones, y éstas se ordenaran ascendentemente según éste valor.

  - El parámetro `pre` sirve para añadir un elemento html justo antes del título, pero ésto sólo se verá representado en la barra de navegación.

  - El parámetro `title` es el que da nombre a la sección, aparecerá como título dentro del contenido de la misma y también en la barra de navegación.

- ### Subsecciones

  - Se creará una carpeta que contendrá el archivo de la subsección. Dicho archivo tendrá que tener el nombre `_index.md`
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
    ├── _index.md //Fichero de portada principal de la web
    └── [seccion-padre] //Carpeta de sección-padre Ej: python
           ├── index.md //Fichero de portada de sección-padre
           └── [seccion-hija] //Carpeta de sección-hija Ej: install-run
                  └── index.md //Fichero de contenido de sección-hija

Se pueden hacer divisiones más profundas en el árbol siguiendo el mismo procedimiento.

### Enlcaces de interés

- [**Página oficial de HUGO**](https://gohugo.io/)
- [**Documentación GitHub Pages**](https://pages.github.com/)
- [**Documentación sobre template utilizado**](https://learn.netlify.com/en/)
- [**Documentación de Markdown**](https://daringfireball.net/projects/markdown/syntax)
- [**Editor de Markdown online**](https://stackedit.io/)
