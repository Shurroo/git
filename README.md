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

The global Git user name and email may be set by including these values in the playbook, for example
```yaml
git_user_name: Groot
git_user_email: groot@galaxyguardians.org
```
If either or both the values are omitted, no action will be taken.

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
      git_user_name: Groot
      git_user_email: groot@galaxyguardians.org
```

Source Files
------------

Source files will be copied from a mounted volume named `Shuroo` if they exist. This method allows convenient use of a flashdrive or mounted network disk containing dotfiles, configuration files and secrets. This role will copy the following files if they are found:
```zsh
/Volumes/Shuroo/.gitconfig
```

Project Name
------------

The project was originally inspired by [Roderik van der Veer](https://github.com/roderik)'s [Superlumic](https://github.com/superlumic/superlumic) project. When I started on a replacement, I searched for a name with some meaning like "launch", "fire up", "bootstrap" or similar. I eventually settled on Hindi "shuroo" (शुरू). [Google Translate](https://translate.google.com/?sl=en&tl=hi&text=begin&op=translate) tells me "shuroo" means "begin", so this works nicely.


License
-------

BSD

Author Information
------------------

Ian Taylor ([IanTaylorFB](https://github.com/IanTaylorFB)), Co-Founder and CTO at [FlyingBinary Ltd](https://flyingbinary.com).
