# ansible-ksw-01
## Status: alpha ( not finished )


Title : Ansible playbooks to generate a 3 server grid
=====================================================

These playbooks will install and manage a three server opensimulator grid.
Servers:
  1) the grid server running the robust login service and the grid services
  2) the asset server, running the robust asset and inventory services
  3) the region server , running the simulator service

Requirements
------------

- This setup requires three Ubuntu servers with a minimal of 2 cpu's each
  and 4 Gb memory. The name of these servers are listed in the
  `infrastructure.cnf` file.
- The servers need to have python installed, and `/usr/bin/phython` available


Configuration
------------
- The grid is configured by setting the variables in `group_vars/all.yml`
- The asset server will run a mysql dKatabase. The database and the system
   account for the grid administrator are configured by setting the variables
   in `group_vars/robust/all.yml`
- The region server will run a mysql database to store simulator assets. The
  database and the system account for the region server administrator are
  configured by setting the variables in `group_vars/simulator/all.yml`    
- The passwords of the database are kept in a vault. You either generate a new
  vault for each group or define the vault_db_password variable in the groups_var
  file with the other variables. The location of the file containing the vault
  passphrase is configured in `ansible.cfg`

  Roles
  ------
- control  : install optional tools for the control host
- baseline : installs and configures packages common for all Servers
- mysql    : installs and configures mysql and the database as storage provider
             for opensim
- opensim  : install opensimulator from github and configures the opensimulator
             ini files


Playbook tags
----------------

Playbooks
----------
- site.yml    : runs the complete installation
- control.yml : configures the control system
- storage.yml : configures the storage providers
- opensim.yml : configures group specefic opensimulator services
- grid.yml    : configures opensimulator host specific services

playbooks/
-  stack_status.yml  : shows service status of all services in the opensim stack
-  stack_restart.yml : executes a controlled restart of the opensim stack

License
-------

BSD

Author Information
------------------
KaiShun Oleander

eMail  : kaishun@xs4all.nl

url    :http://www.kaishunworldz.com
Github : https://github.com/KaiShunOleander
