Auteur : Abdel-had HANAMI

Contexte : Bootcamp DevOps - promotion 12

Centre de formation : eazytraining.fr

Date de publication : le 10 Octobre 2023

LinkedIn : https://www.linkedin.com/in/abdel-had-hanami/

----------

# Environnement d'execution ansible pour le projet [ansible-role-containerized-apache](https://github.com/Abdel-had/ansible-training)

## Présentation

Ce projet Ansible vise à déployer un serveur Apache dans un environnement conteneurisé sur une ou plusieurs machines cibles. Il est structuré de manière à faciliter son utilisation et sa compréhension, suivant les bonnes pratiques de gestion de configuration avec Ansible.

## Structure du Projet

```
mini-projet-ansible-role-containerized-apache/
├── etc/             
│   └── hosts        # Fichier contenant le mappage IP-hostname des clients
├── vagrant/        
│   ├── Vagrantfile  # Fichier de configuration Vagrant
│   └── install_ansible.sh # Script d'installation d'Ansible
├── ansible.cfg      # Fichier de configuration Ansible
├── files/           
│   ├── secrets/
│   │   └── credentials.yml # Fichier chiffré contenant les identifiants
├── inventory/       
│   ├── group_vars/  
│   │   └── prod.yml  # Variables spécifiques à l'environnement de production
│   ├── host_vars/   
│   │   ├── client1.yml # Variables spécifiques au client1
│   │   └── client2.yml # Variables spécifiques au client2
│   └── hosts.yml        # Fichier d'inventaire Ansible
├── roles/           
│   └── requirements.yml  # Fichier de spécification des rôles requis
├── playbooks/      
│   └── apache.yml        # Playbook pour le déploiement d'Apache
└── README.md             # Documentation du projet
```

## Configuration Préliminaire

1. **Environnement Vagrant** : 
   - Assurez-vous d'avoir [Vagrant](https://www.vagrantup.com/) et [Virtualbox](https://www.virtualbox.org/) installés sur votre machine.
   - Exécutez `vagrant up` dans le dossier `vagrant/` pour démarrer les machines virtuelles et installer Ansible.

2. **Configuration Ansible** :
   - Le fichier `ansible.cfg` contient la configuration globale d'Ansible pour ce projet.
   - L'inventaire est spécifié dans le fichier `inventory/hosts.yml`.

3. **Variables** :
   - Les variables globales pour l'environnement de production sont définies dans `inventory/group_vars/prod.yml`.
   - Les variables spécifiques aux hôtes sont définies dans les fichiers sous `inventory/host_vars/`.

4. **Credentials** :
   - Les credentials sont stockés de manière sécurisée dans `files/secrets/credentials.yml` en utilisant Ansible Vault.

## Installation du Rôle

Avant de déployer le playbook, il est nécessaire de télécharger et d'installer le rôle `ansible-role-containerized-apache` à partir de GitHub. Vous pouvez le faire avec la commande `ansible-galaxy` comme suit :

```bash
ansible-galaxy install -r roles/requirements.yml
```

Cette commande lira le fichier `roles/requirements.yml`, téléchargera et installera le rôle `ansible-role-containerized-apache` dans le répertoire `roles/` de votre projet.

Assurez-vous que vous avez exécuté cette commande à partir du répertoire racine du projet `mini-projet-ansible-role-containerized-apache/` pour garantir que le rôle est installé au bon endroit.

---

Avec cette addition, votre projet sera prêt à déployer Apache sur les machines cibles spécifiées dans votre inventaire. Assurez-vous de revoir et d'ajuster les variables et les configurations selon vos besoins avant d'exécuter le playbook.
## Déploiement

Pour déployer le serveur Apache conteneurisé, exécutez le playbook `apache.yml` avec la commande suivante :

```bash
ansible-playbook playbooks/apache.yml
```

## Rôles

Les rôles requis pour ce projet sont spécifiés dans le fichier `roles/requirements.yml`. Le rôle `ansible-role-containerized-apache` est hébergé sur GitHub et sera téléchargé et installé automatiquement lors de l'exécution du playbook.
