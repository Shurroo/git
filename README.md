Ansible Role: Shurroo Git
=========================

Installs `git` on macOS using Homebrew and performs basic configuration. There are no role dependencies but please read the Requirements.

Requirements
------------

* Intel Mac (x86_64) (Apple Silicon, arm64, is not yet supported)
* macOS >= 12.1 (Monterey)
* XCode Command Line Tools (CLT)
* Homebrew
* Ansible >= 2.11

Note that the role is supported for local execution **only**.

Role Variables
--------------

If you want to set the global Git user name and email, please ensure you provide these values in the playbook, for example:
```yaml
git_user_name: Groot
git_user_email: groot@galaxyguardians.org
```
If a value is omitted, any existing value on the target machine will be retained – it will not be deleted.

By default, any existing `~/.gitconfig` file will not be overwritten. To change this behaviour:
```yaml
overwrite_gitconfig: true
```

By default, any existing `~/.ssh/id_rsa` file will not be overwritten. To change this behaviour:
```yaml
overwrite_private_key: true
```

You can enable a log summary to `~/.shurroo/log/` by setting:
```yaml
write_log_file: true
```
The log file is timestamped, so you can differentiate multiple plays, for example `git-2022-0219-1817.log`. Even though a new file is created on each play, the log write does not add to the `changed` task count.

Dependencies
------------

There are no dependencies on other Ansible Galaxy roles, but you must have Homebrew installed. This role deliberately **does not** install Homebrew, and fails if Homebrew is not installed.

You can install Homebrew using the Shurroo [installer](https://github.com/Shurroo/install), or by following the Homebrew [instructions](https://brew.sh/). Note that either of these methods will install the Command Line Tools if they are needed.

Example Playbook
----------------

```yaml
- hosts: localhost
  connection: local
  roles:
    - role: Shurroo.git
  vars:
    write_log_file: true
    overwrite_gitconfig: true
    overwrite_private_key: true
    git_user_name: Groot
    git_user_email: groot@galaxyguardians.org
```

Source Files
------------

Playing the role using `shurroo play git` will automatically discover and use a custom playbook file if it exists. The playbook file must be on a mounted volume named `Shurroo`, and in a `git` folder, like this:
```shell
/Volumes/Shurroo/git/git.yml
```

Source files will be copied from a mounted volume named `Shurroo` if they exist. This method allows convenient use of a flashdrive or mounted network disk containing dotfiles, configuration files and secrets. This role will copy the following files if they are found:
```zsh
/Volumes/Shurroo/git/.gitconfig
/Volumes/Shurroo/git/.ssh/id_rsa
```
Copying a `.gitconfig` file allows you immediate access to your favourite `git` aliases (shortcut commands), settings, colours and other configuration items. For this file to be copied, one of the following must be true:
* No existing `~/.gitconfig` file
* The variable `overwrite_gitconfig`


Copying an `id_rsa` private key file allows you immediate `ssh` access to [github.com](https://github.com). You can test this after running the role using `ssh -T git@github.com`. For this file to be copied, one of the following must be true:
* No existing `~/.ssh/id_rsa` file
* The variable `overwrite_private_key`

Project Name
------------

The project was originally inspired from the [Superlumic](https://github.com/superlumic/superlumic) project by [Roderik van der Veer](https://github.com/roderik). When I started on a replacement, I searched for a name with some meaning like "launch", "fire up", "bootstrap" or similar. I eventually settled on Hindi "shurroo" (शुरू). [Google Translate](https://translate.google.com/?sl=en&tl=hi&text=begin&op=translate) tells me "shurroo" means "begin", so this works nicely. Note that the official latin spelling has only one "r", but that name was already taken on GitHub, so I added a second "r". See the parent [Shurroo](https://github.com/Shurroo/shurroo) project for more details.


License
-------

[BSD-3-Clause](https://spdx.org/licenses/BSD-3-Clause.html)

Author Information
------------------

Ian Taylor ([IanTaylorFB](https://github.com/IanTaylorFB)), Co-Founder and CTO at [FlyingBinary Ltd](https://flyingbinary.com).
