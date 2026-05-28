# Fedora Workstation Setup

This role tweaks a newly (or not so newly) deployed fedora workstation installation.
It will install install some editors, configs, change keyboard shortcuts in Gnome and setup 3rd party repositories.

I use my machine(s) to write GTK applications, python and go, so this role is biased towards that.

## How to use the role

To install packages most tasks require elevated rights, so it's best to run ansible with sudo.
When appropriate (e.g. changing user preferences in Gnome) the tasks will become the target user.
You can include the role like this:

```yaml
---
- name: Install workstation
  hosts: localhost
  gather_facts: true
  vars:
    enable_bibata_cursor: true
    enable_papirus_icons: true
    use_terra_repository: true
    target_user: bob
  roles:
    - fedora_workstation_setup
```

## Variables

You should define these variables in your playbook.

| Variable             | Purpose                                                           |
| ----------------------| -------------------------------------------------------------------|
| enable_bibata_cursor | Wether the bibata cursor theme should be installed and configured |
| enable_papirus_icons | wether the papirus icon theme should be installed and configured  |
| use_terra_repository | wether the Terra repository should be enabled                     |
| target_user          | for which local user these changes should be applied              |


# What will be installed

A bunch of packages will be installed.

## From Fedora Repositories

- vim
- helix
- htop
- bat
- gimp
- krita
- inkscape
- gnome-builder
- gnome-tweaks
- python3-pip
- python3-ansible-lint
- golang
- papirus-icon-theme

## Flatpaks from Flathub

- ExtensionManager
- Zen Browser
- Cambalache
- minitext
- PodmanDesktop
- AntaresSQL
- Obsidian
- Only Office

## From Terra Repository

- ghostty
- codium
- bibata-cursor-theme
- starship

## Other

- 1Password (configures its repository on install)

# Gnome Settings

## Hotkeys

Ctrl + Space: 1Password Quick Access
Super + Enter: Launch Ghostty

## Settings

- Bibata Cursor
- Papirus Icons
- Enable Middle Click Paste
  - Disabled by default in newer Gnome versions
- Change Window Button Layout to Minimize:Maximize:Close
- Enable resize-with-right-button
  - Super + Right click near a window corner or edge to resize a window 
- Calender and Time Format changes


# To Do

- add starship config
- add bashrc
- document which gnome extensions I use and their settings
- document which VS Codium extensions I use and their settings