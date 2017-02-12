# Ansible Role: Upgrade
[![Build Status](https://travis-ci.org/Furdarius/ansible-upgrade.svg?branch=master)](https://travis-ci.org/Furdarius/ansible-upgrade)

Upgrade software on remote machine.
Can reboot machine after upgrade if required.

Allowed types of upgrade:

* `safe` - performs an `aptitude safe-upgrade`
    * Upgrades currently installed packages 
    * Can install new packages to resolve new dependencies
    * Never removes packages
* `full` - performs an `aptitude full-upgrade`
    * Upgrades currently installed packages 
    * Can install new packages to resolve new dependencies
    * Remove currently installed packages
        if this is needed to upgrade the system as a whole
* `dist` - performs an `apt-get dist-upgrade`
    * Same as `full`

## Install

```bash
ansible-galaxy install Furdarius.upgrade
```

## Variables

All variables can be found in [defaults/main.yml](https://github.com/Furdarius/ansible-upgrade/blob/master/defaults/main.yml)

## Playbook example

```yaml
---
- hosts: all
  become: true
  roles:
    - upgrade
  vars:
    upgrade_apt_cache: 3600
    upgrade_type: safe
    upgrade_reboot: false
    upgrade_required_packages:
      - software-properties-common
      - python-software-properties
```

