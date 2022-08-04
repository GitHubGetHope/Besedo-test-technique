# Besedo test technique

There are 3 playbook files :
 - [users-playbook.yml](./users-playbook.yml) : contains a block of tasks to create users based on the `user_accounts.yml` file with `tags=users`, then a task to limit system open file.
 - [docker-playbook.yml](./docker-playbook.yml) : contains tasks to install `docker` and to run container `ansible_happy_roentgen`.
 - [playbook.yml](./playbook.yml) : contains all other tasks . To install nginx, I used the role : [nginxinc/ansible-role-nginx](https://github.com/nginxinc/ansible-role-nginx)
 
## How to use the playbooks ? 
There is two ways to test our playbooks with `Vagrant` : We can create a vm and launch it with `Vagrant` and then play 
```
ansible-playbook -i inventory playbook.yml
``` 
command with iventory contains ip adress of the VM, and you will need ssh certificate. 

The other way is to use `Vagrantfile`. I add an Ansible provision configuration to [Vagrantfile](./ansible/Vagrantfile)  to test the users playbook, you can add more Ansible configurations and options [Vagrant Doc](https://www.vagrantup.com/docs/provisioning/ansible#options). All you have to do after, is to run 
```
Vagrant provision
```
command to test the playbook.
