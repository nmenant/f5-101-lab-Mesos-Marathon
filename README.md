#Introduction to Mesos and Marathon

The purpose of this lab is to give you more visibility on

* Overview of Mesos and Marathon and their key components
* Install Mesos and Marathon with 3 masters and 2 agents
* How to launch application from Marathon
* How to install Mesos-DNS for service discovery
* How to setup and install F5 solutions for Mesos / Marathon environment

The F5 Marathon Container Integration consists of the F5 Marathon BIG-IP Controller, the F5 Application Service Proxy (ASP), and the F5 Marathon ASP Controller.

The F5 Marathon BIG-IP Controller configures a BIG-IP to expose applications in a Mesos cluster as BIG-IP virtual servers, serving North-South traffic.

The F5 Application Service Proxy provides load balancing and telemetry for containerized applications, serving East-West traffic. The F5 Marathon ASP Controller deploys ASP instances ‘on-demand’ for Marathon Applications. 

The official F5 documentation is available here: http://clouddocs.f5.com/containers/v1/marathon/

We consider that you have a valid UDF access (Private Cloud of F5 Networks) to do this lab. If not, you may review the pre-requisites about our lab setup .

The lab guide is hosted here: http://101-lab-mesos-marathon.readthedocs.io/

We also provide some ansible playbooks if you need to setup a Mesos/Marathon env.

We consider that you have a valid UDF access to do this lab. If not, you may review the pre-requisites about our lab setup and howto to build your own