# Fedora Workstation Setup

This role tweaks a newly (or not so newly) deployed fedora workstation installation.  
It will install install some editors, configs, change keyboard shortcuts in Gnome and setup 3rd party repositories.  

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


