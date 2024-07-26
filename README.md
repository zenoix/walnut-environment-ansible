# Walnut Environment (WIP)

This repository contains my Ansible setup to automate the installation and configuration of my development environment in Ubuntu and Arch distributions. 

This repo is heavily influenced and some parts were taken and modified from [TechDufus's dotfiles repo](https://github.com/TechDufus/dotfiles/tree/main). 

## Arch Usage

### Prerequisites
There are a few prerequisites needed. These are:
- git
- ansible-core
- python-watchdog

These can be installed using pacman:
```bash
pacman -S git ansible-core python-watchdog
```

You will need to clone this repository somewhere and install the ansible requirements:

```bash
git clone https://github.com/zenoix/walnut-environment.git
cd walnut-environment
ansible-galaxy install -r requirements.yml
```

You are now ready to set up the environment.
### Usage
> [!NOTE]
> Read through [Customizing the Execution](#Customizing-the-Execution) if you want to choose what gets installed.

> [!CAUTION]
Depending on what is installed, this playbook will override your pre-existing configurations, especially by my [dotfiles](https://github.com/zenoix/dotfiles).

To run the ansible playbook, all you need to do is run:
```bash
ansible-playbook main.yaml
```

and then restart your machine.

> [!NOTE]
> If you are not running it as root, you will need to use the `--ask-become-pass` flag which will prompt you for your root/sudo password. This is needed to install and configure things.

### Customizing the Execution
> [!TIP]
> You can choose what to install and configure by checking out the `group_vars/all.yaml` file.

Either comment out the ones you don't want to install, or use `--tags`/`-t` to only run specific tags, or use the `--skip-tags` to run everything except those specified.

### Post-Execution
After running the playbook, you may have to do extra things to completely set up the environment based on what roles were run.

#### Tmux
Tmux's tmux plugin manager will need to install the plugins. To do this, use `<prefix>I`. In my configuration, `Ctrl` + `Space` is my prefix.

