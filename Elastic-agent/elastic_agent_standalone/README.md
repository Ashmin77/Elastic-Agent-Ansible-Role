
## README.md for `elastic_agent_standalone`

**File: `elastic_agent_standalone/README.md`**

# Elastic Agent Standalone Role

This Ansible role installs and configures the Elastic Agent on Ubuntu and RedHat servers in standalone mode.

## Directory Structure

```
elastic_agent_standalone
├── README.md
├── defaults
│   └── main.yml
├── files
├── handlers
│   └── main.yml
├── meta
│   └── main.yml
├── tasks
│   ├── install.yml
│   ├── main.yml
│   └── status.yml
├── templates
│   └── elastic-agent.yml.j2
├── tests
│   ├── inventory
│   └── test.yml
└── vars
  └── main.yml
```

## Variables

- `elastic_agent_version`: Version of Elastic Agent to install (default: "7.12.0")
- `elastic_agent_url`: URL to download Elastic Agent (default: "https://artifacts.elastic.co/downloads/beats/elastic-agent/elastic-agent-{{ elastic_agent_version }}-linux-x86_64.tar.gz")
- `elastic_agent_install_dir`: Installation directory for Elastic Agent (default: "/opt/Elastic/Agent")
- `elasticsearch_host`: Elasticsearch host (default: "localhost")
- `elasticsearch_port`: Elasticsearch port (default: 9200)
- `elasticsearch_username`: Elasticsearch username (default: "elastic")
- `elasticsearch_password`: Elasticsearch password (default: "changeme")

## Usage

Include this role in your playbook:

```yaml
- hosts: all
  become: yes
  roles:
  - elastic_agent_standalone
```

## Tasks

- Install Dependencies: Ensures the necessary packages (e.g., expect) are installed.
- Check Existing Installation: Checks if Elastic Agent is already installed.
- Download and Extract Elastic Agent: Downloads and extracts the Elastic Agent tarball.
- Install Elastic Agent: Uses expect to handle interactive installation prompts.
- Create Symlink: Creates a symlink to the Elastic Agent binary.
- Ensure Configuration Directory: Ensures the configuration directory exists.
- Copy Configuration File: Copies the Elastic Agent configuration file.
- Ensure Log Directory: Ensures the log directory exists.
- Start and Enable Service: Starts and enables the Elastic Agent service.
- Check and Display Service Status: Checks and displays the status of the Elastic Agent service.

## Example Playbook

```yaml
- hosts: all
  become: yes
  vars:
  elasticsearch_host: "localhost"
  elasticsearch_port: 9200
  elasticsearch_username: "elastic"
  elasticsearch_password: "changeme"
  roles:
  - elastic_agent_standalone
```

To run the playbook:

```bash
ansible-playbook -i inventory.ini deploy.yml
```

