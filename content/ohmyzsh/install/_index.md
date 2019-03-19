+++
title = "Instalación de ZSH y OhMyZsh!"
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

### Enlaces de interés

- [Web OhMyZsh!](https://ohmyz.sh/)