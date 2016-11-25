Welcome to 101 Lab Mesos Marathon's documentation!
==================================================

Introduction
============

The purpose of this lab is to give you more visibility on 

* Overview of Mesos and Marathon and their key components
* Install Mesos and Marathon with 3 masters and 2 agents
* How to launch application from Marathon
* How to install Mesos-DNS for service discovery

If you need just to have a Mesos/Marathon env, you can use the ansible playbooks to do the job. 

We consider that you have a valid UDF access to do this lab. If not, you may review the pre-requisites about our lab setup .

Contents:


.. toctree::
   :maxdepth: 3
   :caption: Getting Started

   getting-started/intro.rst
   getting-started/getting-started.rst

.. toctree::
   :maxdepth: 3
   :caption: Your lab

   your-lab/lab-setup.rst
   your-lab/access-udf.rst  

.. toctree::
   :maxdepth: 3
   :caption: Setup the masters

   setup-masters/install-mesos-marathon.rst
   setup-masters/setup-zookeeper-master.rst
   setup-masters/setup-mesos-master.rst
   setup-masters/setup-marathon.rst
   setup-masters/start-services-master.rst

.. toctree::
   :maxdepth: 3
   :caption: Setup the agents

   setup-agents/install-mesos-agent.rst
   setup-agents/setup-zookeeper-agent.rst
   setup-agents/setup-mesos-agent.rst
   setup-agents/start-services-agent.rst
   setup-agents/test-setup.rst

.. toctree::
   :maxdepth: 3
   :caption: Setup Mesos DNS

   setup-mesos-dns/setup-mesos-dns.rst
   setup-mesos-dns/test-mesos-dns.rst

.. toctree::
   :maxdepth: 3
   :caption: Use Ansible

   ansible/ansible-install-setup.rst
   ansible/ansible-install-playbooks.rst
   ansible/ansible-playbook-settings.rst
 
Indices and tables
==================

* :ref:`genindex`
* :ref:`modindex`
* :ref:`search`

