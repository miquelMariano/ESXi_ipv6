Role Name
=========

Ansible role to enable/disable ipv6 on our ESXi servers

Requirements
------------

No requirements

Role Variables
--------------

No Variables

Dependencies
------------

No dependencies

Example Playbook
----------------

This play is executed when update_mode var is "true" and ensure that role is up to date. By default update var is "false"

miquelMariano.ESXi_{{ role }} folder must be exist. If not, the playbook not found role and fails. You shoud make dir manually "mkdir /etc/ansible/my_role"

```
		- hosts: ansible
 		  user: root
 		  tasks:
 		   - name: Ensure that role are up to date
 		     command: ansible-galaxy install --force {{ item }}
 		     with_items:
 		       - miquelMariano.ESXi_{{ role  }}
 		     when:
 		       - update_mode | default(False)
 		     tags: update
 		     ignore_errors: yes

		- hosts: "{{ servers }}:!localhost"
		  user: root
 		  serial: 15
 		  roles:
 		  - role: miquelMariano.ESXi_{{ role }}
```

Usage
------

`ansible-playbook playbooks/ESXi_config.yml -i inventory/ESXi --extra-vars "servers=servers_group1 role=ipv6 update_mode=true" --tags "update|status|enable|disable""`


License
-------

BSD

Author Information
------------------

[miquelMariano.github.io](https://miquelMariano.github.io) | [Twitter](https://twitter.com/miquelMariano)

