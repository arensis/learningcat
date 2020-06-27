+++
title = "Variables"
weight = 2
pre = "<i class='fa fa-file-code' aria-hidden='true'></i> "
+++

## Variables en Python

- **Sintaxis**

  - Los nombres de las variables en python tienen que empezar por una letra o bien un guión bajo.
  - Los nombres de las variables son case sensitive por tanto una variable con nombre Numero es diferente a una variable con nombre numero
  - Como convención en programación los nombres de métodos o variables suelen escribirse con el tipo de escritura camel case, la primera letara de cada palabra que conforme el nombre de la variable empezará con mayúscula (y por norma general la primera letra del nombre de la variable será en minúscula).
  
    - Ejemplo:

       `variablePrimaria`

       `nombreDePila`

- **Asignación de valor**

  Para que una variable exista hay que asignarle un valor. Este valor puede ser nulo, o bien tener un valor de un tipo de dato determinado.
  Esta asignación se puede realizar de manera individual o múltiple

  - Asignación individual

    ```python
    variable = 1
    ```

  - Asignación múltiple

    ```python
    #Asignación de valores diferentes a diferentes variables
    variable1, variable2, variable3 = 1, 2.1, "Texto"

    #Asignación del mismo valor a múltiples variables
    variable1 = variable2 = variable3 = True
    ```

- **Alcance**

  - Las variables en Python son locales por defecto, es decir, las variables definidas en el bloque de código de una función sólo tienen existencia dentro de la misma. Además, las variables existentes fuera de una función no son visibles dentro de la misma.

- **Tipo de variable:** *Globales*

  - Si fuera necesario, se puede convertir una variable local en global, para poder indicar en una función que vamos a utilizar una variable global tenemos que declararla explícitamente con la sentencia `global` dentro de la función.

    - Ejemplo:

      ```python
      variable_global = True

      def start():
      global variable_global
      print "El valor de variable_global es:", variable_global
      variable_global = not variable_global
      print "Ahora el valor de variable_global es:", variable_global
      ```

- **Tipo de variable:** *Constantes*

  - Las constantes son colocadas dentro de módulos Python que no pueden ser cambiados.
  - Por convención los nombre de las constantes se suelen expresar en mayúsculas y cada palabra separada por un guión bajo.

    - Ejemplo:

      `CAMEL_CASE`

      `VARIABLE_1`

- **Tipos de dato**
  - Ejemplo:

      ```python
      valorNulo = None
      numeroEnteroInt = 1
      cadena = "Hola"
      flotante = 1.2
      booleano = True
      numeroEnteroLong = 1L
      numeroComplejo = 3.14j
      numeroComplejo = 2.1 + 7.8j
      ```