Disk
=========

Partition new disk.

Example Playbook
----------------

    disk_additional_devices:
        - match_size: '50G'
            device: 'notfound'
            part_number: 1
            part_label: 'gpt'
            fs_type: 'ext4'
            fs_opts: '-L app'

License
-------

MIT
