+++
title = "Descarga e instalación del IDE"
pre = "<i class='fa fa-folder-open' aria-hidden='true'></i> "
weight = 1
+++

## Descarga

El IDE de arduino con el que podremos desarrollar el código, compilarlo y cargarlo en la placa de desarrollo se puede descargar gratuitamente desde la web de Arudino: 

<i class="fa fa-link" aria-hidden="true"></i> https://www.arduino.cc/en/Main/Software

## Instalación

- ### Windows / MacOSX

    Si eres usuario de Windows o MacOSX descargarás un ejecutable (exe o dmg respectivamente) con un asistente sencillo de instalación

- ### Linux

  - #### Descompresión de los ficheros del IDE

    Si por el contrario usas linux descargarás un tar.xz, para descomprimir los archivos podrás hacerlo haciendo doble click sobre él para abrirlo con el gestor de achivos o bien haciendo uso del terminal ejecutando dentro de la carpeta en la que se encuentre el fichero descargado el siguiente comando:

    ```bash
    $ tar -xvf arduino-1.8.13-linux64.tar.xz
    ```

  - #### Instalación del IDE

    Una vez descomprimido podremos hacer uso del archivo install.sh para efectuar la instalación, para ello, nos introducimos en la carpeta que acaba de crearse al descomprimir el fichero y ejecutamos el siguiente comando:

    ```bash
    $ sh install.sh
    ```

    Es posible que requieras premisos de administrador para que el script tenga acceso a los directorios en los que requiere copiar los archivos de la aplicación, en caso de ser así deberíamos de ejecutarlo con permisos de administrador:

    ```bash
    $ sudo sh install.sh
    ```

    Una vez instalado ya podremos abrir el IDE de Arduino y empezar a desarrollar.

