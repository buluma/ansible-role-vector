# [vector](#vector)

Vector Role

|GitHub|GitLab|Downloads|Version|Issues|Pull Requests|
|------|------|-------|-------|------|-------------|
|[![github](https://github.com/buluma/ansible-role-vector/workflows/Ansible%20Molecule/badge.svg)](https://github.com/buluma/ansible-role-vector/actions)|[![gitlab](https://gitlab.com/shadowwalker/ansible-role-vector/badges/master/pipeline.svg)](https://gitlab.com/shadowwalker/ansible-role-vector)|[![downloads](https://img.shields.io/ansible/role/d/4878)](https://galaxy.ansible.com/buluma/vector)|[![Version](https://img.shields.io/github/release/buluma/ansible-role-vector.svg)](https://github.com/buluma/ansible-role-vector/releases/)|[![Issues](https://img.shields.io/github/issues/buluma/ansible-role-vector.svg)](https://github.com/buluma/ansible-role-vector/issues/)|[![PullRequests](https://img.shields.io/github/issues-pr-closed-raw/buluma/ansible-role-vector.svg)](https://github.com/buluma/ansible-role-vector/pulls/)|

## [Example Playbook](#example-playbook)

This example is taken from [`molecule/default/converge.yml`](https://github.com/buluma/ansible-role-vector/blob/master/molecule/default/converge.yml) and is tested on each push, pull request and release.

```yaml
---
- name: Converge
  hosts: all
  roles:
    - role: buluma.vector
```

Also see a [full explanation and example](https://buluma.github.io/how-to-use-these-roles.html) on how to use these roles.

## [Role Variables](#role-variables)

The default values for the variables are set in [`defaults/main.yml`](https://github.com/buluma/ansible-role-vector/blob/master/defaults/main.yml):

```yaml
---

## General
# Version
vector_version: 0.19.3
vector_package_architecture: amd64

# Deb
vector_deb_package: "https://packages.timber.io/vector/{{ vector_version }}/vector-{{ vector_package_architecture }}.deb"

# Set true to force the download and installation of the package
vector_force_reinstall: false

# Paths
vector_bin_path: "/usr/bin"
vector_skeleton_paths:
  - "{{ vector_bin_path }}"
vector_exec_name: vector

## Service options
# Documentation
vector_documentation_link: https://vector.dev/docs/about/what-is-vector/

# Owner
vector_user: vector
vector_group: vector
# Maybe you will need some extra groups for user vector
# vector_groups: []

# Start on boot
vector_service_enabled: True
# Current state: started, stopped
vector_service_state: started

# Logs
# If wanted to output the logs to a file define the following variable
# More information at https://www.freedesktop.org/software/systemd/man/systemd.exec.html#StandardOutput=
vector_log_output: journal

vector_config_template_path: "vector.toml.j2"
vector_service_template_path: "vector.service.j2"

vector_data_dir: "/var/lib/vector"
# vector_syslog_identifier: vector
```

## [Requirements](#requirements)

- pip packages listed in [requirements.txt](https://github.com/buluma/ansible-role-vector/blob/master/requirements.txt).


## [Context](#context)

This role is a part of many compatible roles. Have a look at [the documentation of these roles](https://buluma.github.io/) for further information.

Here is an overview of related roles:

![dependencies](https://raw.githubusercontent.com/buluma/ansible-role-vector/png/requirements.png "Dependencies")

## [Compatibility](#compatibility)

This role has been tested on these [container images](https://hub.docker.com/u/buluma):

|container|tags|
|---------|----|
|[Debian](https://hub.docker.com/repository/docker/buluma/debian/general)|all|

The minimum version of Ansible required is 2.12, tests have been done to:

- The previous version.
- The current version.
- The development version.

If you find issues, please register them in [GitHub](https://github.com/buluma/ansible-role-vector/issues)

## [Changelog](#changelog)

[Role History](https://github.com/buluma/ansible-role-vector/blob/master/CHANGELOG.md)

## [License](#license)

[Apache-2.0](https://github.com/buluma/ansible-role-vector/blob/master/LICENSE).

## [Author Information](#author-information)

[buluma](https://buluma.github.io/)

Please consider [sponsoring me](https://github.com/sponsors/buluma).

### [Special Thanks](#special-thanks)

Template inspired by [Robert de Bock](https://github.com/robertdebock)
