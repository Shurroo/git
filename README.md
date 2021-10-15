Ansible Role: Git
=================

Installs git on macOS using Homebrew and performs basic configuration.

Requirements
------------

* Ansible >= 2.1
* macOS
* Homebrew

Role Variables
--------------

A description of the settable variables for this role should go here, including any variables that are in defaults/main.yml, vars/main.yml, and any variables that can/should be set via parameters to the role. Any variables that are read from other roles and/or the global scope (ie. hostvars, group vars, etc.) should be mentioned here as well.

Dependencies
------------

There are no dependencies on other Ansible Galaxy roles, but you must have Homebrew installed. This role deliberately **does not** install Homebrew, and fails if Homebrew is not installed.

You can install Homebrew by following their [instructions](https://brew.sh/).

Example Playbook
----------------

```yaml
- hosts: localhost
  connection: local
  roles:
    - role: IanTaylorFB.git
```

Source Files
------------

Source files will be copied from a mounted volume named `Shuroo` if they exist. This method allows convenient use of a flashdrive or mounted network disk containing dotfiles, configuration files and secrets. This role will copy the following files if they are found:
```zsh
/Volumes/Shuroo/.gitconfig
```

License
-------

BSD

Author Information
------------------

Ian Taylor (IanTaylorFB)

FlyingBinary Ltd
