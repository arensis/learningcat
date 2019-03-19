+++
title = "Instalar y ejecutar"
+++

## Instalar Python

```bash
sudo apt-get update
sudo apt-get install python3.6
```

## Comprobar versión de Python instalada 

```bash
python3.6 -V
```

>*En este caso la versión base que instalamos es la 3.6, por ello el comando para ejecutar será **python3.6**, pero dentro de la 3.6 tiene versiones, por defecto se instala la última versión estable disponible*

## Ejecutar un fichero Python en un terminal

Los ficheros python tienen extensión `*.py` para ejecutar la aplicación que contiene tendrá que hacerse con el comando `python3.6` seguido del fichero. (Tendrá que ejecutarse en la ruta donde se encuentre el fichero)

```bash
python3.6 Ejemplo.py
```

## Consola de Python

En el terminal podemos ejecutar una consola de python para poder hacer pruebas con código directamente.

- **Abrir** la consola de python en un terminal:

  ```bash
  python3.6
  ```

- **Ejecutar comando** de ejemplo en consola

  ```python
  println("Hola mundo")
  ```

- **Salir o cerrar** la consola de python

  ```python
  exit()
  ```