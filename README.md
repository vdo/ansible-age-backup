Role Name
=========

A role to backup remote files using [age](https://github.com/FiloSottile/age) encrypted tarballs, using user's SSH keys from GitHub.

Requirements
------------

* [age](https://github.com/FiloSottile/age) encryption tool must be installed in the host running the playbook.

How this role works
-------------------

* Creates one or more tarballs of the paths defined in `remote_backup_paths`.
* Downloads the tarballs locally to a temporary path.
* Encrypts the tarballs combining the all the SSH keys of all Github users, using the URI https://github.com/{user}.keys
* Deletes safely any unencrypted file left behind, using `shred`.

The generated files will follow the pattern: `{ hostname }_{ path }_{ random string }.tgz.age`, converting any dots, slashes and asterisks, for example: `www_example_net__var_log_dmesg@_bxhlndi5.tgz.age` would be the backup of `/var/log/dmesg*` at`www.example.net`.

Role Variables
--------------
|Variable|Description|Default Value
|---|---|---|
|`remote_backup_paths`| Paths on the remote host(s) to generate the backups from (required) | []
|`github_users`|Github usernames to fetch SSH keys used to encrypt (required)| []
|`remote_backup_temp_path`|Path in the remote host(s) to store the temporal tarballs |`/tmp`
|`local_backup_temp_path`|Path in the localhost to store the temporal tarballs |`/tmp`
|`local_backup_destination`|Destination path of the encrypted backups |`./`

Example Playbook
----------------

```yaml
---
- hosts: all
  become: true
  vars:
    remote_backup_paths:
      - "/var/log/auth*"
      - "/etc/ssl/certs/"
    github_users:
      - "vdo"
      - "ahasna"
  roles:
    - vdo.age-backup
```

License
-------
Apache License 2.0
