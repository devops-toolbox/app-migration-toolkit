Role Name
=========

app-migration-toolkit: App-migration-toolkit

[![Build Status](https://travis-ci.org/cmihai-ansible/app-migration-toolkit.svg?branch=master)](https://travis-ci.org/cmihai-ansible/app-migration-toolkit)

Ansible galaxy:
---------------

[https://galaxy.ansible.com/devopstoolbox.app-migration-toolkit](https://galaxy.ansible.com/devopstoolbox.app-migration-toolkit)

```bash
ansible-galaxy install devopstoolbox.app-migration-toolkit
```

Requirements
------------

- For RHEL, a Red Hat subscription or functional local repository.
- Ansible 2.4 or higher

Role Variables
--------------

```yaml
app-migration-toolkit_packages_state: present
app-migration-toolkit_remove_packages: true
app-migration-toolkit_enable_service: true
app-migration-toolkit_enable_selinux: true
app-migration-toolkit_copy_templates: true
app-migration-toolkit_firewall_configure: true
app-migration-toolkit_firewall_rules:
  - service: ssh
  - port: 3389
app-migration-toolkit_users:
  - user: devops
    group: docker
app-migration-toolkit_selinux_booleans:
  - name: ftp_home_dir
    state: true
    persistent: true
```

Dependencies
------------

- For Red Hat, subscription-manager.

Example Playbook
----------------

```yaml
---
- name: Install app-migration-toolkit on localhost
  hosts:
    - localhost
  connection: local

  tasks:
    - name: app-migration-toolkit is configured
      import_role:
        name: devopstoolbox.app-migration-toolkit
      vars:
        app-migration-toolkit_packages_state: present
        app-migration-toolkit_remove_packages: true
        app-migration-toolkit_enable_service: true
        app-migration-toolkit_enable_selinux: true
        app-migration-toolkit_copy_templates: true
        app-migration-toolkit_firewall_configure: true
        app-migration-toolkit_firewall_rules:
          - service: ssh
          - port: 3389
        app-migration-toolkit_users:
          - user: devops
            group: docker
        app-migration-toolkit_selinux_booleans:
          - name: ftp_home_dir
            state: true
            persistent: true
      tags: app-migration-toolkit
```

License
-------

MIT

Author Information
------------------

- [Mihai Criveti](https://www.linkedin.com/in/devopstoolbox.)
