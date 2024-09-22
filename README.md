# oracle-physical-standby-ansible
Physical standby database creation using Oracle's RMAN Active duplicate and Ansible. </br>
(Note: The code is tested for 19c database)

<b>Source</b>: Non-RAC/Standalone database server with ASM <br/>
<b>Target</b> : Non-RAC/Standalone database server with ASM

<h2>REQUIREMENTS</h2>
 1. Fill out vars.yml with appropriate values <br/>
 2. Copy the ansible scripts to standby database server node and run ansible-playbook from there
 <br/>
 <br/>
To enable dataguard configs on primary database, run below playbook

````
ansible-playbook -i inventory/hosts primary_db_dg_enable.yml --extra-vars hosts="<primary_db_server_name>"  --ask-pass --ask-become-pass
````

To create Oracle dataguard/physical standby database for Non-RAC-Non-RAC setup , run below playbook </br>
Note: All the Ansible tasks are idempotent, except the last task (task: RMAN duplicate)

````
ansible-playbook configure_standbydb.yml --ask-pass --ask-become-pass
````
