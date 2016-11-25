Install and Setup Ansible
=========================

The first thing to do is to connect to master1. You can see how to access your environment :ref:`access_udf`



.. warning::

	Install and setup have already been done. 

	* In the cluster blueprint, it has been done on master1. 
	* IN the standalone blueprint, it has been done on the mesos node

	The section below is for your information. You may go straight here :ref:`install_playbooks`


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

regarding the variables assignement: the strings after each hostname create specific variables related to this host only:

* zoo_myid is used to specify a variable value for each host when ansible runs a playbook against this node

* mesos_interface is used to specify which local interface/IP should be used for the mesos installation


/etc/ansible/hosts file (you need to be sudo to manage this file) for the cluster mode

::

	[masters]
	master1.my-lab zoo_myid=1 mesos_interface=10.1.10.1
	master2.my-lab zoo_myid=2 mesos_interface=10.1.10.2
	master3.my-lab zoo_myid=3 mesos_interface=10.1.10.3

	[slaves]
	slave1.my-lab mesos_interface=10.1.20.51
	slave2.my-lab mesos_interface=10.1.20.52

	[marathon]
	master1.my-lab
	master2.my-lab
	master3.my-lab

	[local]
	localhost


/etc/ansible/hosts file for the standalone mode

::

	[standalone]
	mesos mesos_interface=10.1.10.1


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





