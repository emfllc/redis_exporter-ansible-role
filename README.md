## Redis Exporter Ansible Role

[![CI](https://github.com/bilalcaliskan/redis_exporter-ansible-role/workflows/CI/badge.svg?event=push)](https://github.com/bilalcaliskan/redis_exporter-ansible-role/actions?query=workflow%3ACI)

Installs and configures redis-exporter to expose Redis metrics to Prometheus on RHEL/CentOS 7/8 instances.

### Requirements

This role requires minimum Ansible version 2.4 and maximum Ansible version 2.9. You can install suggested version with pip:
```
$ pip install "ansible==2.9.16"
```

This role requires a Running Redis process on the same server. You can set up Redis instances with Sentinel using bilalcaliskan.redis role.
Also note that this role requires root access, so either run it in a playbook with a global `become: true`, or invoke the role in your playbook like:

*If you have a running Redis process on the same server*:
```yaml
- hosts: all
  become: true
  roles:
    - role: bilalcaliskan.redis_exporter
```

*If you do not have a running Redis process on the same server, it will setup Redis and Redis exporter sequentially*:
```yaml
- hosts: all
  become: true
  roles:
    - role: bilalcaliskan.redis
    - role: bilalcaliskan.redis_exporter
```

### Role Variables
See the default values in [defaults/main.yml](defaults/main.yml). You can overwrite them in [vars/main.yml](vars/main.yml) if neccessary or you can set them while running playbook.

> Please note that this role will ensure that `firewalld` systemd service on your servers are started and enabled by default. If you want to stop and disable `firewalld` service, please modify below variable as false when running playbook:  
> ```yaml  
> firewalld_enabled: false

### Dependencies

None

### Example Playbook File For `Installation`

```yaml
- hosts: all
  become: true
  roles:
    - role: bilalcaliskan.redis_exporter
      vars:
        install_redis_exporter: true
        redis_port: 6379
        version: 1.15.0
```

You can also override default variables inside [vars/main.yml](vars/main.yml)*:
```yaml
version: 1.15.0
```

### Example Playbook File For `Uninstallation`

```yaml
- hosts: all
  become: true
  roles:
    - role: bilalcaliskan.redis_exporter
      vars:
        install_redis_exporter: false
```

### License

MIT / BSD
