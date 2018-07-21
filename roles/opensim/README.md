Role opensimulator
==================

opensimulator role
- configures the system accounts for opensimulator administration
(defaults are the gridadmin and regionadmin user).
- adds the accounts to the sudo group
- copies the public key of the ansible user account on the control system to the
  remote servers in order to allow for ssh access
- clones the opensimulator binaries from the designated github repo
- sets up links to the correct configuration and opensim binary folder
- configures the `robust-include/DataStorage-Provider.ini` files with
  the database user credentials

Requirements
------------



Role Variables
--------------
- git_bin : the git project containing the opensim binaries
- git_cnf : the configuration project for the opensimulator config architectures

- storage_provider : the ini source file for the storage provider credentials


Dependencies
------------
- git is installed ( done by the baseline role )


Example Playbook
----------------



License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
