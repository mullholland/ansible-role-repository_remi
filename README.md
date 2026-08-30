# [Ansible role ansible-generator](#ansible-generator)

description

|GitHub|Downloads|Version|
|------|---------|-------|
|[![github](https://github.com/mullholland/ansible-role-ansible-generator/actions/workflows/molecule.yml/badge.svg)](https://github.com/mullholland/ansible-role-ansible-generator/actions/workflows/molecule.yml)|[![downloads](https://img.shields.io/ansible/role/d/mullholland/ansible-generator)](https://galaxy.ansible.com/mullholland/ansible-generator)|[![Version](https://img.shields.io/github/release/mullholland/ansible-role-ansible-generator.svg)](https://github.com/mullholland/ansible-role-ansible-generator/releases/)|
## [Example Playbook](#example-playbook)

This example is taken from [`molecule/default/converge.yml`](https://github.com/mullholland/ansible-role-ansible-generator/blob/master/molecule/default/converge.yml) and is tested on each push, pull request and release.

```yaml
---
- name: Converge
  hosts: all
  gather_facts: true
  # vars:
  #   example_var: "value"
  roles:
    - role: "{{ lookup('env', 'MOLECULE_PROJECT_DIRECTORY') }}"
```

The machine needs to be prepared. In CI this is done using [`molecule/default/prepare.yml`](https://github.com/mullholland/ansible-role-ansible-generator/blob/master/molecule/default/prepare.yml):

```yaml
---
- name: Prepare
  hosts: all
  gather_facts: true

  roles:
    # - role: mullholland.repository_codereadybuilder
    #   when:
    #     - (ansible_distribution == "RedHat" and ansible_distribution_major_version == "8") or
    #       (ansible_distribution == "CentOS" and ansible_distribution_major_version == "9")
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

The default values for the variables are set in [`defaults/main.yml`](https://github.com/mullholland/ansible-role-ansible-generator/blob/master/defaults/main.yml):

```yaml
---
repository_remi_php_version: "8.1"
```

## [Requirements](#requirements)

- pip packages listed in [requirements.txt](https://github.com/mullholland/ansible-role-ansible-generator/blob/master/requirements.txt).

## [State of used roles](#state-of-used-roles)

The following roles are used to prepare a system. You can prepare your system in another way.

| Requirement | GitHub | GitLab |
|-------------|--------|--------|
|[mullholland.repository_powertools](https://galaxy.ansible.com/mullholland/repository_powertools)|[![Build Status GitHub](https://github.com/mullholland/ansible-role-repository_powertools/workflows/Ansible%20Molecule/badge.svg)](https://github.com/mullholland/ansible-role-repository_powertools/actions)|[![Build Status GitLab](https://gitlab.com/mullholland-github-mirror/ansible-role-repository_powertools/badges/master/pipeline.svg)](https://gitlab.com/mullholland-github-mirror/ansible-role-repository_powertools)|
|[mullholland.repository_epel](https://galaxy.ansible.com/mullholland/repository_epel)|[![Build Status GitHub](https://github.com/mullholland/ansible-role-repository_epel/workflows/Ansible%20Molecule/badge.svg)](https://github.com/mullholland/ansible-role-repository_epel/actions)|[![Build Status GitLab](https://gitlab.com/mullholland-github-mirror/ansible-role-repository_epel/badges/master/pipeline.svg)](https://gitlab.com/mullholland-github-mirror/ansible-role-repository_epel)|
|[mullholland.repository_rpmfusion](https://galaxy.ansible.com/mullholland/repository_rpmfusion)|[![Build Status GitHub](https://github.com/mullholland/ansible-role-repository_rpmfusion/workflows/Ansible%20Molecule/badge.svg)](https://github.com/mullholland/ansible-role-repository_rpmfusion/actions)|[![Build Status GitLab](https://gitlab.com/mullholland-github-mirror/ansible-role-repository_rpmfusion/badges/master/pipeline.svg)](https://gitlab.com/mullholland-github-mirror/ansible-role-repository_rpmfusion)|

## [Context](#context)

This role is a part of many compatible roles. Have a look at [the documentation of these roles](https://mullholland.net) for further information.

## [Compatibility](#compatibility)

This role has been tested on these [container images](https://hub.docker.com/u/mullholland):

|container|tags|
|---------|----|
|[EL](https://hub.docker.com/r/mullholland/enterpriselinux)|all|
|[Rocky](https://hub.docker.com/r/mullholland/rockylinux)|all|
|[AlmaLinux](https://hub.docker.com/r/mullholland/almalinux)|all|
|[Fedora](https://hub.docker.com/r/mullholland/fedora/)|all|
|[CentOS](https://hub.docker.com/r/mullholland/centos)|all|

The minimum version of Ansible required is 2.10, tests have been done to:

- The version before the previous version.
- The previous version.
- The current version.

If you find issues, please register them in [GitHub](https://github.com/mullholland/ansible-role-ansible-generator/issues).

## [License](#license)

[MIT](https://github.com/mullholland/ansible-role-ansible-generator/blob/master/LICENSE).

## [Author Information](#author-information)

[Mullholland](https://mullholland.net)
