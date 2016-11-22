Setup Zookeeper
===============

We need to point our agent to our 3 master instances. This is how the agent(s) will find the master(s). This is done via the file /etc/mesos/zk

2181 is zookeeper's default port. 

Do this on **all your agents**

::

	printf "zk://10.1.10.1:2181,10.1.10.2:2181,10.1.10.3:2181/mesos" | sudo tee /etc/mesos/zk

	

