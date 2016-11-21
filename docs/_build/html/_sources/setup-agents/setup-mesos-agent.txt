Setup Mesos
===========

Configure Mesos
---------------

We need to provide IP / hostname information to the mesos slave system (as we did for mesos master)

On each agent:

::

	#On slave1: 
	echo "10.1.10.51" | sudo tee /etc/mesos-slave/ip
	echo "slave1.my-lab" | sudo tee /etc/mesos-slave/hostname

	#On slave2:
	echo "10.1.10.52" | sudo tee /etc/mesos-slave/ip
	echo "slave2.my-lab" | sudo tee /etc/mesos-slave/hostname

Install and setup docker
------------------------
We have to install docker-engine on the agents to be able to run docker containers

on *each agent*, do the following:

::

	sudo apt-key adv --keyserver hkp://ha.pool.sks-keyservers.net:80 --recv-keys 58118E89F3A912897C070ADBF76221572C52609D

	echo "deb https://apt.dockerproject.org/repo ubuntu-xenial main" | sudo tee /etc/apt/sources.list.d/docker.list

	sudo apt-get update


	#For Ubuntu Trusty, Wily, and Xenial, it’s recommended to install the linux-image-extra-* kernel packages. The linux-image-extra-* packages allows you use the aufs storage driver.

	sudo apt-get install -y linux-image-extra-$(uname -r) linux-image-extra-virtual

	sudo apt-get install -y docker-engine


Once this is done, docker should be up and running already. 

To test that it was launched successfully, you may use the command

::
	
	sudo docker run hello-world

This will download a test image automatically and launch it. You should have things appearing on your terminal. Once it is done, the container will stop automatically (you can validate this with the command sudo docker ps –a)

We need to allow mesos and docker containers in mesos: 

::

	echo 'docker,mesos' | sudo tee /etc/mesos-slave/containerizers

	#Increase the timeout to 10 min so that we have enough time to download any needed docker image
	echo '10mins' | sudo tee /etc/mesos-slave/executor_registration_timeout
