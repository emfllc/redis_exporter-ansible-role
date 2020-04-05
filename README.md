## Redis Exporter Ansible Role

[![Build Status](https://travis-ci.org/bilalcaliskan/redis_exporter-ansible-role.svg?branch=master)](https://travis-ci.org/bilalcaliskan/redis_exporter-ansible-role)

Installs and configures redis-exporter to expose redis metrics to Prometheus on RHEL/CentOS 7/8 instances.

## Requirements

No special requirements; note that this role requires root access, so either run it in a playbook with a global `become: yes`, or invoke the role in your playbook like:

      - hosts: all
        become: true
        roles:
          - role: bilalcaliskan.redis_exporter

## Role Variables

See the default values in 'defaults/main.yml'. You can overwrite them in 'vars/main.yml' if neccessary.

## Dependencies

None

## Example Playbook

      - hosts: all
        become: true
        vars_files:
          - vars/main.yml
        roles:
          - role: bilalcaliskan.redis_exporter

*Inside `vars/main.yml`*:

        version: 0.21.2
        exporter_port: 9121
        user: redisexporter
        group: redisexporter
        required_packages:
          - firewalld

## Playbook for uninstall

      - hosts: all
        become: true
        vars_files:
          - vars/main.yml
        roles:
          - role: bilalcaliskan.redis_exporter

*Inside `vars/main.yml`*:

        install_redis_exporter: false

## License

MIT / BSD
