## Role Name

Installs and configures Redis exporter to monitoring over Prometheus on RHEL/CentOS servers.

## Requirements

No special requirements; note that this role requires root access, so either run it in a playbook with a global `become: yes`, or invoke the role in your playbook like:

    - hosts: redis-cluster
      roles:
        - role: redis_exporter
          become: yes

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

        exporter_type: redis
        exporter_version: 0.21.2
        exporter_download_url: https://github.com/oliver006/redis_exporter/releases/download/v{{ exporter_version }}/redis_exporter-v{{ exporter_version }}.linux-amd64.tar.gz
        exporter_file_name: redis_exporter-v{{ exporter_version }}.linux-amd64.tar.gz
        exporter_folder_name: /opt
        exporter_port: 9121
        exporter_user: prometheus
        exporter_group: prometheus

## Dependencies

None

## Example Playbook

    - hosts: redis-cluster
      become: yes
      vars_files:
        - vars/main.yml
      roles:
        - { role: bilalcaliskan.redis }

*Inside `vars/main.yml`*:

        exporter_port: 9121
        exporter_user: prometheus
        exporter_group: prometheus

## License

MIT / BSD
