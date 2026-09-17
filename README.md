# Fedora Linux Configuration Guide

# Table of contents

- [Introduction](#introduction)
- [General](#general)
  - [Nerd Fonts](#nerd-fonts) 
  - [kitty](#kitty)
  - [Yazi](#yazi)
  - [KeePassXC](#keepassxc)
  - [cmus](#cmus)
  - [yt-dlp](#yt-dlp)
  - [qBittorrent](#qbittorrent)
  - [Easy Effects](#easy-effects)
  - [LibreOffice](#libreoffice)
  - [GIMP](#gimp)
  - [Kdenlive](#kdenlive)
  - [OpenRGB](#openrgb)
  - [Discord](#discord)
  - [Waterfox](#waterfox)
- [Shell](#shell)
  - [bash](#bash)
  - [fish](#fish)
  - [Zsh](#zsh)
    - [Zsh aliases](#zsh-aliases)
- [Information](#information)
  - [htop](#htop)
  - [btop](#btop)
  - [fastfetch](#fastfetch)
  - [fetch](#fetch)
- [Coding](#coding)
  - [G++](#g)
  - [GFortran](#gfortran)
  - [Python](#python)
  - [TeX Live](#tex-live)
- [Editor](#editor)
  - [Vim](#vim)
  - [Neovim](#neovim)
  - [VSCodium](#vscodium)
    - [VSCodium extensions](#vscodium-extensions)
- [Science](#science)
  - [Avogadro](#avogadro)
- [Gaming](#gaming)
  - [Steam](#steam)
  - [additional](#additional)
- [Keyboard shortcuts](#keyboard-shortcuts)
  - [Discord hotkey](#discord-hotkey)
  - [Easy Effects hotkey](#easy-effects-hotkey)
  - [Firefox hotkey](#firefox-hotkey)
  - [Steam hotkey](#steam-hotkey)
  - [kitty hotkey](#kitty-hotkey)
  - [KeePassXC hotkey](#keepassxc-hotkey)
- [GRUB](#grub)

<br>

# Introduction

Default:
- BTRFS
- LUKS
- KDE

<br>

# General

Update all installed software packages to their latest versions

```bash
sudo dnf upgrade --refresh
```

<br>

Fonts installation

```bash
sudo dnf install fira-code-fonts
```
```bash
sudo dnf install ibm-plex-mono-fonts
```
```bash
sudo dnf install jetbrains-mono-fonts
```

<br>

## Nerd Fonts

Download the Nerd Fonts archives

```bash
curl -L https://github.com/ryanoasis/nerd-fonts/releases/latest/download/FiraCode.tar.xz -o /tmp/FiraCode.tar.xz
```
```bash
curl -L https://github.com/ryanoasis/nerd-fonts/releases/latest/download/IBMPlexMono.tar.xz -o /tmp/IBMPlexMono.tar.xz
```
```bash
curl -L https://github.com/ryanoasis/nerd-fonts/releases/latest/download/JetBrainsMono.tar.xz -o /tmp/JetBrainsMono.tar.xz
```

<br>

Create font directories

```bash
mkdir -p ~/.local/share/fonts/FiraCode
```
```bash
mkdir -p ~/.local/share/fonts/IBMPlexMono
```
```bash
mkdir -p ~/.local/share/fonts/JetBrainsMono
```

<br>

Extract archives to directories

```bash
tar -xJf /tmp/FiraCode.tar.xz -C ~/.local/share/fonts/FiraCode
```
```bash
tar -xJf /tmp/IBMPlexMono.tar.xz -C ~/.local/share/fonts/IBMPlexMono
```
```bash
tar -xJf /tmp/JetBrainsMono.tar.xz -C ~/.local/share/fonts/JetBrainsMono
```

<br>

Rebuild the system font cache

```bash
fc-cache -fv
```

<br>

## kitty

```bash
sudo dnf install kitty
```

<br>

## Yazi

```bash
sudo dnf copr enable lihaohong/yazi
```
```bash
sudo dnf install yazi
```

<br>

## KeePassXC

```bash
sudo dnf install keepassxc
```

<br>

## cmus

```bash
sudo dnf install cmus
```

<br>

## yt-dlp

```bash
sudo dnf install yt-dlp
```

<br>

## qBittorrent

```bash
sudo dnf install qbittorrent
```

<br>

## Easy Effects

```bash
sudo dnf install easyeffects
```

<br>

## LibreOffice

```bash
sudo dnf install libreoffice
```

<br>

## GIMP

```bash
sudo dnf install gimp
```

<br>

## Kdenlive

```bash
sudo dnf install kdenlive
```

<br>

## OpenRGB

```bash
sudo dnf install openrgb
```

<br>

## Discord

Add Flathub remote repository to Flatpak

```bash
flatpak remote-add --if-not-exists flathub https://dl.flathub.org/repo/flathub.flatpakrepo
```

<br>

Install the Discord app from the Flathub repository using Flatpak

```bash
flatpak install flathub com.discordapp.Discord
```

<br>

## Waterfox

```bash
sudo dnf config-manager addrepo --from-repofile=https://download.opensuse.org/repositories/isv:/BrowserWorks/Fedora_44/isv:BrowserWorks.repo
```
```bash
sudo dnf install waterfox
```

<br>

# Shell

## bash

File path *~/.bashrc*

<br>

Edit the *.bashrc* configuration file

```bash
nvim ~/.bashrc
```

<br>

Clear alias

```bash
alias c="clear"
```

<br>

Neovim alias

```bash
alias v="nvim"
```

<br>

Reload the *.bashrc* configuration file in the current session

```bash
source ~/.bashrc
```

<br>

## fish

```bash
sudo dnf install fish
```

<br>

File path *~/.config/fish/config.fish/*

<br>

Edit the *config.fish* configuration file

```bash
nvim ~/.config/fish/config.fish
```

<br>

Clear abbr

```bash
abbr --add c 'clear'
```

<br>

Neovim abbr

```bash
abbr --add v 'nvim'
```

<br>

Reload the *config.fish* configuration file in the current session

```bash
source ~/.config/fish/config.fish
```

<br>

## Zsh

```bash
sudo dnf install zsh
```

<br>

Change the current user's default shell

```bash
chsh -s $(which zsh)
```

<br>

Install Oh My Zsh

```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

<br>

Install the zsh-autosuggestions plugin

```bash
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
```


<br>

Install the fzf-tab plugin

```bash
git clone https://github.com/Aloxaf/fzf-tab ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/fzf-tab
```

<br>

Install the fast-syntax-highlighting plugin

```bash
git clone https://github.com/zdharma-continuum/fast-syntax-highlighting.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/plugins/fast-syntax-highlighting
```

<br>

File path *~/.zshrc*

<br>

Edit the *.zshrc* configuration file

```bash
nvim ~/.zshrc
```

<br>

Change prompt theme

```bash
ZSH_THEME="ys"
```

<br>

Set plugins

```bash
plugins=(... zsh-autosuggestions fzf-tab fast-syntax-highlighting)
```

<br>

Reload the *.zshrc* configuration file in the current session

```bash
source ~/.zshrc
```

<br>

### Zsh aliases

File path *~/.zshrc*

<br>

Edit the *.zshrc* configuration file

```bash
nvim ~/.zshrc
```

<br>

Clear alias

```bash
alias c='clear'
```

<br>

Neovim alias

```bash
alias v='nvim'
```

<br>

Reload the *.zshrc* configuration file in the current session

```bash
source ~/.zshrc
```

<br>

# Information

## htop

```bash
sudo dnf install htop
```

<br>

## btop

```bash
sudo dnf install btop
```

<br>

## fastfetch

```bash
sudo dnf install fastfetch
```

<br>

## fetch

```bash
sudo dnf copr enable realorangekun/fetch
```
```bash
sudo dnf install fetch
```

<br>

# Coding

## G++

```bash
sudo dnf install gcc-c++
```

<br>

## GFortran

```bash
sudo dnf install gcc-gfortran
```

<br>

## Python

```bash
sudo dnf install ... ... ... ... ... ... ... ... ... ...
```

<br>

## TeX Live

```bash
sudo dnf install texlive-scheme-full
```

<br>

# Editor

## Vim

```bash
sudo dnf install vim
```

<br>

## Neovim

```bash
sudo dnf install neovim
```

<br>

## VSCodium

```bash
sudo tee -a /etc/yum.repos.d/vscodium.repo << 'EOF'
[gitlab.com_paulcarroty_vscodium_repo]
name=gitlab.com_paulcarroty_vscodium_repo
baseurl=https://paulcarroty.gitlab.io/vscodium-deb-rpm-repo/rpms/
enabled=1
gpgcheck=1
repo_gpgcheck=1
gpgkey=https://gitlab.com/paulcarroty/vscodium-deb-rpm-repo/raw/master/pub.gpg
metadata_expire=1h
EOF
```
```bash
sudo dnf install codium
```

<br>

### VSCodium extensions

- LaTeX Workshop

<br>

# Science

## Avogadro

```bash
sudo dnf install avogadro
```

<br>

# Gaming

## Steam

Add RPM Fusion Free and RPM Fusion Nonfree repositories to the Fedora system by installing their setup packages <br>
https://docs.fedoraproject.org/en-US/gaming/proton/

```bash
sudo dnf install https://mirrors.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm https://mirrors.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm -y
```

<br>

Enable the fedora-cisco-openh264 repository in the DNF package manager configuration <br>
https://docs.fedoraproject.org/en-US/gaming/proton/

```bash
sudo dnf config-manager setopt fedora-cisco-openh264.enabled=1
```

<br>

Steam installation

```bash
sudo dnf install steam
```

<br>

multimedia package group installation

```bash
sudo dnf group install multimedia
```

<br>

sound-and-video package group installation

```bash
sudo dnf group install sound-and-video
```

<br>

GameMode package installation

```bash
sudo dnf install gamemode
```

<br>

## additional

<br>

# Keyboard shortcuts

## Discord hotkey

```
Ctrl + Alt + D
```

<br>

## Easy Effects hotkey

```
Ctrl + Alt + E
```

<br>

## Firefox hotkey

```
Ctrl + Alt + F
```

<br>

## Steam hotkey

```
Ctrl + Alt + S
```

<br>

## kitty hotkey

```
Ctrl + Alt + T
```

<br>

## KeePassXC hotkey

```
Ctrl + Alt + Q
```

<br>

# GRUB

File path */etc/default/grub*

<br>

Edit the *grub* configuration file

```bash
sudo nvim /etc/default/grub
```

<br>

Set GRUB timeout

```bash
GRUB_TIMEOUT=10
```

<br>

Generate a new GRUB bootloader configuration file

```bash
sudo grub2-mkconfig -o /boot/grub2/grub.cfg
```

<br>

Display GRUB environment variables

```bash
sudo grub2-editenv list
```

<br>

Remove the *menu_auto_hide* variable from the GRUB environment block

```bash
sudo grub2-editenv - unset menu_auto_hide
```
