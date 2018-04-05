[![Build Status](https://travis-ci.org/bendews/ansible-cloudflared.svg?branch=master)](https://travis-ci.org/bendews/ansible-cloudflared)

# cloudflared

This role simplifies the process of installing and enabling the `cloudflared` package. Commonly used as a DNS-Over-HTTPS proxy for the Cloudflare [1.1.1.1 service](https://blog.cloudflare.com/announcing-1111/).

## Requirements

- Python >= 2.6
- Ansible >= 2.4
- systemd

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml` for more variables that can be modified)

```yaml
cloudflared_allow_firewall: false
cloudflared_enable_service: true
cloudflared_upstream: "https://1.1.1.1/dns-query"
cloudflared_port: 5053
cloudflared_options: "proxy-dns --port {{ cloudflared_port }} --upstream {{ cloudflared_upstream }}"
cloudflared_bin_location: "/usr/local/bin"
```

# Example Playbook

    - hosts: servers
      tasks:
        - name: Install and Configure cloudflared
          include_role:
            name: bendews.cloudflared
          vars:
          cloudflared_allow_firewall: false
          cloudflared_enable_service: false
          cloudflared_port: 5053


# TODO:

- None

# License

MIT

# Author Information

Created in 2018 by [Ben Dews](https://bendews.com)
