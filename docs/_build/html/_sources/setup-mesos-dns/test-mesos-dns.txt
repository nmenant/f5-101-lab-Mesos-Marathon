Test Mesos DNS
==============

to test our Mesos DNS setup, we will start a new application and check if it automatically gets a DNS name. 

Start a new app in marathon: 

::

{
  "id": "test",
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

Once it's running, go to one of your slaves and run ping test.marathon.mesos. It should work
