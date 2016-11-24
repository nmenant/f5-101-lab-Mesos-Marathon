Install and Setup Ansible
=========================

Install Ansible
---------------

You can use the following command on one of the node to install Ansible. We will use master1 for example

Connect to master1 and run the following commands:

::

	sudo apt-add-repository ppa:ansible/ansible -y
	
	sudo apt-get update && sudo apt-get install ansible -y



Setup Ansible
-------------

Enable the following option in /etc/ansible/

::

	inventory      = /etc/ansible/hosts

	become_user=root

Example of /etc/ansible/hosts

::

	[masters]
	master1.my-lab zoo_myid=1
	master2.my-lab zoo_myid=2
	master3.my-lab zoo_myid=3

	[slaves]
	slave1.my-lab
	slave2.my-lab

	[marathon]
	master1.my-lab
	master2.my-lab
	master3.my-lab

	[local]
	localhost


	Test Ansible
	------------


