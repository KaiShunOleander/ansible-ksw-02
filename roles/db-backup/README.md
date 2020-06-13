Role db-backup
==============

Schedules daily compressed full database backups.

Requirements
------------

Backup system available and listed with backup ports in `infrastructure.def`.

Role Variables
--------------



Dependencies
------------



Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    --- 
      - hosts:
          - robust
          - backup
        become: yes
        gather_facts: yes
        roles:
          - db-backup

License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
