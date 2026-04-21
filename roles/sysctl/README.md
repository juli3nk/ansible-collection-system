Sysctl
======

Manage kernel parameters with sysctl.

Role variables
--------------

- `sysctl_config_file`: Destination file for managed sysctl settings.
- `sysctl_reload`: Reload sysctl settings with `sysctl --system` when config changes.
- `sysctl_settings_common`: Baseline sysctl settings shared by all hosts.
- `sysctl_settings_host`: Per-host sysctl overrides/additions (merged over common).
- `sysctl_settings`: Legacy single map kept for backward compatibility.

Example Playbook
----------------

    sysctl_settings_common:
      net.ipv4.tcp_syncookies: 1
      net.ipv4.conf.all.accept_redirects: 0

    sysctl_settings_host:
      net.ipv4.ip_forward: 1

License
-------

MIT
