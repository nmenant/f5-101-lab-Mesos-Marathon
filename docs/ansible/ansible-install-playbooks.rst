Install Mesos / Marathon
========================

We will use the following github repo to retrieve the needed ansible playbook: https://github.com/nmenant/101-lab-Mesos-Marathon 

We will install the playbooks on master1 but need to install git first. 

run this command to install git: 

::

	sudo apt-get install -y git


create a specific directory to clone the github repo:

::

	mkdir /home/user/github_repo

	cd /home/user/github_repo


clone the github repo:

::

	git clone https://github.com/nmenant/101-lab-Mesos-Marathon

	cd ansible/playbooks

to run the ansible playbooks and setup the environment as explained in the step by step guide:

::

	ansible-playbook site.yml --extra-vars "install_mode=cluster"



Right now, only cluster is supported. Work in progress to have a deployment on a single node. 
