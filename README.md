Role Name
=========

A role to backup remote data using age encrypted tarballs. It can conveniently use your authorized SSH public keys in the remote host as encrytion keys.

Requirements
------------

* [age](https://github.com/FiloSottile/age) encryption tool must be installed in the host running the playbook.


Role Variables
--------------

A description of the settable variables for this role should go here, including any variables that are in defaults/main.yml, vars/main.yml, and any variables that can/should be set via parameters to the role. Any variables that are read from other roles and/or the global scope (ie. hostvars, group vars, etc.) should be mentioned here as well.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: username.rolename, x: 42 }

License
-------

Apache License 2.0
