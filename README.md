# Elastic Agent Ansible Role

This repository contains Ansible roles for managing Elastic Agent installations in standalone mode. The roles provided are:

1. **Elastic Agent Standalone Role**: Installs and configures Elastic Agent as a standalone agent.
2. **Elastic Agent Uninstall Role**: Uninstalls the Elastic Agent and cleans up any related configurations.

## Directory Structure

```
Elastic-agent
├── deploy.yml
├── elastic_agent_standalone
│   ├── README.md
│   ├── defaults
│   │   └── main.yml
│   ├── files
│   ├── handlers
│   │   └── main.yml
│   ├── meta
│   │   └── main.yml
│   ├── tasks
│   │   ├── install.yml
│   │   ├── main.yml
│   │   └── status.yml
│   ├── templates
│   │   └── elastic-agent.yml.j2
│   ├── tests
│   │   ├── inventory
│   │   └── test.yml
│   └── vars
│       └── main.yml
├── elastic_agent_uninstall_role
│   ├── README.md
│   ├── defaults
│   │   └── main.yml
│   ├── files
│   ├── handlers
│   │   └── main.yml
│   ├── meta
│   │   └── main.yml
│   ├── tasks
│   │   └── main.yml
│   ├── templates
│   ├── tests
│   │   ├── inventory
│   │   └── test.yml
│   └── vars
│       └── main.yml
├── inventory.ini
└── uninstall_agent.yml
```

## Roles

1. Elastic Agent Standalone Role

Installs and configures Elastic Agent on Ubuntu and RedHat servers in standalone mode.

Path: elastic_agent_standalone

Tasks:
- Install dependencies
- Check for existing installation
- Download and extract Elastic Agent
- Configure Elastic Agent
- Start and enable Elastic Agent service
- Check and display service status

2. Elastic Agent Uninstall Role

Uninstalls Elastic Agent from Ubuntu and RedHat servers and cleans up any configurations.

Path: elastic_agent_uninstall_role

Tasks:
- Stop and disable Elastic Agent service
- Remove installation directory
- Remove symlink
- Remove configuration and log directories

## Playbooks

Deploy Playbook

Installs Elastic Agent.

Path: deploy.yml

Usage: `ansible-playbook -i inventory.ini deploy.yml`

Uninstall Playbook

Uninstalls Elastic Agent.

Path: uninstall_agent.yml

Usage: `ansible-playbook -i inventory.ini uninstall_agent.yml`

## Inventory

Define your target hosts in the inventory.ini file.

Usage:

To install Elastic Agent, run:

```bash
ansible-playbook -i inventory.ini deploy.yml
```

To uninstall Elastic Agent, run:

```bash
ansible-playbook -i inventory.ini uninstall_agent.yml
```