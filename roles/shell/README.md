Shell
=========

Manage shell.

Role variables
--------------

- `shell_prompt_enabled`: Enable or disable managed prompt script.
- `shell_prompt_state`: Prompt script desired state (`present` or `absent`).
- `shell_prompt_target_file`: Prompt script target path.
- `shell_global_path_prepend`: Global PATH entries to prepend via `/etc/profile.d`.
- `shell_global_path_target_file`: Path of managed global PATH profile snippet.
- `shell_manage_user_path`: Enable per-user PATH management.
- `shell_user_path_prepend`: Mapping of username to PATH entries to prepend.
- `shell_user_path_target_file`: Per-user shell file to manage (default `.profile`).
- `shell_manage_user_bashrc_template`: Enable per-user `.bashrc` template management.
- `shell_user_bashrc_template_users`: List of users that should receive managed `.bashrc`.
- `shell_user_bashrc_enable_colors_default`: Default color behavior in managed `.bashrc`.
- `shell_user_bashrc_enable_colors`: Per-user color toggle map for managed `.bashrc`.
- `shell_manage_user_bashrc_extras`: Enable per-user `.bashrc` extras management.
- `shell_user_bashrc_target_file`: Per-user bashrc file to manage (default `.bashrc`).
- `shell_user_bashrc_extras`: Mapping of username to list of managed bashrc blocks (`id`, `block`).
- `shell_ensure_user_runtime_dirs`: Ensure `/run/user/<uid>` exists for users in `shell_user_bashrc_extras`.
  The role can render `templates/bashrc.j2` (colors/aliases + prompt sourcing)
  and append user-specific extra blocks.

Example
-------

    shell_global_path_prepend:
      - /usr/local/sbin

    shell_user_path_prepend:
      openclaw:
        - /home/openclaw/.npm-global/bin

    shell_manage_user_bashrc_template: true
    shell_user_bashrc_template_users:
      - openclaw
    shell_user_bashrc_enable_colors:
      openclaw: true

    shell_manage_user_bashrc_extras: true
    shell_ensure_user_runtime_dirs: true
    shell_user_bashrc_extras:
      openclaw:
        - id: openclaw-env
          block: |
            export NODE_EXTRA_CA_CERTS=/usr/local/share/ca-certificates/kazmen-root.crt
            export XDG_RUNTIME_DIR=/run/user/$(id -u)
        - id: dbus
          block: |
            if [ -z "$DBUS_SESSION_BUS_ADDRESS" ]; then
              export DBUS_SESSION_BUS_ADDRESS="unix:path=${XDG_RUNTIME_DIR}/bus"
            fi

License
-------

MIT
