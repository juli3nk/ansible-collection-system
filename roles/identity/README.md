Identity
=========

Manage identity.

Notes
-----

- `password_from_username: true` sets an initial password based on username (hashed).
- `password_force_change: true` forces password change at first login.
- When `password_from_username: true`, first-login password change is automatically enforced.
- Users with `admin: true` automatically trigger creation of `identity_admin_group_name` when `identity_manage_admin_group: true`.

Example Playbook
----------------

    identity_gitrepo_provider: 'gitlab'
    identity_gitrepo_url: 'https://gitlab.example.com'

    identity_users:
        - name: 'ubuntu'
            create: false
            ssh: true
            admin: true
        - name: 'ops'
            create: true
            ssh: true
            admin: true
            authorized:
                - gitrepo_username: 'user1'
                - gitrepo_username: 'user2'

License
-------

MIT
