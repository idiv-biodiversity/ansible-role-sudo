Ansible Role: sudo
==================

An Ansible role that configures sudo / sudoers.

Table of Contents
-----------------

<!-- toc -->

- [Requirements](#requirements)
- [Role Variables](#role-variables)
- [Dependencies](#dependencies)
- [Example Playbook](#example-playbook)
  * [Top-Level Playbook](#top-level-playbook)
  * [Role Dependency](#role-dependency)
- [License](#license)

<!-- tocstop -->

Requirements
------------

- Ansible 2.9

Role Variables
--------------

```yml
sudo_sudoers:
  - name: alice
  - name: bob

# disable wheel in /etc/sudoers if distro does so by default
sudo_disable_wheel: no
```

Dependencies
------------

```yml
---

# requirements.yml

roles:

  - name: idiv_biodiversity.sudo
    src: https://github.com/idiv-biodiversity/ansible-role-sudo
    version: vX.Y.Z

...
```

Example Playbook
----------------

### Top-Level Playbook

Write a top-level playbook:

```yml
---

- name: server
  hosts: group

  roles:
    - role: idiv_biodiversity.sudo
      tags:
        - sudo

...
```

### Role Dependency

Define the role dependency in `meta/main.yml`:

```yml
---

dependencies:

  - role: idiv_biodiversity.sudo
    tags:
      - sudo

...
```

License
-------

MIT
