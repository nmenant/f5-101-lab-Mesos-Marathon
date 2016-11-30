Lab Setup
==============

Here is the setup of our lab

==================   ====================  =========================
Agent                    Management IP         IP for APP Traffic
==================   ====================  =========================
Master 1                 10.1.10.1                    N/A
Master 2                 10.1.10.2                    N/A
Master 3                 10.1.10.3                    N/A
Agent  1                 10.1.10.51               10.1.20.51
Agent  2                 10.1.10.52               10.1.20.52
Win10 Jumpbox            10.1.10.50               10.1.20.50
==================   ====================  =========================

default user (for jumpbox, masters and agents):

* login: user
* password: user

In case you don't use UDF, here are a few things to know that could be useful (if you want to reproduce this in another environment)

Here are the different things to take into accounts during this installation guide: 

* We use Ubuntu xenial in this UDF blueprint
* We updated on all the nodes the /etc/hosts file so that each node is reachable via its name



::

	#masters host file
	user@master1:~$ cat /etc/hosts
	127.0.0.1       localhost
	10.1.10.1       master1 master1.my-lab
	10.1.10.2       master2 master2.my-lab
	10.1.10.3       master3 master3.my-lab
	10.1.10.51      slave1  slave1.my-lab
	10.1.10.52      slave2  slave2.my-lab

	#agents host file
	user@master1:~$ cat /etc/hosts
	127.0.0.1       localhost
	10.1.10.1       master1 master1.my-lab
	10.1.10.2       master2 master2.my-lab
	10.1.10.3       master3 master3.my-lab
	10.1.20.51      slave1  slave1.my-lab
	10.1.20.52      slave2  slave2.my-lab


* On master1, we created some ssh keys for user that we copied on all the nodes. This way you can use master1 to connect to all nodes without authentication 
* we enabled user to do sudo commands without authentication (needed to use ansible with this user). This was done via the visudo command to specify that we allow passwordless sudo command for this user (here is a thread talking about how to do it: `visudo  <http://askubuntu.com/questions/504652/adding-nopasswd-in-etc-sudoers-doesnt-work/504666/>`_)






