Masters setup
============

We will setup the following 3 masters: 

==================   ============
Master                   IP 
==================   ============
Master 1               10.1.10.1
Master 2               10.1.10.2
Master 3               10.1.10.3
==================   ============

Access your windows 10 jumpbox and launch putty to access your master via ssh 

.. image: ../images/Launch_putty.png
   :align: center
   :scale: 50%

It may be best to open 3 putty session, one for each master. You'll have to run several commands on each of them. Here are the credentials to authenticate on the master: 

::
   login: student
   password: student

On each master, run the following commands: 

::
    sudo yum -y update

This command will update the master to have the latest packages. It may takes some time. 

::
   We already disabled firewalld on all Masters and Agents. Dockers and firewalld are not working well together at this time. 
   we disabled/removed firewalld with the following command
   sudo systemctl stop firewalld && sudo systemctl disable firewalld


