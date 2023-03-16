---
layout:     post
title:      "Configure Vim on Mac/Linux"
author:     "Cooper"
header-img: "img/post-bg-2015.jpg"
catalog: true
typora-root-url: ../
tags:
    - Mac
    - CS
    - Vim
---

# Vim - the ubiquitous text editor

[Vim](https://www.vim.org/) is a configurable text editor built to make  creating and changing any kind of text very efficient. It is included as `vi`  with most `UNIX` systems and with `MacOS`.

# Installation

To install the latest `Vim` version, use `homebrew`:

```
brew install vim
```

# SpaceVim

[SpaceVim](https://github.com/SpaceVim/SpaceVim) is a `vim` configuration inspired by `spacemacs`, it is compatible with `vim` and `neovim`.

## Install SpaceVim

```
curl -sLf https://spacevim.org/install.sh | bash
```

Then all plugins will be downloaded automatically by running `vim`.

## Configuration

The default configuration file of `SpaceVim` is `~/.SpaceVim.d/init.toml`.

### Use Vim as a Python IDE

For full tutorial, please see [here](https://spacevim.org/use-vim-as-a-python-ide/). Alternatively, you can configure `Vim` as a `C/C++` IDE.

#### Enable language layer

The python language support in SpaceVim is provided by `lang#python` layer, and it is not enabled by default. You need to enable it in SpaceVim configuration file. Press `SPC f v d` to open the SpaceVim configuration file, and add following snippet to your configuration file.

```
[[layers]]
  name = "lang#python"
```

#### Select a Python interpreter

Python is an interpreted language, and in order to run Python code and get semantic information, you need to tell SpaceVim which interpreter to use. This can be set with `python_interpreter` layer option. For example:

```
[[layers]]
  name = 'lang#python'
  python_interpreter = 'D:\scoop\shims\python.exe'
```

# Uninstallation

