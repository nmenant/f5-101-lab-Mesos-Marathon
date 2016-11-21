Test your setup
===============

Launch a command
----------------

Connect to Marathon through one of the master (:8080) and launch an application

1.	Click on *create application*
2.	ID: Test
	CPU: 0.1
	Memory : 32M
	Command: echo Test; sleep 10
3.	Start your application

Once it runs, if you connect to the mesos framework, you should see more and more completed tasks. Name of the task should be "Test" (our ID). 

Go Back to MArathon, click on our application *test* and click on the setting button and select *destroy* to remove it. 


Launch a container
------------------

To test our containers from marathon, click on create an application, switch to JSON mode and use the following to start an apache in a container (this may takes some time since we will have to retrieve first the image)

::

{
  "id": "my-website",
  "cpus": 0.5,
  "mem": 32.0,
  "container": {
    "type": "DOCKER",
    "docker": {
      "image": "eboraas/apache-php",
      "network": "BRIDGE",
      "portMappings": [
        { "containerPort": 80, "hostPort": 0 }
      ]
    }
  }
}


Then check the port used by the container and try to access it (slave IP:port)

