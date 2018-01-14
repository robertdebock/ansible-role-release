# Tools
Several tools to manage or use this role

# Setup
Run `ansible-galaxy install -r requirements.yml` to download all required roles.

# Releasing
When you want to create a release:
- `vagrant up` to start virtual machines.
- `ansible-playbook.yml snapshot.yml` to start container and
- Create containers
- Bootstrap
- Update
- Create a package list
- Delete containers

This basically "freezes" or "snapshots" the (package) state of an installation. This snapshot (stored in i.e. "CentOS-7") can be pasted into the role variables.

# Adding distributions
When you want to create another "offering", these files are relevant:
-  snapshot.yml to add the creation and deletion of the container.
- inventory/hosts to note the name of the containers used.
- snapshot.yml in case a new package manager is used.
- requirements.yml if you want to add functionality.

TODO:
- Docker does not run a kernel, nor grub. This means the snapshots created here can't be used on a virtual or physical machine. Probably remove the while docker case.
