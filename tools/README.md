# Tools
Several tools to manage or use this role

# Setup
Run `ansible-galaxy install -r requirements.yml` to download all required roles.

# Releasing
When you want to create a release:
- `vagrant up` to start virtual machines.
- `ansible-playbook.yml snapshot.yml` to:
- Run all roles defined.
- Create a package list

This basically "freezes" or "snapshots" the (package) state of an installation. This snapshot (stored in i.e. "CentOS-7.yml") is pasted into the role variables.

# Adding distributions
When you want to create another "offering", these files are relevant:
- Vagrantfile to add the another distribution.
- snapshot.yml in case a new package manager is used.
- requirements.yml if you want to add functionality.
