Setup Mesos-DNS
===============

If you want to be able to do service discovery with Mesos/Marathon, you will need to install and setup mesos-dns. 

To leverage marathon for scalability and HA, we will launch Mesos-DNS in a docker container from Marathon

Do the following on **SLAVE1** (we force the docker image to start on slave1)

::

	sudo mkdir /etc/mesos-dns

Create a file in /etc/mesos-dns/ called config.json  

::

	sudo cat /etc/mesos-dns/config.json

.. code-block:: none

	{
        "zk": "zk://10.1.10.1:2181,10.1.10.2:2181,10.1.10.3:2181/mesos",
        "masters": ["10.1.10.1:5050", "10.1.10.2:5050", "10.1.10.3:5050"],
        "refreshSeconds": 60,
        "ttl": 60,
        "domain": "mesos",
        "port": 53,
        "resolvers": ["8.8.8.8"],
        "timeout": 5,
        "httpon": true,
        "dnson": true,
        "httpport": 8123,
        "externalon": true,
        "SOAMname": "ns1.mesos",
        "SOARname": "root.ns1.mesos",
        "SOARefresh": 60,
        "SOARetry": 600,
        "SOAExpire": 86400,
        "SOAMinttl": 60
	}


launch the mesos-dns image in marathon. Connect to marathon, click on *Create an application* and enable *json mode* 

.. code-block:: none

	{
		"args": [	
		"/mesos-dns",
		"-config=/config.json"
    	],
    	"container": {
		  "docker": {
		            "image": "mesosphere/mesos-dns",
		            "network": "HOST"
		    },
		    "type": "DOCKER",
		    "volumes": [
		    	{
				"containerPath": "/config.json", 
    	        "hostPath": "/etc/mesos-dns/config.json",
				"mode": "RO"
		         }
		       ] 
   		},
   		"cpus": 0.2,
		"id": "mesos-dns-docker",
		"instances": 1,
		"constraints": [["hostname", "CLUSTER", "slave1.my-lab"]]
	}	

Last thing is to update /etc/resolv.conf on **all slaves*: we add our mesos dns into our resolve.conf file

::

	sudo sed -i '1s/^/nameserver 10.1.20.51\n/' /etc/resolv.conf
