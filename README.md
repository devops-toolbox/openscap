Role Name
=========

openscap: Openscap

[![Build Status](https://travis-ci.org/cmihai-ansible/openscap.svg?branch=master)](https://travis-ci.org/cmihai-ansible/openscap)

Ansible galaxy:
---------------

[https://galaxy.ansible.com/devopstoolbox.openscap](https://galaxy.ansible.com/devopstoolbox.openscap)

```bash
ansible-galaxy install devopstoolbox.openscap
```

Requirements
------------

- For RHEL, a Red Hat subscription or functional local repository.
- Ansible 2.4 or higher

Role Variables
--------------

```yaml
openscap_packages_state: present
openscap_remove_packages: true
openscap_enable_service: true
openscap_enable_selinux: true
openscap_copy_templates: true
openscap_firewall_configure: true
openscap_firewall_rules:
  - service: ssh
  - port: 3389
openscap_users:
  - user: devops
    group: docker
openscap_selinux_booleans:
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
- name: Install openscap on localhost
  hosts:
    - localhost
  connection: local

  tasks:
    - name: openscap is configured
      import_role:
        name: devopstoolbox.openscap
      vars:
        openscap_packages_state: present
        openscap_remove_packages: true
        openscap_enable_service: true
        openscap_enable_selinux: true
        openscap_copy_templates: true
        openscap_firewall_configure: true
        openscap_firewall_rules:
          - service: ssh
          - port: 3389
        openscap_users:
          - user: devops
            group: docker
        openscap_selinux_booleans:
          - name: ftp_home_dir
            state: true
            persistent: true
      tags: openscap
```

License
-------

MIT

Author Information
------------------

- [Mihai Criveti](https://www.linkedin.com/in/devopstoolbox.)
