Ansible Role automation-agent
=========
- [Introduction](#introduction)
- [Requirements](#requirements)
- [Variables](#variables)
- [Tags](#tags)
- [Usage](#usage)
- [Examples](#examples)
- [Author](#author)

# Introduction

This role will install and configure an MongoDB automation agent. An up & running  OPS Manager Installation is required. The OPS Manager Host is the Installation Source.


# Requirements

- Running OPS Manager Installation
- Ansible Version >= 2.4


# Variables
| Name | Description | Default |
|:-----|:------------|:--------|
| automation_agent_package_name | Name of the Package to install | mongodb-mms-automation-agent-manager-5.4.9.5483-1.ppc64le.rhel7.rpm |
| automation_agent_package_state | Package state | present |
| automation_agent_service_names | List of service name | mongodb-mms-automation-agent.service |
| automation_agent_service_state | Service state | started |
| automation_agent_service_enabled | Service enabled | true |
| automation_agent_package_path  | Path where RPM is saved | /opt/mongodb |
| automation_agent_package_url | The URL where the RPM is downloaded from | not set |


# Tags
- automation-agent: run all tasks from this role
- automation-agent-install: ensure that all packages in __automation_agent_package_names__ are in state __automation_agent_package_state__
- automation-agent-config: ensure configuration
- automation-agent-service: ensure that all services in __automation_agent_service_names__ are in state __automation_agent_service_state__

# Usage

Example playbook

```yaml
- hosts: 127.0.0.1
  roles:
  - role: automation-agent
```

# Examples

```yaml
- hosts: 127.0.0.1
  vars:
    automation_agent_package_url: https://mongo-ops-host.example.com:8443/download/agent/automation/{{ automation_agent_package_name }}
    automation_agent_package_name: mongodb-mms-automation-agent-manager-5.4.9.5483-1.x86_64.rhel7.rpm
    config_param_mms_group_id: 123abc123abc123abc123abc
    config_param_mms_api_key: 456yxc456yxc456yxc456yxc456yxc456yxc
    config_param_mms_base_url: https://mongo-ops-host.example.com:8443
  roles:
  - role: automation-agent
```

# Author

Jens Schneider
