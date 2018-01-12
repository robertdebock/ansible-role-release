server
=========

[![Build Status](https://travis-ci.org/robertdebock/ansible-role-server.svg?branch=master)](https://travis-ci.org/robertdebock/ansible-role-server)

Install all required packages on a server.

Requirements
------------

- A Bootstrapped system (hint: robertdebock.bootstrap)
- Access to a repository containing packages, likely on the internet.
- Ansible 2.2 or higher.

Capture all packages with:
- CentOS:
```
rpm -qa --queryformat "    - %{NAME}-%{VERSION}-%{RELEASE}\n" | grep -v gpg-pubkey | sort
```

Benefits of this approach:
- A list of changed package is visible in code.
- (Not tested) It's possible to downgrade to another "release".
- This does not depend on Satellite. The repository can be a simple mirror.

Drawbacks of this approach:
- A "snapshot" of packages and versions has to be created.

Drawbacks of both approaches:
- Changing package dependencies can result in orphaned packages.

Role Variables
--------------

None known

Dependencies
------------

- robertdebock.bootstrap

Example Playbook
----------------

```
---
- name: server
  hosts: all
  gather_facts: no
  become: yes

  roles:
    - robertdebock.server

  tasks:
    - name: install some extra software
```

To install this role:
- Install this role individually using `ansible-galaxy install robertdebock.server`
- Use another role that depends on this one and run `ansible-galaxy install --role-file requirements.yml`:

```
---
- src: robertdebock.server
```

-------

Apache License, Version 2.0

Author Information
------------------

Robert de Bock <robert@meinit.nl>
