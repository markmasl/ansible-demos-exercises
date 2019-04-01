This playbook (web_and_db_servers_playbook.yml) spins up a pair of web servers and a mysql db server in the GCP infrustructure.

In order to run this playbook following changes where made to the ansible.cfg file:
1. path to the inventory was changed
inventory = ~/ansible-demos-exercises/gcp-ansible/inventory/
2. # additional paths to search for roles in, colon separated
roles_path = /etc/ansible/roles:/usr/share/ansible/roles:/~/ansible-demos-exercises/gcp-ansible/roles
3. private_key_file = ~/.ssh/id_rsa
4. vault_password_file = ~/ansible-demos-exercises/gcp-ansible/.vault_pass
5. Additional plugins required for dynamic inventory
enable_plugins = host_list, script, yaml, ini, gcp_compute
