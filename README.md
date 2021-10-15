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

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

```yaml
- hosts: localhost
  connection: local
  roles:
    - role: IanTaylorFB.git
```

License
-------

BSD

Author Information
------------------

Ian Taylor (IanTaylorFB)

FlyingBinary Ltd
