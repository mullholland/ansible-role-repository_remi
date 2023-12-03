# [Ansible role repository_remi](#repository_remi)

description

|GitHub|Downloads|Version|
|------|---------|-------|
|[![github](https://github.com/mullholland/ansible-role-repository_remi/actions/workflows/molecule.yml/badge.svg)](https://github.com/mullholland/ansible-role-repository_remi/actions/workflows/molecule.yml)|[![downloads](https://img.shields.io/ansible/role/d/mullholland/repository_remi)](https://galaxy.ansible.com/mullholland/repository_remi)|[![Version](https://img.shields.io/github/release/mullholland/ansible-role-repository_remi.svg)](https://github.com/mullholland/ansible-role-repository_remi/releases/)|
## [Example Playbook](#example-playbook)

This example is taken from [`molecule/default/converge.yml`](https://github.com/mullholland/ansible-role-repository_remi/blob/master/molecule/default/converge.yml) and is tested on each push, pull request and release.

```yaml
---
- name: Converge
  hosts: all
  become: true
  gather_facts: true
  # vars:
  #   example_var: "value"
  roles:
    - role: "mullholland.repository_remi"
```

The machine needs to be prepared. In CI this is done using [`molecule/default/prepare.yml`](https://github.com/mullholland/ansible-role-repository_remi/blob/master/molecule/default/prepare.yml):

```yaml
---
- name: Prepare
  hosts: all
  become: true
  gather_facts: true

  roles:
    - role: mullholland.repository_codereadybuilder
      when:
        - (ansible_distribution == "RedHat" and ansible_distribution_major_version == "8") or
          (ansible_distribution == "CentOS" and ansible_distribution_major_version == "9")
    - role: mullholland.repository_powertools
      when:
        - ansible_distribution in [ "CentOS", "Rocky", "AlmaLinux" ]
        - ansible_distribution_major_version == "8"
    - role: mullholland.repository_epel
      when:
        - (ansible_distribution == "Amazon" and
          ansible_distribution_major_version == "2") or
          (ansible_distribution in [ "RedHat", "CentOS", "Rocky", "AlmaLinux" ])
    - role: mullholland.repository_rpmfusion
      when:
        - ansible_distribution == "Fedora"
```



## [Role Variables](#role-variables)

The default values for the variables are set in [`defaults/main.yml`](https://github.com/mullholland/ansible-role-repository_remi/blob/master/defaults/main.yml):

```yaml
---
repository_remi_php_version: "8.1"
```

## [Requirements](#requirements)

- pip packages listed in [requirements.txt](https://github.com/mullholland/ansible-role-repository_remi/blob/master/requirements.txt).


## [Context](#context)

This role is a part of many compatible roles. Have a look at [the documentation of these roles](https://mullholland.net) for further information.

Here is an overview of related roles:
![dependencies](https://raw.githubusercontent.com/mullholland/ansible-role-repository_remi/png/requirements.png "Dependencies")

## [Compatibility](#compatibility)

This role has been tested on these [container images](https://hub.docker.com/u/mullholland):

|container|tags|
|---------|----|
|[EL](https://hub.docker.com/r/mullholland/enterpriselinux)|all|
|[Amazon](https://hub.docker.com/r/mullholland/amazonlinux)|Candidate|
|[Fedora](https://hub.docker.com/r/mullholland/fedora/)|all|

The minimum version of Ansible required is 2.10, tests have been done to:

- The previous version.
- The current version.
- The development version.

If you find issues, please register them in [GitHub](https://github.com/mullholland/ansible-role-repository_remi/issues).

## [License](#license)

[MIT](https://github.com/mullholland/ansible-role-repository_remi/blob/master/LICENSE).

## [Author Information](#author-information)

[Mullholland](https://mullholland.net)
