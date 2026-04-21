Fail2ban
=========

Install and configure fail2ban to protect SSH and services.

Role variables
--------------

- `fail2ban_enabled`: Controls whether fail2ban is installed/configured (`true`) or removed (`false`).

Example Playbook
----------------

    fail2ban_bantime: 1h
    fail2ban_findtime: 10m
    fail2ban_maxretry: 5

License
-------

MIT
