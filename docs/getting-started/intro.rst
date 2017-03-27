Introduction
============

The purpose of this lab is to give you more visibility on 

* Overview of Mesos and Marathon and their key components
* Install Mesos and Marathon with 3 masters and 2 agents
* How to launch application from Marathon
* How to install Mesos-DNS for service discovery
* How to setup and install F5 solutions for Mesos / Marathon environment

The F5 Marathon Container Integration consists of the F5 Marathon BIG-IP Controller, the F5 Application Service Proxy (ASP), and the F5 Marathon ASP Controller.

The F5 Marathon BIG-IP Controller configures a BIG-IP to expose applications in a Mesos cluster as BIG-IP virtual servers, serving North-South traffic.

The F5 Application Service Proxy provides load balancing and telemetry for containerized applications, serving East-West traffic. The F5 Marathon ASP Controller deploys ASP instances ‘on-demand’ for Marathon Applications. 

The official F5 documentation is available here: `F5 Mesos Marathon Integration <http://clouddocs.f5.com/containers/v1/marathon/>`_

We consider that you have a valid UDF access to do this lab. If not, you may review the pre-requisites about our lab setup .

Some ansible playbooks are provided also to do the same deployment in an automated way (standalone - allinone deployment, cluster deployment): :ref:`install_setup_ansible`