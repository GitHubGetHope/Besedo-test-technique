## Overview

_Ansible_ – [docs.ansible.com](https://docs.ansible.com/ansible/latest/index.html)

Ansible is an IT automation tool. It can configure systems, deploy software, and orchestrate more advanced IT tasks such as continuous deployments or zero downtime rolling updates.

_Vagrant_ – [vagrantup.com](https://www.vagrantup.com/docs)

Vagrant is a tool for building and managing virtual machine environments in a single workflow. With an easy-to-use workflow and focus on automation, Vagrant lowers development environment setup time, increases production parity, and makes the "works on my machine" excuse a relic of the past.

## Action

Files included :

- [YAML – user_accounts.yml](./user_accounts.yml), this file contains variables to be used in the playbook.

- [Vagrantfile](./Vagrantfile), this is a Vagrantfile, it may be used to test your playbook.

Using `ansible` and the [yaml](./user_accounts.yml) data structure define the following tasks in a `playbook.yml` file :

- Change the system open file limit to `65536` for the `root` user.

- Create the users accounts contained in [yaml](./user_accounts.yml) data structure and then;
    - Users must be able to login with by their `login` using their `ssh_keys`
    - Users must be part of the mentionned `groups`.
    - An `info` file in their `/home/USER/info` must contain the following informations : `name`, `position` & `office`.

- Install the `docker` package and then
    - Run a given container : `public.ecr.aws/q0x2y8f9/nginx-demo` – default exposed port is `55000`
    - Name the container `ansible_happy_roentgen`

- Download and copy the following [file – prrtprrt.txt](https://gist.githubusercontent.com/slgevens/aa9a2fc52cb5fef8b41c1b11a8b7d3e3/raw/dc1e3e288967bd4818277e4688d1daf615225337/prrtprrt.txt)
    - In each users `home/USER/prrtprrt.txt`
    - Locally (on your computer) in the working directory `{{ playbook_dir }}/files/prrtprrt.txt`

- Encrypt sensitive data with `ansible-vault`
    - Modify the [yaml](./user_accounts.yml) file and encrypt each users `passwd`
    - __Provide the encryption key__

- Use an [Ansible role](https://docs.ansible.com/ansible/latest/user_guide/playbooks_reuse_roles.html) to install `nginx` and then
    - Use this role [geerlingguy/ansible-role-nginx](https://github.com/geerlingguy/ansible-role-nginx) or find a better one
    - Expose the port `80` FORWARDING REQUESTS to the container `ansible_happy_roentgen`

- Use `tags` and `block`
    - Each `block` should able to be called by its `tags`

## Evaluation

The candidate must send an archive or submit a private Github repository link (prefered) containing the playbook(s) and all files, plus a README giving the steps to use them.
