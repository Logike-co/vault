#docker 

---
**INDEX**

- [[#Tutorials|Tutorials]]
- [[#Introduction|Introduction]]
- [[#Docker and Containerization|Docker and Containerization]]
- [[#Using Docker command|Using Docker command]]
	- [[#Using Docker command#Working with Docker Images|Working with Docker Images]]
	- [[#Using Docker command#Running a Docker Container|Running a Docker Container]]
		- [[#Running a Docker Container#Run into container shell:|Run into container shell:]]
	- [[#Using Docker command#List networks|List networks]]
		- [[#List networks#Remove a network|Remove a network]]

---

## Tutorials

* *[[How To Install Docker on Ubuntu 22.04]]
* *[[How To Install Docker Compose on Ubuntu 22.04]]

---

# Introduction

Docker simplifies the process of managing application processes in containers. While containers are similar to virtual machines in certain ways, they are more lightweight and resource-friendly. This allows developers to break down an application environment into multiple isolated services.

For applications depending on several services, orchestrating all the containers to start up, communicate, and shut down together can quickly become unwieldy. [Docker Compose](https://docs.docker.com/compose/) is a tool that allows you to run multi-container application environments based on definitions set in a YAML file. It uses service definitions to build fully customizable environments with multiple containers that can share networks and data volumes.

Containerization is the process of distributing and deploying applications in a portable and predictable way. It accomplishes this by packaging components and their dependencies into standardized, isolated, lightweight process environments called containers.  Many organizations are now interested in designing applications and services that can be easily deployed to distributed systems, allowing the system to scale easily and survive machine and application failures.  Docker, a containerization platform developed to simplify and standardize deployment in various environments, was largely instrumental in spurring the adoption of this style of service design and management.  A large amount of software has been created to build on this ecosystem of distributed container management.

## Docker and Containerization

Docker is the most common containerization software in use today. While other containerizing systems exist, Docker makes container creation and management simple and integrates with many open source projects.
![[container_ov.png]]
In this image, you can begin to see (in a simplified view) how containers relate to the host system. Containers isolate individual applications and use operating system resources that have been abstracted by Docker. In the exploded view on the right, we can see that containers can be built by “layering”, with multiple containers sharing underlying layers, decreasing resource usage.

Docker’s main advantages are:

-   **Lightweight resource utilization**: instead of virtualizing an entire operating system, containers isolate at the process level and use the host’s kernel.
-   **Portability**: all of the dependencies for a containerized application are bundled inside of the container, allowing it to run on any Docker host.
-   **Predictability**: The host does not care about what is running inside of the container and the container does not care about which host it is running on.  The interfaces are standardized and the interactions are predictable.

Typically, when designing an application or service to use Docker, it works best to break out functionality into individual containers, a design decision known as service-oriented architecture. This gives you the ability to easily scale or update components independently in the future. Having this flexibility is one of the many reasons that people are interested in Docker for development and deployment.

To find out more about containerizing applications with Docker, click [here](https://www.digitalocean.com/community/tutorials/the-docker-ecosystem-an-overview-of-containerization).

## Using Docker command

Using `docker` consists of passing it a chain of options and commands followed by arguments. The syntax takes this form:
```
docker [option] [command] [arguments]
```

To view all available subcommands, type:
```
docker
```

As of Docker version 20.10.14, the complete list of available subcommands includes:
```
Output  attach      Attach local standard input, output, and error streams to a running container
  build       Build an image from a Dockerfile
  commit      Create a new image from a container's changes
  cp          Copy files/folders between a container and the local filesystem
  create      Create a new container
  diff        Inspect changes to files or directories on a container's filesystem
  events      Get real time events from the server
  exec        Run a command in a running container
  export      Export a container's filesystem as a tar archive
  history     Show the history of an image
  images      List images
  import      Import the contents from a tarball to create a filesystem image
  info        Display system-wide information
  inspect     Return low-level information on Docker objects
  kill        Kill one or more running containers
  load        Load an image from a tar archive or STDIN
  login       Log in to a Docker registry
  logout      Log out from a Docker registry
  logs        Fetch the logs of a container
  pause       Pause all processes within one or more containers
  port        List port mappings or a specific mapping for the container
  ps          List containers
  pull        Pull an image or a repository from a registry
  push        Push an image or a repository to a registry
  rename      Rename a container
  restart     Restart one or more containers
  rm          Remove one or more containers
  rmi         Remove one or more images
  run         Run a command in a new container
  save        Save one or more images to a tar archive (streamed to STDOUT by default)
  search      Search the Docker Hub for images
  start       Start one or more stopped containers
  stats       Display a live stream of container(s) resource usage statistics
  stop        Stop one or more running containers
  tag         Create a tag TARGET_IMAGE that refers to SOURCE_IMAGE
  top         Display the running processes of a container
  unpause     Unpause all processes within one or more containers
  update      Update configuration of one or more containers
  version     Show the Docker version information
  wait        Block until one or more containers stop, then print their exit codes

```

To view the options available to a specific command, type:
```
docker docker-subcommand --help
```

To view system-wide information about Docker, use:
```
docker info
```

### Working with Docker Images

To check whether you can access and download images from Docker Hub, type:
```
docker run hello-world
```

You can search for images available on Docker Hub by using the `docker` command with the `search` subcommand. For example, to search for the Ubuntu image, type:
```
docker search ubuntu
```

You can download it to your computer using the `pull` subcommand. Execute the following command to download the official `ubuntu` image to your computer:
```
docker pull ubuntu
```

To see the images that have been downloaded to your computer, type:
```
docker images
```

### Running a Docker Container

The combination of the **-i** and **-t** switches gives you interactive shell access into the container:
```
docker run -it ubuntu
```

You can run any command inside the container, To exit the container, type `exit` at the prompt.

To view the **active containers**, use:
```
docker ps
```

To view all containers — active and inactive, run `docker ps` with the `-a` switch:
```
docker ps -a
```

To view the latest container you created, pass it the `-l` switch:
```
docker ps -l
```

To start a stopped container, use `docker start`, followed by the container ID or the container’s name.

To stop a running container, use `docker stop`, followed by the container ID or name.

If you no longer need a container anymore, remove it with the `docker rm` command, again using either the container ID or the name.

#### Run into container shell:

```
docker exec -ti activiti /bin/bash
docker exec -ti container_name sh
```

### List networks

Run a `docker network ls` command to view existing container networks on the current Docker host.
#### Remove a network
To remove the network named 'my-network':

```
docker network rm my-network
```

## Copy files from container to host

```
docker cp <containerId>:/file/path/within/container /host/path/target
```

Here's an example:

```
$ sudo docker cp goofy_roentgen:/out_read.jpg .
```