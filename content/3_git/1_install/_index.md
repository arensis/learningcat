+++
title = "Instalar y configurar"
weight = 1
pre = "<i class='fa fa-folder-open' aria-hidden='true'></i> "
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

    #### Configurar el nombre

     ```bash
     git config --global user.name "John Doe"
     ```

    #### Configurar el e-mail

     ```bash
     git config --global user.email johndoe@example.com
     ```

- ### Editor de texto por defecto

    También podemos configurar el editor que se abrirá cuando git requiera de editar o añadir algún mensaje. Por defecto, el editor de texto que git usará si no se ha configurado ninguno es el editor de texto por defecto del sistema.

    #### Configurar editor de texto

     ```bash
     git config --global core.editor emacs
     ```
