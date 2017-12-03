Go to live! kata
==================================

## Requirements

You need vagrant and ansible 2.4 on the host machine.

## Istruction

First, check the variables in ansible/deploy.yml, then deploy a new machine with "vagrant up".

Run again the deploy with: "vagrant provision" or (at path level):

PYTHONUNBUFFERED=1 ANSIBLE_FORCE_COLOR=true ANSIBLE_HOST_KEY_CHECKING=false ANSIBLE_SSH_ARGS='-o UserKnownHostsFile=/dev/null -o IdentitiesOnly=yes -o ControlMaster=auto -o ControlPersist=60s' ansible-playbook --connection=ssh --timeout=30 --limit="default" --inventory-file=.vagrant/provisioners/ansible/inventory -v ansible/deploy.yml

Backup an installation with the playbook backup.yml, change the required vars (bk_dest in particular) and run:

PYTHONUNBUFFERED=1 ANSIBLE_FORCE_COLOR=true ANSIBLE_HOST_KEY_CHECKING=false ANSIBLE_SSH_ARGS='-o UserKnownHostsFile=/dev/null -o IdentitiesOnly=yes -o ControlMaster=auto -o ControlPersist=60s' ansible-playbook --connection=ssh --timeout=30 --limit="default" --inventory-file=.vagrant/provisioners/ansible/inventory -v ansible/backup.yml

## Details

The deploy playbook supports a clean wordpress installation with sources downloaded from wordpress.org, or a deploy of a backup (done with the playbook backup.yml or, manually, dumping and compressing the wordpress db in bz2 and compressing the wordpress main dir in bz2). It tries to be idempotent, if you want a destructive installation that overwrite wordpress files and db use force_installation: True.

You can install multiple wordpress sites in the same machine, just change wp_site_name before running the deploy of each site.

## Task

Contained in this repo, there are some instructions for a new application that will go live in the next month!

You will need to:

1. Fork this repository.

2. Automate the creation of the infrastructure and the setup of the application.

   You have only these instructions:

   2.1 It works on Ubuntu Linux 14.04 x64

   2.2 It's based on the last version of WordPress (it will be more useful if we can parameterize the version)

   2.3 You can choose Apache, Nginx or whatever you want

   For any other issues or question you will have to ask to the developers. In this case please ask us without problems :)

3. Once deployed, the application should be secure, fast and stable. Assume that the machine is running on the public Internet and should be hardened and locked down.

4. Make any assumptions that you need to. This is an opportunity to showcase your skills, so if you want to, implement the deployment process with any additional features, tools or techniques you'd like to.

5. We are evaluating solutions based on the architecture and quality of the deployment. Show us just how beautiful, clean and pragmatic your code can be.

6. Once your solution is ready, please send us the link of your project.
