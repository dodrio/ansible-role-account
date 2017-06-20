# account

[![Build Status](https://travis-ci.org/m31271n/ansible-role-account.svg?branch=master)](https://travis-ci.org/m31271n/ansible-role-account)
[![Ansible Galaxy](https://img.shields.io/badge/galaxy-m31271n.account-blue.svg)](https://galaxy.ansible.com/m31271n/account)

Ansible role that manages accounts.

Original code is forked from [dochang/ansible-role-account](https://github.com/dochang/ansible-role-account).

## Requirements

None.

## Role Variables

+ `account_groups` (default: `[]`): A list of groups where each group support all parameters from `group` module.
+ `account_users` (default: `[]`): A list of users where each user support all parameters from `user` module, plus a special parameter `authorized_keys`.
+ `account_users.authorized_keys`: A list of ssh public keys where each key support all parameters from `authorized_key` module.

See `tasks/main.yml` for details.

## Dependencies

None.

## Example Playbook

```
- hosts: servers
  roles:
    - role: m31271n.account
      account_groups:
        - name: sudo
          system: yes
          state: present
      account_users:
        - name: foo
          createhome: yes
          groups: sudo
          authorized_keys:
            - key: 'xxxxxxxx'
              state: present
            - key: 'yyyyyyyy'
              state: absent
        - name: bar
          uid: 1024
          authorized_keys: []
```

* * *

<p align="center">Made with ❤ by <a href="http://index.m31271n.com">m31271n</a></p>
