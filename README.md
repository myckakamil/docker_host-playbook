# Docker Host Configuration Playbook

## Overview

This Ansible playbook configures a server defined in the `docker_host` inventory group.  
Its primary purpose is to:

- Prepare the system (APT cache update)
- Install and configure Docker
- Deploy Immich as a container

The playbook is designed to be idempotent and safe to re-run.

## Inventory Example

```ini
[docker_host]
192.168.1.100 ansible_user=debian
```

## Vault Example

```yaml
---
password: P@$$w0rd
```

---

## Running the Playbook

```bash
ansible-playbook -i inventory.ini playbook.yml --ask-vault-pass
```

Or with a vault password file:

```bash
ansible-playbook -i inventory.ini playbook.yml --vault-password-file .vault_pass
```

---

## Directory Structure Example

```
.
├── playbook.yml
├── vault.yaml
├── tasks/
│   ├── install_docker.yaml
│   └── immich.yaml
└── inventory.ini

.
├── inventory.ini
├── main.yaml
├── README.md
├── tasks
│   ├── immich.yaml
│   └── install_docker.yaml
├── templates
│   ├── immich_compose.yaml.j2
│   └── immich_env.j2
└── vars
    └── vault.yaml
```
