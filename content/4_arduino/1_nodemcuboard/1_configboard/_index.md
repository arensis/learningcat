+++
title = "Configurar placa"
pre = "<i class='fa fa-wrench' aria-hidden='true'></i> "
weight = 1
+++

## Preparar IDE para poder usar la placa

Las placas NodeMCU no están dentro del listado que incorpora el IDE, por ello tendremos que añadirlo en el IDE e instalar un pluggin que nos permitirá usar el IDE de Arduino con este tipo de placas.

- ### Añadir tarjetas adicionales al IDE

    El primer paso es añádir la URL que incorpora las nuevas tarjetas de tipo ESP826 al IDE, para ello abriremos las preferencias del IDE: `Archivo > Preferencias`

    Una vez en las preferencias del IDE tendremos que incluir la siguiente URL en el apartado `Gestor de URLs Adicionales de Tarjetas`:

    <i class="fa fa-link" aria-hidden="true"></i> http://arduino.esp8266.com/stable/package_esp8266com_index.json

    Para aplicar los cambios bastará con pulsar el botón de `Ok` de la ventana de `Preferencias`

- ### Instalando el controlador para placas con ESP8266

    Una vez añadido el repositorio de placas tendremos que instalar los controladores en el gestor de placas, para ello vamos a: `Herramientas > Placa > Gestor de tarjetas`, en el buscador escribiremos ESP8266 e instalaremos el que nos aparece como ESP8266 Community

- ### Seleccionando la placa de desarrollo

    Una vez instalados los controladores de las placas ya podremos seleccionar nuestra placa: `Herramientas > Placa > ESP8266 Boards > NodeMCU 1.0 (ESP-12E Module)`

- ### Seleccionar puerto serial para la comunicación con la placa

  - #### Windows o MacOSX

    Simplemente podremos seleccionarlo yendo a: `Herramientas > Puerto > COM1 /COM7`

  - #### Linux

    Seleccionaremos el puerto que nos aparezca como USB o ACM: `Herramientas > Puerto > ttyUSB0 / ttyACM0` el número final puede variar
    Es posible que al tartar de subir el codigo a nuestra placa nos muestre un error de permisos al tratar de acceder al puerto, si fuera así necesitaríamos proporcionar permisos a nuestro usuario para poder acceder al puerto.

    - ##### Mostrar la información de los puertos disponibles

        Para mostrar la información del grupo al que pertenece el puerto que necesitamos agregar los permisos tendremos que ejecutar el siguiente comando:

        - Si nos aparecía disponible el puerto ttyUSB habría que ejecutar:

            ```bash
            $ ls -l /dev/ttyUSB*
            ```

        - Si nos aparecía disponible el puerto ttyACM habría que ejecutar:

            ```bash
            $ ls -l /dev/ttyACM*
            ```

        El comando puede devolvernos una respuesta similar a estas dos:


            $ crw-rw---- 1 root uucp 188, 0  5 apr 23.01 ttyUSB0

            $ crw-rw---- 1 root dialout 188, 0  5 apr 23.01 ttyACM0


        Con esto podremos saber al grupo al que pertence el puerto, en el primer caso sería `uucp` y en el segundo `dialout`

        Y de esta manera podremos añadir nuestro usuario al grupo con el siguiente comando:

        - Para el primer caso:

            ```bash
            $ usermod -a -G uucp nuestroUsuarioDeLinux
            ```

        - Para el segundo caso:

            ```bash
            $ usermod -a -G dialout nuestroUsuarioDeLinux
            ```

        Una vez realizado necesitaríamos reiniciar el equipo para que se apliquen los cambios en los permisos, podremos ver si tenemos nuestro usuario pertenece a ese grupo listando todos los grupos a los que pertence nuestro usuario mediante el siguiente comando:

        ```bash
        $ groups nuestroUsuarioDeLinux
        ```

        Para poder probar en el IDE que todo fue correctamente, seleccionamos el puerto al que hemos proporcionado permisos y cargamos un código de ejemplo en la placa: `Archivo > Ejemplos > Ejemplos para NodeMCU 1.0 (ESP-12E Module) > ESP8266 > Blink`

        Este ejemplo hará que el led del módulo wifi de la placa parpadee cada dos segundos. Si todo funciona correctamente ya tendríamos configurada nuestra placa con el IDE de Arduino.