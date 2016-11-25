Install and Setup Ansible
=========================

The first thing to do is to connect to master1. You can see how to access your environment :ref:`access_udf`



.. warning::

	Install and setup have already been done on master1. So this is for your information. You may go straight here :ref:`install_playbooks`


Install Ansible
---------------

You can use the following commands to install Ansible. 

Connect to master1 and run the following commands:

::

	sudo apt-get update -y

	sudo apt-get install -y software-properties-common
	
	sudo apt-add-repository ppa:ansible/ansible -y
	
	sudo apt-get update && sudo apt-get install ansible -y



Setup Ansible
-------------

Enable the following options in /etc/ansible/ (you need to use sudo)


* inventory: specify which file contains the nodes available to ansible
* become_user: allow to specify which user we impersonate when using become
* host_key_checking: means that we bypass the security host check when connecting via ssh

::

	inventory      = /etc/ansible/hosts

	become_user=root

	host_key_checking = False


/etc/ansible/hosts is used to list the nodes that are available to ansible. You can group them. In the example below, we created 3 different groups: 

* masters: nodes to be setup with Mesos and the Zookeeper services
* slaves: nodes to be setup with Mesos as agents/slaves
* marathon: nodes to be setup with Marathon
* local: to run specific command on the Ansible controller

zoo_myid is used to specify a variable value for each host when ansible runs a playbook against this node

Example of /etc/ansible/hosts (you need to be sudo to manage this file)

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

We can test that ansible and the hosts file are setup properly by running a command against all hosts: 

::

	ansible all -a "hostname"

This will run the hostname command on all nodes. 

You should have an output like this: 

.. image:: ../images/ansible-test-setup.png
	:align: center
	:scale: 50%





