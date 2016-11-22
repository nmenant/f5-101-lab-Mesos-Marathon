Mesos Setup
===========

On **each master** we need to setup the following files with the relevant information: 

* /etc/mesos-master/ip 
* /etc/mesos-master/hostname
* /etc/mesos/zk (to have zookeeper handle HA for mesos)

::

	# On master1
	printf "10.1.10.1" | sudo tee /etc/mesos-master/ip
	printf "master1.my-lab" | sudo tee /etc/mesos-master/hostname
	printf "zk://10.1.10.1:2181,10.1.10.2:2181,10.1.10.3:2181/mesos" | sudo tee /etc/mesos/zk

	# On master2
	printf "10.1.10.2" | sudo tee /etc/mesos-master/ip
	printf "master1.my-lab" | sudo tee /etc/mesos-master/hostname
	printf "zk://10.1.10.1:2181,10.1.10.2:2181,10.1.10.3:2181/mesos" | sudo tee /etc/mesos/zk

	# On master3
	printf "10.1.10.3" | sudo tee /etc/mesos-master/ip
	printf "master1.my-lab" | sudo tee /etc/mesos-master/hostname
	printf "zk://10.1.10.1:2181,10.1.10.2:2181,10.1.10.3:2181/mesos" | sudo tee /etc/mesos/zk

