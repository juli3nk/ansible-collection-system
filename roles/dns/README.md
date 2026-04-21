Dns
===

Manage DNS resolver behavior with 3 modes:

- `dhcp`: DNS is managed by DHCP/network stack
- `resolved`: DNS is managed by systemd-resolved
- `static`: a static `/etc/resolv.conf` is written

Example Playbook
----------------

    dns_mode: resolved
    dns_nameservers:
      - 192.168.1.1
    dns_fallback_servers:
      - 1.1.1.1
      - 1.0.0.1
    dns_domains:
      - local
    dns_enable_dnssec: false
    dns_enable_cache: true

License
-------

MIT
