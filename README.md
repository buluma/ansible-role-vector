# [Ansible role vector](#ansible-role-vector)

Vector Role

|GitHub|GitLab|Downloads|Version|
|------|------|---------|-------|
|[![github](https://github.com/buluma/ansible-role-vector/workflows/Ansible%20Molecule/badge.svg)](https://github.com/buluma/ansible-role-vector/actions)|[![gitlab](https://gitlab.com/shadowwalker/ansible-role-vector/badges/master/pipeline.svg)](https://gitlab.com/shadowwalker/ansible-role-vector)|[![downloads](https://img.shields.io/ansible/role/d/buluma/vector)](https://galaxy.ansible.com/buluma/vector)|[![Version](https://img.shields.io/github/release/buluma/ansible-role-vector.svg)](https://github.com/buluma/ansible-role-vector/releases/)|

## [Example Playbook](#example-playbook)

This example is taken from [`molecule/default/converge.yml`](https://github.com/buluma/ansible-role-vector/blob/master/molecule/default/converge.yml) and is tested on each push, pull request and release.

```yaml
---
- gather_facts: false
  hosts: all
  name: Converge
  roles:
  - role: buluma.vector
```

The machine needs to be prepared. In CI this is done using [`molecule/default/prepare.yml`](https://github.com/buluma/ansible-role-vector/blob/master/molecule/default/prepare.yml):

```yaml
---
- become: true
  gather_facts: false
  hosts: all
  name: Prepare
  roles:
  - role: buluma.bootstrap
  - role: buluma.ca_certificates
```

Also see a [full explanation and example](https://buluma.github.io/how-to-use-these-roles.html) on how to use these roles.

## [Role Variables](#role-variables)

The default values for the variables are set in [`defaults/main.yml`](https://github.com/buluma/ansible-role-vector/blob/master/defaults/main.yml):

```yaml
---
vector_bin_path: /usr/bin/{{ vector_exec_name }}
vector_config_path: /etc/vector
vector_config_template_path: templates/config/
vector_configs_folder: "{{ vector_config_path }}"
vector_data_dir: /var/lib/vector
vector_deb_package: https://packages.timber.io/vector/{{ vector_version }}/vector_{{ vector_version }}-1_{{ vector_package_architecture }}.deb
vector_documentation_link: https://vector.dev/docs/about/what-is-vector/
vector_env_path: /etc/default/vector
vector_exec_name: vector
vector_force_reinstall: false
vector_group: vector
vector_log_output: journal
vector_package_architecture: amd64
vector_service_enabled: true
vector_service_state: started
vector_service_template_path: vector.service.j2
vector_skeleton_paths: "{{ vector_skeleton_paths_base + vector_skeleton_paths_extend | default([]) }}"
vector_skeleton_paths_base:
  - "{{ vector_config_path }}"
vector_user: vector
vector_version: 0.29.1
```

## [Requirements](#requirements)

- pip packages listed in [requirements.txt](https://github.com/buluma/ansible-role-vector/blob/master/requirements.txt).

## [State of used roles](#state-of-used-roles)

The following roles are used to prepare a system. You can prepare your system in another way.

| Requirement | GitHub | GitLab |
|-------------|--------|--------|
|[buluma.bootstrap](https://galaxy.ansible.com/buluma/bootstrap)|[![Build Status GitHub](https://github.com/buluma/ansible-role-bootstrap/workflows/Ansible%20Molecule/badge.svg)](https://github.com/buluma/ansible-role-bootstrap/actions)|[![Build Status GitLab](https://gitlab.com/shadowwalker/ansible-role-bootstrap/badges/master/pipeline.svg)](https://gitlab.com/shadowwalker/ansible-role-bootstrap)|
|[buluma.ca_certificates](https://galaxy.ansible.com/buluma/ca_certificates)|[![Build Status GitHub](https://github.com/buluma/ansible-role-ca_certificates/workflows/Ansible%20Molecule/badge.svg)](https://github.com/buluma/ansible-role-ca_certificates/actions)|[![Build Status GitLab](https://gitlab.com/shadowwalker/ansible-role-ca_certificates/badges/master/pipeline.svg)](https://gitlab.com/shadowwalker/ansible-role-ca_certificates)|

## [Context](#context)

This role is part of many compatible roles. Have a look at [the documentation of these roles](https://buluma.github.io/) for further information.

Here is an overview of related roles:
![dependencies](https://raw.githubusercontent.com/buluma/ansible-role-vector/png/requirements.png "Dependencies")

## [Compatibility](#compatibility)

This role has been tested on these [container images](https://hub.docker.com/u/buluma):

|container|tags|
|---------|----|
|[Debian](https://hub.docker.com/r/buluma/debian)|all|
|[Ubuntu](https://hub.docker.com/r/buluma/ubuntu)|all|

The minimum version of Ansible required is 2.12, tests have been done on:

- The previous version.
- The current version.
- The development version.

If you find issues, please register them on [GitHub](https://github.com/buluma/ansible-role-vector/issues).

## [License](#license)

[Apache-2.0](https://github.com/buluma/ansible-role-vector/blob/master/LICENSE).

## [Author Information](#author-information)

[buluma](https://buluma.github.io/)
