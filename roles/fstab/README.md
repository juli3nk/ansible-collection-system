Fstab
=========

Add entry to /etc/fstab file.

Example Playbook
----------------

    fstab_mounts:
        - src: 'LABEL=app'
            path: '/opt/app'
            fstype: 'ext4'
            opts: 'defaults,discard'
            state: mounted

License
-------

MIT
