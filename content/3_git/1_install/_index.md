+++
title = "Instalar y configurar"
weight = 1
+++

## Instalar Git

```bash
sudo apt install git-all
```

## Comprobar la versión de Git instalada

```bash
git --version
```

## Configuración

- ### Mostrar la configuración actual

  ```bash
  git config --list
  ```

- ### Identidad

  Una vez realizada la instalación, hay que configurar la identidad. La identidad consta de un nombre y un e-mail, esta información servirá para identificar quién ha sido el autor de una acción realizada con git (commit, merge, revert...).

  Para poder utilizar git es necesario añadir esta información, de lo contrario no nos dejará realizar acciones de escritura.

  - **Configurar el nombre**

     ```bash
     git config --global user.name "John Doe"
     ```

  - **Configurar el e-mail**

     ```bash
     git config --global user.email johndoe@example.com
     ```

- ### Editor de texto por defecto

  También podemos configurar el editor que se abrirá cuando git requiera de editar o añadir algún mensaje. Por defecto, el editor de texto que git usará si no se ha configurado ninguno es el editor de texto por defecto del sistema.

  - **Configurar editor de texto**

     ```bash
     git config --global core.editor emacs
     ```

## Configuración para github/gitlab para conectar por ssh

Para que podamos realizar acciones (commits, merge, reverts...) sobre un repositorio en el que se nos han otorgado permisos podremos hacerlo de dos maneras, o por usuario y contraseña (teniendo que introducir el usuario y contraseña cada vez que queramos ejecutar una acción sobre él), o bien por ssh. Al hacerlo por ssh cada vez que queramos ejecutar una acción leerá nuestra clave ssh para darnos acceso de manera automática.

Para ello primero tenemos que tener una clave ssh pública en nuestro equipo, para comprobarlo tendremos que listar los ficheros que se encuentran en el directorio `~/.ssh` con el siguiente comando:

- ### Comprobar si existen claves ssh ya creadas

  ```bash
  ls -al ~/.ssh
  ```

  Si ya hubiera alguna clave creada aparecería un listado de archivos, normalente los ficheros suelen tener un nombre similar a los siguientes:

   - id_dsa.pub
   - id_ecdsa.pub
   - id_ed25519.pub
   - id_rsa.pub

   Si no apareciera ningún fichero tendremos que crear una clave pública.

- ### Crear una clave ssh para conectar con github/gitlab
  
  - **Crear clave ssh**

    Para crear la clave ssh, para ello introduciremos el comando a continuación substituyendo el e-mail de ejemplo por el e-mail con el que nos hayamos registrado en gihub/gitlab

    ```bash
    ssh-keygen -t rsa -b 4096 -C "your_email@example.com
    ```

    Al ejecutarlo nos aparecerán 3 preguntas:

    - La primera de ellas nos dará la opción de poner un nombre a nuestra clave ssh, podemos dejarlo en blanco y presionar enter para que tome un nombre por defecto o poner uno a nuestra elección. La clave se guardará en la ruta indicada.

      ```bash
      > Enter a file in which to save the key (/home/you/.ssh/id_rsa): 
      ```

    - La segunda y tercera pregunta nos dará la opción de configurar una contraseña para nuestra clave ssh. Esto servirá para que cada vez que se vaya a usar nuestra clave ssh nos salga un mensaje de aviso para poder poner esa contraseña que hemos configurado.

      Puede que quizá no queramos que se nos esté pidiendo ninguna contraseña cada vez que tengamos que hacer uso de la clave ssh, para ello simplemente dejándolo en blanco y presionando enter en ambos casos será suficiente.

      ```bash
      > Enter passphrase (empty for no passphrase): [Type a passphrase]
      > Enter same passphrase again: [Type passphrase again]
      ```
  
  - **Añadir clave ssh al ssh-agent**

    Una vez que tenemos creada la clave ssh, tendremos que añadir la clave que queremos utilizar al ssh-agen. Para ello primeramente lo iniciaremos en segundo plano con el siguiente comando:

    ```bash
    eval "$(ssh-agent -s)"
    ```

    Una vez arrancado en segundo plano añadiremos nuestra clave ssh privada al ssh-agent. Si has creado tu clave con un nombre diferente, o si estás añadiendo una clave ya existente con un nombre diferente, reemplaza id_rsa en el comando por el nombre de tu clave privada.

    Add your SSH private key to the ssh-agent. If you created your key with a different name, or if you are adding an existing key that has a different name, replace id_rsa in the command with the name of your private key file.

    ```bash
    ssh-add ~/.ssh/id_rsa
    ```

    Una vez hecho esto ya podremos proceder a añadirla en github/gitlab en la configuración del perfil de usuario, en el apartado SSH. Para ello tendremos que copiar la clave ssh que hemos creado para incluirla en nuestro listado de claves ssh de github/gitlab.

  - **Copiar clave pública en el portapapeles**

    Para copiar la clave pública podremos hacerlo abriendo el fichero en un editor de textos y copiándola o mediante la herramienta xclip:

    - Instalación de xclip:

      ```bash
      sudo apt-get install xclip
      ```

    - Copiar la clave pública con xclip

      En caso de que nuestra clave pública tenga un nombre diferente tendremos que substituirlo en el comando.

      ```bash
      xclip -sel clip < ~/.ssh/id_rsa.pub
      ```