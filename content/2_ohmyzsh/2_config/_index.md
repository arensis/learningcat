+++
title = "Configuración"
weight = 2
pre = "<i class='fa fa-wrench' aria-hidden='true'></i> "
+++

## Fichero de configuración

La configuración del framework se puede cambiar editando el archivo de configuración, se puede editar con un editor de texto por consola como nano:

```bash
nano ~/.zshrc
```

En este fichero hay diversas opciones para configurar, esto se puede realizar cambiando el valor de algún parámetro o descomentando un parámetro que actualmente esta deshabilitado para que tenga efecto.

Algunos de los parámetros que podemos modificar para personalizar el aspecto de la consola y ciertos comandos de utilidad son los siguientes:

#### Añadir temas

Los temas te proporcionan ayudas visuales en la consola, como el nombre de la rama en git, si hay cambios sin commitear etc..

Hay una infinidad de temas, en la documentación del framework dispones de un amplio listado con capturas de pantalla: 
  
  <i class='fab fa-github' style="font-size: 1.1em"></i> https://github.com/robbyrussell/oh-my-zsh/wiki/Themes

El tema que viene configurado por defecto es `robbyrussell`, para poder cambiarlo hay que editar el fichero de configuración hay que cambiar el valor del siguiente parámetro por el nombre del nuevo tema elegido entre comillas dobles:

```bash
ZSH_THEME="robbyrussell"
```

#### Añadir plugins

Los pluggins proporcionan ayudas en la consola, como el plugin de git, en la propia documentación del framework ya hay amplio listado de plugins disponibles:

<i class='fab fa-github' style="font-size: 1.1em"></i> https://github.com/robbyrussell/oh-my-zsh/wiki/Plugins

También puedes consultar el mismo listado en la carpeta del framework en la que están instalados:


Por defecto viene habilitado el plugin de git, sin embargo, si se quisieran añadir más plugins basta con añadirlos al listado en el archivo de configuración.

Vamos a ver un ejemplo con el plugin `chucknorris`. Para ello necesitamos instalar primero fortune, que es una aplicación que al ejecutarla muestra una frase aleatoria, y también cowsay, una aplicación que dibuja una vaca mostrando una frase en el bocadillo.

```bash
#instalación de fortune
sudo apt-get install fortune-mod

#instalación de cowsay
sudo apt-get install cowsay
```

Ahora vamos a habilitar el plugin en la configuración del framework editando el fichero y modificando el parámetro plugins añadiendo el nombre del plugin que queremos habilitar separado con  un espacio de los otros plugins del listado:

```bash
plugins=(git chucknorris)
```

Cerraremos y abriremos la consola para aplicar todos los cambios y vermos si nos ha funcionado utilizando los comandos del plugin:

```bash
#Chiste aleatorio de Chuck Norris
chuck

#Chiste aletaorio de Chuck Norris con una vaca
chuck_cow
```