# Ansible role [vector](https://galaxy.ansible.com/ui/standalone/roles/buluma/vector/documentation)

Vector Role

|GitHub|Version|Issues|Pull Requests|Downloads|
|------|-------|------|-------------|---------|
|[![github](https://github.com/buluma/ansible-role-vector/actions/workflows/molecule.yml/badge.svg)](https://github.com/buluma/ansible-role-vector/actions/workflows/molecule.yml)|[![Version](https://img.shields.io/github/release/buluma/ansible-role-vector.svg)](https://github.com/buluma/ansible-role-vector/releases/)|[![Issues](https://img.shields.io/github/issues/buluma/ansible-role-vector.svg)](https://github.com/buluma/ansible-role-vector/issues/)|[![PullRequests](https://img.shields.io/github/issues-pr-closed-raw/buluma/ansible-role-vector.svg)](https://github.com/buluma/ansible-role-vector/pulls/)|[![Ansible Role](https://img.shields.io/ansible/role/d/buluma/vector)](https://galaxy.ansible.com/ui/standalone/roles/buluma/vector/documentation)|

## [Example Playbook](#example-playbook)

This example is taken from [`molecule/default/converge.yml`](https://github.com/buluma/ansible-role-vector/blob/master/molecule/default/converge.yml) and is tested on each push, pull request and release.

```yaml
---
- name: Converge
  hosts: all
  gather_facts: false
  roles:
    - role: buluma.vector
```

The machine needs to be prepared. In CI this is done using [`molecule/default/prepare.yml`](https://github.com/buluma/ansible-role-vector/blob/master/molecule/default/prepare.yml):

```yaml
---
- name: Prepare
  hosts: all
  become: yes
  gather_facts: no

  roles:
    - role: buluma.bootstrap
```

Also see a [full explanation and example](https://buluma.github.io/how-to-use-these-roles.html) on how to use these roles.

## [Role Variables](#role-variables)

The default values for the variables are set in [`defaults/main.yml`](https://github.com/buluma/ansible-role-vector/blob/master/defaults/main.yml):

```yaml
---

## General
# Version
vector_version: 0.29.1
vector_package_architecture: amd64

# Deb
vector_deb_package: "https://packages.timber.io/vector/{{ vector_version }}/vector_{{ vector_version }}-1_{{ vector_package_architecture }}.deb"

# Set true to force the download and installation of the package
vector_force_reinstall: false

# Paths
vector_exec_name: vector
vector_env_path: "/etc/default/vector"
vector_bin_path: "/usr/bin/{{ vector_exec_name }}"
vector_config_path: "/etc/vector"
vector_skeleton_paths_base:
  - "{{ vector_config_path }}"
vector_skeleton_paths: "{{ vector_skeleton_paths_base + vector_skeleton_paths_extend | default([]) }}"

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
# vector_log_output_stdout:
# vector_log_output_stderr:

vector_config_template_path: "templates/config/"
vector_service_template_path: "vector.service.j2"

# vector_config_files:  # https://vector.dev/docs/reference/configuration/#multiple-files
#   - "{{ vector_config_path }}/*.toml"
#   - "{{ vector_config_path }}/*.yml"
vector_configs_folder: "{{ vector_config_path }}"  # https://vector.dev/docs/reference/configuration/#automatic-namespacing

vector_data_dir: "/var/lib/vector"
# vector_syslog_identifier: vector
```

## [Requirements](#requirements)

- pip packages listed in [requirements.txt](https://github.com/buluma/ansible-role-vector/blob/master/requirements.txt).

## [State of used roles](#state-of-used-roles)

The following roles are used to prepare a system. You can prepare your system in another way.

| Requirement | GitHub | Version |
|-------------|--------|--------|
|[buluma.bootstrap](https://galaxy.ansible.com/buluma/bootstrap)|[![Ansible Molecule](https://github.com/buluma/ansible-role-bootstrap/actions/workflows/molecule.yml/badge.svg)](https://github.com/buluma/ansible-role-bootstrap/actions/workflows/molecule.yml)|[![Version](https://img.shields.io/github/release/buluma/ansible-role-bootstrap.svg)](https://github.com/shadowwalker/ansible-role-bootstrap)|

## [Context](#context)

This role is a part of many compatible roles. Have a look at [the documentation of these roles](https://buluma.github.io/) for further information.

Here is an overview of related roles:

![dependencies](https://raw.githubusercontent.com/buluma/ansible-role-vector/png/requirements.png "Dependencies")

## [Compatibility](#compatibility)

This role has been tested on these [container images](https://hub.docker.com/u/buluma):

|container|tags|
|---------|----|
|[Debian](https://hub.docker.com/repository/docker/buluma/debian/general)|all|
|[Ubuntu](https://hub.docker.com/repository/docker/buluma/ubuntu/general)|all|

The minimum version of Ansible required is 2.12, tests have been done to:

- The previous version.
- The current version.
- The development version.

If you find issues, please register them in [GitHub](https://github.com/buluma/ansible-role-vector/issues)

## [Changelog](#changelog)

[Role History](https://github.com/buluma/ansible-role-vector/blob/master/CHANGELOG.md)

## [License](#license)

[Apache-2.0](https://github.com/buluma/ansible-role-vector/blob/master/LICENSE)

## [Author Information](#author-information)

[Shadow Walker](https://buluma.github.io/)

