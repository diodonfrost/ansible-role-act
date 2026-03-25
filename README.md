# ansible-role-act

[![molecule](https://github.com/diodonfrost/ansible-role-act/workflows/molecule/badge.svg)](https://github.com/diodonfrost/ansible-role-act/actions)
[![Ansible Galaxy](https://img.shields.io/badge/galaxy-diodonfrost.act-660198.svg)](https://galaxy.ansible.com/diodonfrost/act)

This role provide a compliance for install act on your target host.

## Requirements

This role was developed using Ansible 2.8 Backwards compatibility is not guaranteed.
Use `ansible-galaxy install diodonfrost.act` to install the role on your system.

## Role Variables

This role has multiple variables. The defaults for all these variables are the following:

```yaml
---
# defaults file for ansible-role-act

# Define act version to install
# Possible values: https://api.github.com/repos/nektos/act/releases
# Default: latest
act_version: latest

# Define where to install act binary
# Default: use local system path defined in Ansible vars/*.yml
act_path: "{{ _act_default_path }}"
```

## Dependencies

None

## Example Playbook

This is a sample playbook file for deploying the Ansible Galaxy act role in a localhost and installing latest act version.

```yaml
---
- hosts: localhost
  become: true
  roles:
    - role: diodonfrost.act
```

This role can also install a specific version of act.

```yaml
---
- hosts: localhost
  become: true
  roles:
    - role: ansible-role-act
      vars:
        act_version: v0.2.70
```

## Local Testing

This project uses [Molecule](http://molecule.readthedocs.io/) to aid in the
development and testing.

To develop or test you'll need to have installed the following:

* Linux (e.g. [Ubuntu](http://www.ubuntu.com/))
* [Docker](https://www.docker.com/)
* [Python](https://www.python.org/) (including python-pip)
* [Ansible](https://www.ansible.com/)
* [Molecule](http://molecule.readthedocs.io/)
* [Libvirt](https://www.virtualbox.org/) (windows tests only)
* [Vagrant](https://www.vagrantup.com/downloads.html) (windows tests only)

### Testing with Docker

```shell
# Install requirements
pip install -r requirements-dev.txt

# Test ansible role with ubuntu 26.04
molecule test

# Test ansible role with debian 13
image=ansible-debian:13 molecule test

# Apply role on debian 13 instance
image=ansible-debian:13 molecule converge

# Launch tests on debian 13 instance
image=ansible-debian:13 molecule verify
```

### Testing with Vagrant and Libvirt

```shell
# Test ansible role with Windows
molecule test -s windows
```

## License

Apache 2

## Author Information

This role was created in 2019 by diodonfrost.
