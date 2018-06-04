release
=========

[![Build Status](https://travis-ci.org/robertdebock/ansible-role-release.svg?branch=master)](https://travis-ci.org/robertdebock/ansible-role-release)

Install or update all required packages on a server.

Context
--------
This role is a part of many compatible roles. Have a look at [the documentation of these roles](https://robertdebock.nl/) for further information.

Here is an overview of related roles:
![dependencies](https://raw.githubusercontent.com/robertdebock/robertdebock.github.io/artifacts/release.png "Dependency")

Requirements
------------

- A Bootstrapped system (hint: robertdebock.bootstrap)
- A way to update a system (hint: robertdebock.update)
- Access to a repository containing packages, likely on the internet.
- Ansible 2.2 or higher.

Benefits of this approach:
- A list of changed package is visible in code.
- This does not depend on Satellite. The repository can be a simple mirror.

Drawbacks of this approach:
- A "snapshot" of packages and versions has to be created.
- Not listed packages are not managed/updated.

Drawbacks of both approaches:
- Changing package dependencies can result in orphaned packages.
- (Not tested) It's possible to downgrade to another "release".

Role Variables
--------------

None known

Dependencies
------------

- [robertdebock.bootstrap](https://travis-ci.org/robertdebock/ansible-role-bootstrap)
- [robertdebock.update](https://travis-ci.org/robertdebock/ansible-role-update)

Example Playbook
----------------

```
---
- name: server
  hosts: all
  gather_facts: no
  become: yes

  roles:
    - robertdebock.release

  tasks:
    - name: install some extra software
```

To install this role:
- Install this role individually using `ansible-galaxy install robertdebock.release`
- Use another role that depends on this one and run `ansible-galaxy install --role-file requirements.yml`:

```
---
- src: robertdebock.release
```

-------

Apache License, Version 2.0

Author Information
------------------

Robert de Bock](https://robertdebock.nl/) <robert@meinit.nl>
