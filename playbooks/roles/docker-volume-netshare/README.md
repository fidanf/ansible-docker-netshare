Ansible Docker Volume Netshare
=========

Installs [Docker Volume Netshare](https://github.com/ContainX/docker-volume-netshare) for Debian / Ubuntu.

Requirements
------------

- Docker

Role Variables
--------------

See [./defaults/main.yml](./defaults/main.yml) variables

Dependencies
------------

None

Example Playbook
----------------

```yaml
---
- hosts: all
  gather_facts: yes
  become: yes

  roles:
    - name: docker-volume-netshare
      vars:
        dvn_start_opt: cifs
        dvn_volumes_config:
          - name: samba/share
            driver: cifs
            driver_options:
              username: "user"
              password: "pass"
              fileMode: "0777"
              dirMode: "0777"

```

License
-------

BSD
