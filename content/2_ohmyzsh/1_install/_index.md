+++
title = "Instalación de ZSH y OhMyZsh!"
weight = 1
pre = "<i class='fa fa-folder-open' aria-hidden='true'></i> "
+++

## Instalación de la consola zsh

```bash
sudo apt install zsh
```

Comprueba si está correctamente instalada:

```bash
zsh --version
```

Cambia la consola por defecto del terminal a zsh:

```bash
chsh -s $(which zsh)
```

Para que se apliquen los cambios tendrás que cerrar sesión y volver a iniciar sesión


## Instalación de OhMyZsh

```bash
sudo apt-get install git-core
```

```bash
sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
```