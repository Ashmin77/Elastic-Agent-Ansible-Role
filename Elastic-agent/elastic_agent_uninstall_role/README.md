
## Elastic Agent Uninstall Role

This Ansible role uninstalls the Elastic Agent from Ubuntu and RedHat servers, including cleanup of any configuration, logs, and binaries.

### Directory Structure

```
elastic_agent_uninstall_role
├── README.md
├── defaults
│   └── main.yml
├── files
├── handlers
│   └── main.yml
├── meta
│   └── main.yml
├── tasks
│   └── main.yml
├── templates
├── tests
│   ├── inventory
│   └── test.yml
└── vars
  └── main.yml
```

### Variables

- `elastic_agent_install_dir`: Installation directory for Elastic Agent (default: "/opt/Elastic/Agent")
- `elastic_agent_config_dir`: Configuration directory for Elastic Agent (default: "/etc/elastic-agent")
- `elastic_agent_log_dir`: Log directory for Elastic Agent (default: "/var/log/elastic-agent")
- `elastic_agent_bin`: Binary location for Elastic Agent (default: "/usr/bin/elastic-agent")

### Usage

Include this role in your playbook:

```yaml
- hosts: all
  become: yes
  roles:
  - elastic_agent_uninstall_role
```

### Tasks

- Stop and Disable the Service: Stops the Elastic Agent service and disables it to prevent it from starting automatically.
- Remove Installation Directory: Deletes the directory where the Elastic Agent is installed.
- Remove Symlink: Removes the symlink to the Elastic Agent binary.
- Remove Configuration Directory: Deletes the configuration directory for the Elastic Agent.
- Remove Log Directory: Deletes the log directory for the Elastic Agent.
- Debug Messages: Provides clear output messages indicating the status of each removal step.

### Example Playbook

```yaml
- hosts: all
  become: yes
  roles:
  - elastic_agent_uninstall_role
```

To run the playbook:

```bash
ansible-playbook -i inventory.ini uninstall_agent.yml
```

