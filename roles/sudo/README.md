Sudo
=========

Manage sudoers file.

Role variables
--------------

- `sudo_manage_cloud_init_rule`: remove cloud-init sudoers rule.
- `sudo_manage_admin_group_rule`: manage group-based sudoers rule.
- `sudo_admin_group_name`: group used by group-based sudoers rule.
- `sudo_automation_user`: automation account name used for bootstrap safety rule.
- `sudo_manage_automation_user_rule`: manage dedicated sudoers rule for automation user.
- `sudo_cleanup_automation_user_rule`: remove automation sudoers rule when set to `true`.
- `sudo_require_automation_user_in_admin_group`: require automation user in admin group before cloud-init sudoers removal (only relevant when dedicated automation rule is disabled).
- `sudo_timestamp_timeout`: sudo timeout value; set to `null` to disable timeout file.
- Cloud-init sudoers removal is skipped automatically if current session cannot run `sudo -n` yet (common right after group membership changes). Re-run after reconnect.

License
-------

MIT
