# Tools
Tools to manage or use this role

# Overview
```text
+-----+   +----+    +----------------+
| ISO | + | KS |    | Ansible roles: |
+-----+   +----+    | - bootstrap    |
    |       |       | - update       |
    +-------+       +----------------+
    |                        |
    V                        V
+========+    +------+  +=========+
| Packer | -> | VMDK |  | Ansible |
+========+    +------+  +=========+
                  |          |
                  V          V
            +=========+    +----------+
            | Vagrant | -> | instance |
            +=========+    +----------+
                             |
                             V
+------+    +=========+    +---------+
| LNXS | <- | Ansible | <- | Release |
+------+    +=========+    +---------+
```

Legend:
- Single dash (-): Input or output, typically files or arifacts.
- Double dash (=): Processes/programs.
- ISO: an ISO to install a Linux distribution with.
- KS: Kickstart file (or preseed for Ubuntu) to configure the Linux distribution with.
- Packer: A Hashicorp application to make installable artifacts with.
- Ansible roles: A playbook referring to desired roles.
- VMDK: An artifact that Packer creates. Can be used to start instances with.
- Ansible: The program to modify instances with.
- Vagrant: A Hashicorp applicatsion to manage (start) instances.
- instance: A running instance, based on the VMDK, modified by Ansible roles.
- Release: A list of packages found on "instance".
- LNXS: Linux boxes where packages are matched to "Release".

# Defining a release
1. List all roles and tasks that define your release in snapshot.yml.
2. Add all required roles to requirements.yml.
3. Run `ansible-galaxy install -r requirements.yml` to download all required roles.

# Releasing
When you want to create a release:
- `vagrant up` to start virtual machines.
- `ansible-playbook snapshot.yml` to:
- Run all roles defined.
- Create a package list

This basically "freezes" or "snapshots" the (package) state of an installation. This snapshot (stored in i.e. "CentOS-7.yml") is pasted into the role variables.

# Adding distributions
When you want to create another "offering", these files are relevant:
- Vagrantfile to add the another distribution.
- snapshot.yml in case a new package manager is used.
