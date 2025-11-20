#docker #docker-compose #ubuntu #v22-04 #v24-04
___
**INDEX**

- [Overview](#Overview)
	- [What you’ll learn](#What%20you%E2%80%99ll%20learn)
	- [What you’ll need](#What%20you%E2%80%99ll%20need)
- [Installation Instructions](#Installation%20Instructions)
	- [Step 1 - Installing Docker Compose](#Step%201%20-%20Installing%20Docker%20Compose)
	- [Step 2 - Running Docker Compose](#Step%202%20-%20Running%20Docker%20Compose)
	- [Step 3 - Getting Familiar with Docker Compose Commands](#Step%203%20-%20Getting%20Familiar%20with%20Docker%20Compose%20Commands)
- [Conclusion](#Conclusion)

___
# Overview

Docker simplifies the process of managing application processes in containers. While containers are similar to virtual machines in certain ways, they are more lightweight and resource-friendly. This allows developers to break down an application environment into multiple isolated services.

For applications depending on several services, orchestrating all the containers to start up, communicate, and shut down together can quickly become unwieldy. [Docker Compose](https://docs.docker.com/compose/) is a tool that allows you to run multi-container application environments based on definitions set in a YAML file. It uses service definitions to build fully customizable environments with multiple containers that can share networks and data volumes.

## What you’ll learn

- How to install and configure docker compose in Ubuntu.

## What you’ll need

- Ubuntu OS.
- Docker installed on your server.

# Installation Instructions

## Step 1 - Installing Docker Compose

First, confirm the latest version available in their [releases page](https://github.com/docker/compose/releases). At the time of this writing, the most current stable version is `2.33.1`.

Use the following command to download:

```bash
mkdir -p ~/.docker/cli-plugins/
curl -SL https://github.com/docker/compose/releases/download/v2.33.1/docker-compose-linux-x86_64 -o ~/.docker/cli-plugins/docker-compose
```

Next, set the correct permissions so that the `docker compose` command is executable:
```bash
chmod +x ~/.docker/cli-plugins/docker-compose
```

To verify that the installation was successful, you can run:
```bash
docker compose version
```

Docker Compose is now successfully installed on your system. 

##  Step 2 - Running Docker Compose

To run the compose in background mode use (must be run where the compose file is located):
```bash
docker compose up -d
```

Your environment is now up and running in the background. To verify that the container is active, you can run:

```bash
docker compose ps
```

## Step 3 - Getting Familiar with Docker Compose Commands

To check the logs produced by your container, you can use the `logs` command:
```bash
docker compose logs
```

If you want to pause the environment execution without changing the current state of your containers, you can use:
```bash
docker compose pause
```

To resume execution after issuing a pause:
```bash
docker compose unpause
```

The `stop` command will terminate the container execution, but it won’t destroy any data associated with your containers:
```bash
docker compose stop
```

If you want to remove the containers, networks, and volumes associated with this containerized environment, use the `down` command:
```bash
docker compose down
```

In case you want to also remove the base image from your system, you can use:
```bash
docker image rm nginx:alpine
```

# Conclusion

In this guide, you’ve seen how to install Docker Compose and set up a containerized environment. You’ve also seen how to manage this environment using Compose commands.

For a complete reference of all available `docker compose` commands, check the [official documentation](https://docs.docker.com/compose/reference/).