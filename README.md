# Fedora Container for Molecule

An [Fedora][fedora] based container image for testing [Ansible][ansible] Roles with [Molecule][molecule].

## Example Molecule scenario

The example `molecule.yml` below is a scenario to run test on Fedora 33.

```yml
---
dependency:
  name: galaxy
driver:
  name: docker
lint: |
  set -e
  yamllint .
  ansible-lint
  flake8
platforms:
  - name: instance
    image: "ghcr.io/hspaans/molecule-container-fedora:33"
    command: ""
    volumes:
      - /sys/fs/cgroup:/sys/fs/cgroup:ro
    privileged: true
    pre_build_image: true
provisioner:
  name: ansible
verifier:
  name: testinfra
```

## Versions

The container is based on [LTS](https://en.wikipedia.org/wiki/Long-term_support) distribution versions with official support and fall within N and N-1. The *latest*-tag is an experimental tag to test future releases.

| Platform | Version |                                    Image                                     |
| :------: | :-----: | :--------------------------------------------------------------------------: |
|  Fedora  |   32    |     [hspaans/molecule-container-fedora:32][molecule-container-fedora:32]      |
|  Fedora  |   33    |     [hspaans/molecule-container-fedora:33][molecule-container-fedora:33]      |
|  Fedora  |   34    | [hspaans/molecule-container-fedora:latest][molecule-container-fedora:latest] |

[ansible]: https://github.com/ansible/ansible
[fedora]: https://centos.org
[molecule]: https://github.com/ansible-community/molecule
[molecule-container-fedora:latest]: ghcr.io/hspaans/molecule-container-fedora:latest
[molecule-container-fedora:32]: ghcr.io/hspaans/molecule-container-fedora:32
[molecule-container-fedora:33]: ghcr.io/hspaans/molecule-container-fedora:33
