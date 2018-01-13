# luzifer-ansible / logrotate

This role installs logrotate on a host and optionally adds logrotate configuration files.

## Requirements

- Debian >= 8 (jessie)
- Ubuntu >= 16.04 (xenial)

## Usage

See the [Ansible Galaxy Intro](https://galaxy.ansible.com/intro) for usage of roles within Ansible Galaxy.

Custom logrotate files are supplied through the `logrotate_configs` variable:

```yaml
logrotate_configs:
  - name: vault
    paths:
      - '/var/log/vault/*.log'
    lines:
      - missingok
      - notifempty
      - compress
      - copytruncate
      - daily
      - maxsize 100M
      - rotate 7
    scripts:
      postrotate: ls -lh /var/log/vault  # Just a demonstration, ls makes no sense
```
