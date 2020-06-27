+++
title = "Configurar accesso ssh"
weight = 2
pre = "<i class='fa fa-wrench' aria-hidden='true'></i>&nbsp;"
+++

Para que podamos realizar modificaciones sobre un repositorio en el que se nos han otorgado permisos podremos hacerlo de dos maneras, o por usuario y contraseña (teniendo que introducir el usuario y contraseña cada vez que queramos subir algún cambio), o bien por ssh.

Para realizarlo mediante ssh necesitaríamos una clave pública en nuestro equipo, ya sea alguna que ya tuviéramos anteriormente o crear una específica.

## Comprobar si existen claves ssh ya creadas

Para comprobarlo tendremos que listar los ficheros que se encuentran en el directorio `~/.ssh` con el siguiente comando:

  ```bash
  ls -al ~/.ssh
  ```

Si ya hubiera alguna clave creada aparecería un listado de archivos, del listado de claves necesitraíamos las que son públicas y normalente los ficheros suelen tener un nombre similar a los siguientes:

- id_dsa.pub
- id_ecdsa.pub
- id_ed25519.pub
- id_rsa.pub

Si no apareciera ningún fichero con la extensión *.pub tendríamos que crear una clave pública nueva.

## Crear una clave ssh para conectar con github/gitlab

- ### Crear clave ssh

    Para crear la clave ssh, para ello introduciremos el comando a continuación substituyendo el e-mail de ejemplo por el e-mail con el que nos hayamos registrado en gihub/gitlab

     ```bash
     ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
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
  
- ### Añadir clave ssh al ssh-agent

    Una vez que tenemos creada la clave ssh, tendremos que añadir la clave que queremos utilizar al ssh-agen. Para ello primeramente lo iniciaremos en segundo plano con el siguiente comando:

    ```bash
    eval "$(ssh-agent -s)"
    ```

    Una vez arrancado en segundo plano añadiremos nuestra clave ssh privada al ssh-agent. Si has creado tu clave con un nombre diferente, o si estás añadiendo una clave ya existente con un nombre diferente, reemplaza id_rsa en el comando por el nombre de tu clave privada.

    ```bash
    ssh-add ~/.ssh/id_rsa
    ```

- ### Copiar clave pública en el portapapeles

    El último paso sería copiar el contenido del fichero de la clave pública para añadirla en Github/Gitlab en la configruación del perfil de usuario, dentro del apartado SSH. El copiar el contenido lo podríamos efectuar de diversas maneras:

    - Abriendo el fichero con un editor de texto y copiando el contenido

    - Mostrando el contenido del archivo por consola mediante el comando cat y copiando el resultado:

      ```bash
      cat ~/.ssh/id_rsa.pub
      ```

    - Con alguna herramienta como por ejemplo xclip:
      - Instalación de xclip:

        ```bash
        sudo apt-get install xclip
        ```

      - Copiar la clave pública con xclip
  
            En caso de que nuestra clave pública tenga un nombre diferente tendremos que substituirlo en el comando.

            ```bash
            xclip -sel clip < ~/.ssh/id_rsa.pub
            ```
