.. _install_playbooks:

Install Mesos / Marathon with Ansible
=====================================

We will use the following github repo to retrieve the needed ansible playbook: https://github.com/nmenant/101-lab-Mesos-Marathon 

We will install the playbooks on master1 but need to install git first. 

You need to use git to retrieve the repo. **It's already installed on master1 (Cluster UDF blueprint) and mesos node (Standalone UDF blueprint)**. If it's not already installed in your env, run this command to install git: 

::

	sudo apt-get install -y git


create a specific directory to clone the github repo (here we consider that your user is called "user"):

::

	mkdir /home/user/github_repo

	cd /home/user/github_repo


clone the github repo:

::

	git clone https://github.com/nmenant/101-lab-Mesos-Marathon

	cd 101-lab-Mesos-Marathon/ansible/playbooks

to run the ansible playbooks and setup the environment as explained in the step by step guide (cluster):

::

	ansible-playbook site.yml --extra-vars "install_mode=cluster"


if you want to deploy Mesos and Marathon in standalone:

::

	ansible-playbook site.yml --extra-vars "install_mode=standalone"


