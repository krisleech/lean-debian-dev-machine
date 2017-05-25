# Ultra Lean Development Machine

A simple and quick way to provision an ultra lean development machine.

Tested with:

* Ansible 2.1
* Debian 8 (Jessie)

[![Demo](https://img.youtube.com/vi/Ql4hYROBqSY/0.jpg)](https://www.youtube.com/watch?v=Ql4hYROBqSY)

## Features

- xorg + i3
- vim, git etc.

After logging in to your machine type `startx` to begin a GUI session using
i3 as the window manager.

## Configure

Edit `vars.yml` and change the `user` var:

```yaml
user: kris
```

## Usage

Install everything:

    ansible-playbook -K -v setup.yml

## Vagrant/VirtualBox

```
vagrant up --provision
```
