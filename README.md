# Ansible Role: apache

Role to install httpd/apache.


<!-- TOC depthFrom:2 depthTo:6 withLinks:1 updateOnSave:1 orderedList:0 -->

- [Requirements](#requirements)
- [Dependencies](#dependencies)
- [Role Variables](#role-variables)
- [Example Playbook](#example-playbook)
- [License](#license)

<!-- /TOC -->

## Requirements
* Ansible >= 2.9


## Dependencies
Depends on no other role.


## Role Variables

see [defaults/main.yml](defaults/main.yml)


## Example Playbook
A short example how to use the role within a playbook.

```
- hosts: all
  roles:
    - { role: apache }
```

## License
BSD
