Setup Zookeeper
===============

We need to point zookeeper to our 3 master instances. This is done in the file /etc/mesos/zk

2181 is zookeeper's default port. 

::

	echo "zk://10.1.10.1:2181,10.1.10.2:2181,10.1.10.3:2181/mesos" | sudo tee /etc/mesos/zk

	

