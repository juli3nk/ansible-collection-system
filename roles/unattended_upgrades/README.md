Unattended Upgrades
===================

Install and configure Debian unattended_upgrades.

Role variables
--------------

- `unattended_upgrades_enabled`: Install/configure when `true`, remove when `false`.
- `unattended_upgrades_system_enabled`: Keep package/config installed but enable (`true`) or disable (`false`) unattended upgrade behavior.
- `unattended_upgrades_allowed_origins`: Allowed apt origins for unattended updates.
- `unattended_upgrades_auto_reboot`: Enable automatic reboot after unattended upgrades.
- `unattended_upgrades_auto_reboot_time`: Reboot time when auto reboot is enabled.

Example Playbook
----------------

    unattended_upgrades_enabled: true
    unattended_upgrades_system_enabled: false
    unattended_upgrades_auto_reboot: false

License
-------

MIT
