# Simple ROS in docker example

This is a simple example of how a ROS package may be built in docker, and how to run a collection of nodes in docker.

## Prerequisites

* [docker](https://www.docker.com/community-edition)
* [docker-compose](https://docs.docker.com/compose/install/)

## 1. Building our package

The catkin_ws folder contains what could have been your personal catkin workspace. We will use the beginner_tutorials package as an example.
The package is similar to any other ROS package, but note the Dockerfile. The dockerfile will copy the code from the beginner_tutorials folder and build it.
For a more in-depth explanation read the comments in the dockerfile.

In the beginner_tutorials folder, run the following:

```bash
docker build . --tag "my-beginner-tutorial"
```

This will build the docker image. That's it!

## 2. Running a collection of nodes

To run a collection of nodes we will use docker-compose. Docker-compose allows us to define a network of docker containers through docker-compose.yaml.
The given docker-compose.yaml file will start a listener node, a talker node, and the ROS master node.

To run the example run the following in the root folder:

```bash
docker-compose up
```

This will start the three nodes and you should see the listener and talker communicating.
To stop the example just hit CTRL+C.

For more information on how this works look inside the docker-compose.yaml file.

## Where to continue

Now that you have completed this example I recommend trying to make this work for a package of your own.
Try fiddling around with the docker-compose.yaml file and run other examples, renaming services and see what works or doesn't.

Further on, the ROS' docker repository contains a useful readme. <https://hub.docker.com/_/ros/>

## Credits

All code in the catkin_ws folder, except the Dockerfile and docker_entry_script.sh is from <https://github.com/ros/catkin_tutorials>