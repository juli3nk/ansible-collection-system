Network
=======

Manage host network backend selection and service state.

This role focuses on the network stack backend:

- `networkmanager`
- `systemd-networkd`
- `static` (disable both managed backends)

DNS resolver behavior should stay in the dedicated `dns` role.
`network_interfaces` is currently applied for `systemd-networkd` backend.

Role variables
--------------

- `network_backend`: Backend to apply (`networkmanager`, `systemd-networkd`, `static`).
  Defaults to `systemd-networkd` for server-oriented usage.
- `network_manage_packages`: Install/remove backend packages.
- `network_manage_services`: Enable/start or disable/stop backend services.
- `network_interfaces`: High-level interface map (NixOS-like) used to auto-generate `.network` files for `systemd-networkd`.
- `network_networkd_units`: Optional low-level `.network` units appended after auto-generated units.

Example Playbook
----------------

    network_backend: systemd-networkd
    network_interfaces:
      enp1s0:
        dhcp: true
        address: null
        aliases: []
        gateway: null

License
-------

MIT
