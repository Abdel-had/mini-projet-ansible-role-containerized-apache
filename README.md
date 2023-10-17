Author: Abdel-had HANAMI

Context: Bootcamp DevOps training, 12th promotion

Training center: eazytraining.fr

Release date: 10th of October, 2023

LinkedIn: https://www.linkedin.com/in/abdel-had-hanami/

----------

# Ansible Execution Environment for the project [ansible-role-containerized-apache](https://github.com/Abdel-had/ansible-training)

## Overview

This Ansible project aims to deploy an Apache server in a containerized environment on one or more target machines. It is structured in a way to facilitate its use and understanding, following the best practices of configuration management with Ansible.

## Project Structure

```
mini-projet-ansible-role-containerized-apache/
├── etc/             
│   └── hosts        # File containing the IP-hostname mapping of clients
├── vagrant/        
│   ├── Vagrantfile  # Vagrant configuration file
│   └── install_ansible.sh # Ansible installation script
├── ansible.cfg      # Ansible configuration file
├── files/           
│   ├── secrets/
│   │   └── credentials.yml # Encrypted file containing credentials
├── inventory/       
│   ├── group_vars/  
│   │   └── prod.yml  # Variables specific to the production environment
│   ├── host_vars/   
│   │   ├── client1.yml # Variables specific to client1
│   │   └── client2.yml # Variables specific to client2
│   └── hosts.yml        # Ansible inventory file
├── roles/           
│   └── requirements.yml  # File specifying required roles
├── playbooks/      
│   └── apache.yml        # Playbook for deploying Apache
└── README.md             # Project documentation
```

## Preliminary Configuration

1. **Vagrant Environment** : 
   - Ensure you have [Vagrant](https://www.vagrantup.com/) and [Virtualbox](https://www.virtualbox.org/) installed on your machine.
   - Run `vagrant up` in the `vagrant/` directory to start the virtual machines and install Ansible.

2. **Ansible Configuration** :
   - The `ansible.cfg` file contains the global Ansible configuration for this project.
   - The inventory is specified in the `inventory/hosts.yml` file.

3. **Variables** :
   - Global variables for the production environment are defined in `inventory/group_vars/prod.yml`.
   - Host-specific variables are defined in the files under `inventory/host_vars/`.

4. **Credentials** :
   - Credentials are securely stored in `files/secrets/credentials.yml` using Ansible Vault.

## Role Installation

Before deploying the playbook, it is necessary to download and install the `ansible-role-containerized-apache` role from GitHub. You can do this with the `ansible-galaxy` command as follows:

```bash
ansible-galaxy install -r roles/requirements.yml
```

This command will read the `roles/requirements.yml` file, download, and install the `ansible-role-containerized-apache` role into the `roles/` directory of your project.

Ensure you have run this command from the root directory of the `mini-projet-ansible-role-containerized-apache/` project to ensure the role is installed in the correct location.

---

With this addition, your project will be ready to deploy Apache on the target machines specified in your inventory. Make sure to review and adjust the variables and configurations according to your needs before running the playbook.

## Deployment

To deploy the containerized Apache server, run the `apache.yml` playbook with the following command:

```bash
ansible-playbook playbooks/apache.yml
```

## Roles

The roles required for this project are specified in the `roles/requirements.yml` file. The `ansible-role-containerized-apache` role is hosted on GitHub and will be downloaded and installed automatically when running the playbook.
