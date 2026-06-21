Network
=======

Manage host network backend selection and service state.

This role focuses on the network stack backend:

- `networkmanager`
- `systemd-networkd`
- `static` (ifupdown via `/etc/network/interfaces`)

DNS resolver behavior should stay in the dedicated `dns` role.
`network_interfaces` and `network_bridges` are applied for the `systemd-networkd`
and `static` backends.

Role variables
--------------

- `network_backend`: Backend to apply (`networkmanager`, `systemd-networkd`, `static`).
  Defaults to `systemd-networkd` for server-oriented usage.
- `network_manage_packages`: Install backend-specific packages (`network-manager` or `ifupdown`).
- `network_manage_services`: Enable/start or disable/stop backend services.
- `network_enable_ipv6`: Enable IPv6 in generated systemd-networkd units.
- `network_interfaces`: Interface map used to generate network config. Keys may be exact names or patterns (`en*`).
- `network_bridges`: Bridge definitions (member interfaces, addresses, DHCP).
- `network_virtual_interface_patterns`: Interface name patterns left unmanaged (containers, veth).
- `network_debian_static_interfaces_path`: ifupdown interfaces file path (static backend, Debian).

Example Playbook
----------------

    network_backend: systemd-networkd
    network_enable_ipv6: false
    network_interfaces:
      enp1s0: {}
    network_bridges:
      br0:
        interfaces:
          - enp1s0
        dhcp: true
        aliases:
          - 192.168.1.200/24

License
-------

MIT
