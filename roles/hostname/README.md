Hostname
========

Manage system hostname and optional `/etc/hosts` hostname mapping.

Example Playbook
----------------

    hostname_name: "server01"
    hostname_fqdn: "server01.home.arpa"
    hostname_manage_etc_hosts: true
    hostname_hosts_ip: "127.0.1.1"
    hostname_hosts_aliases:
      - "server01.local"
    hostname_hosts_extra_entries:
      - ip: "192.168.1.10"
        names:
          - "nas.home.arpa"
          - "nas"
      - ip: "192.168.1.11"
        names:
          - "git.home.arpa"
          - "git"

License
-------

MIT
