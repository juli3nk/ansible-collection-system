uv
==

Install [uv](https://github.com/astral-sh/uv) for specific Linux users via the official install script.

The target users must already exist and should be managed by the `identity` role.

Role variables
--------------

- `uv_users`: List of usernames to install uv for (`~/.local/bin/uv`).
- `uv_install_script_url`: Official installer URL (default Astral script).
- `uv_binary_relative_path`: Relative path from user home to uv binary.
- `uv_force_install`: Remove and reinstall uv when `true`.
- `uv_prerequisite_packages`: Packages required before install (`curl`, `ca-certificates`); validated only, installed by `package` role.
- `uv_cmd_user`: Username used to publish host fact `uv_cmd` for downstream roles.

Facts
-----

- `uv_cmd_by_user`: Map of username to uv binary path.
- `uv_cmd`: Set when `uv_cmd_user` is defined, or when exactly one entry exists in `uv_users`.

Example Playbook
----------------

    uv_users:
      - hermes
    uv_cmd_user: hermes

    shell_user_path_prepend:
      hermes:
        - /home/hermes/.local/bin

License
-------

MIT
