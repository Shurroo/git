Ansible Role: Homebrew Git
==========================

Installs `git` on macOS using Homebrew and performs basic configuration. No depencies.

Requirements
------------

* Ansible >= 2.11
* macOS
* Homebrew

Role Variables
--------------

The global Git user name and email may be set by including these values in the playbook, for example:
```yaml
git_user_name: Groot
git_user_email: groot@galaxyguardians.org
```
If a value is omitted, any existing value on the target machine will be retained – it will not be deleted.

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
/Volumes/Shuroo/.ssh/id_rsa
```
Copying a `.gitconfig` file allows you immediate access to your favourite `git` aliases (shortcut commands), settings, colours and other configuration items.

Copying an `id_rsa` private key file allows you immediate `ssh` access to [github.com](https://github.com). You can test this after running the role using `ssh -T git@github.com`.

Project Name
------------

The project was originally inspired from the [Superlumic](https://github.com/superlumic/superlumic) project by [Roderik van der Veer](https://github.com/roderik). When I started on a replacement, I searched for a name with some meaning like "launch", "fire up", "bootstrap" or similar. I eventually settled on Hindi "shuroo" (शुरू). [Google Translate](https://translate.google.com/?sl=en&tl=hi&text=begin&op=translate) tells me "shuroo" means "begin", so this works nicely.


License
-------

BSD

Author Information
------------------

Ian Taylor ([IanTaylorFB](https://github.com/IanTaylorFB)), Co-Founder and CTO at [FlyingBinary Ltd](https://flyingbinary.com).
