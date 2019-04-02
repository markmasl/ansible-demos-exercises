This playbook (web_and_db_servers_playbook.yml) spins up a pair of web servers and a mysql db server in the GCP infrustructure.

In order to run this playbook following changes where made to the ansible.cfg file:
1. path to the inventory was changed
inventory = ~/ansible-demos-exercises/gcp-ansible/inventory/
2. additional paths to search for roles in
roles_path = /etc/ansible/roles:/usr/share/ansible/roles:~/ansible-demos-exercises/gcp-ansible/roles
3. private_key_file = ~/.ssh/id_rsa
4. vault_password_file = ~/ansible-demos-exercises/gcp-ansible/.vault_pass
5. Additional plugins required for dynamic inventory
enable_plugins = host_list, script, yaml, ini, gcp_compute


In order to be able connect to the GCP instances you have to enable OS-loging. Please follow this documentation:
https://cloud.google.com/compute/docs/instances/managing-instance-access#configure_users

This playbook does following:
1. Spins up 3 servers: webserver01, webserver02, dbserver01
2. Setting up LB with two webservers in the backend
3. Setting up FW rule that allows connection only on port 80
4. Setting up WEB servers with python and all requred packages.
5. Setting up DB server with MYSQL installed.
6. Applying web application configs for DB server and for WEB servers 

Application uses following roles:
- gcp
- andrewrothstein.flask
- geerlingguy.mysql
- flaskapp

In order to test application, you have to go to LB's IP address: http://X.X.X.X , and then push "Sign up today" button. You should be forwarded to new page http://X.X.X.X/showSignUp. This is page where you can try to sign up. All entered data will be sent to MySQL database. In order to verify that data was sent you have to open browser debug mode (console) where you should see message: {"message": "User created successfully !"}. If you will try to submit same data again, a new message will apear, stating: {"error": "(u'Username Exists !!',)"}
