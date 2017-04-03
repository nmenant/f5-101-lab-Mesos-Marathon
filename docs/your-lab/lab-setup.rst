Lab Setup
==============

Here is the setup we will leverage to either create a new environment or to connect to an existing environment (F5 UDF)

In the existing environment, here is the setup you'll get: 

==================   ==================  =========================  ==============================================
    Hostname             AWS Mgt IP             Mesos Network                     Login / Password 
==================   ==================  =========================  ==============================================
    Master 1              10.1.1.4               10.1.10.11           ssh: ubuntu/<your key> - su : root/default 
    Master 2              10.1.1.5               10.1.10.12           ssh: ubuntu/<your key> - su : root/default 
    Master 3              10.1.1.6               10.1.10.13           ssh: ubuntu/<your key> - su : root/default 
    Agent  1              10.1.1.7               10.1.10.51           ssh: ubuntu/<your key> - su : root/default 
    Agent  2              10.1.1.8               10.1.10.52           ssh: ubuntu/<your key> - su : root/default  
 Windows Jumpbox          10.1.1.9               10.1.10.50                 administrator / ibKvT4w=Aa
    BIG-IP                10.1.1.10              10.1.10.60                      admin/admin
==================   ==================  =========================  ==============================================

In case you don't use UDF, here are a few things to know that could be useful (if you want to reproduce this in another environment)

Here are the different things to take into accounts during this installation guide: 

* We use Ubuntu xenial in this UDF blueprint
* We updated on all the nodes the /etc/hosts file so that each node is reachable via its name

::

	Example of our hosts file
	user@master1:~$ cat /etc/hosts
	127.0.0.1       localhost
	10.1.10.1       ip-10-1-1-4 master1 master1.my-lab
	10.1.10.2       ip-10-1-1-5 master2 master2.my-lab
	10.1.10.3       ip-10-1-1-6 master3 master3.my-lab
	10.1.10.51      ip-10-1-1-7 slave1 slave1.my-lab
	10.1.10.52      ip-10-1-1-8 slave2 slave2.my-lab


* On master1, we created some ssh keys for user that we copied on all the nodes. This way you can use master1 to connect to all nodes without authentication 
* we enabled user to do sudo commands without authentication (needed to use ansible with this user). This was done via the visudo command to specify that we allow passwordless sudo command for this user (here is a thread talking about how to do it: `visudo  <http://askubuntu.com/questions/504652/adding-nopasswd-in-etc-sudoers-doesnt-work/504666/>`_)






