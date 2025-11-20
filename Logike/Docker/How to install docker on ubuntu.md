#docker #ubuntu #v22-04 #v24-04
___
**INDEX**

- [Overview](#Overview)
	- [What you’ll learn](#What%20you%E2%80%99ll%20learn)
	- [What you’ll need](#What%20you%E2%80%99ll%20need)
- [Installation Instructions](#Installation%20Instructions)
	- [Step 1 - Installing Docker](#Step%201%20-%20Installing%20Docker)
	- [Step 2 - Executing the Docker Command Without Sudo (Optional)](#Step%202%20-%20Executing%20the%20Docker%20Command%20Without%20Sudo%20(Optional))
	- [Step 3 - Configure Docker to start on boot with systemd](#Step%203%20-%20Configure%20Docker%20to%20start%20on%20boot%20with%20systemd)
	- [Step 4 - Manage Docker service](#Step%204%20-%20Manage%20Docker%20service)
- [Uninstall Docker Engine](#Uninstall%20Docker%20Engine)

---

# Overview

[Docker](https://www.docker.com/) is an application that simplifies the process of managing application processes in _containers_. Containers let you run your applications in resource-isolated processes. They’re similar to virtual machines, but containers are more portable, more resource-friendly, and more dependent on the host operating system.

In this tutorial, you’ll install and use Docker Community Edition (CE) on Ubuntu. You’ll install Docker itself, work with containers and images, and push an image to a Docker Repository.

## What you’ll learn

- How to install and configure docker in Ubuntu.

## What you’ll need

- Ubuntu OS: [[How to install an Ubuntu LTS server]]
- A `sudo` non-**root** user and a firewall.

# Installation Instructions

## Step 1 - Installing Docker

The Docker installation package available in the official Ubuntu repository may not be the latest version. To ensure we get the latest version, we’ll install Docker from the official Docker repository. To do that, we’ll add a new package source, add the GPG key from Docker to ensure the downloads are valid, and then install the package.

First, update your existing list of packages:
```bash
sudo apt update
```

Next, install a few prerequisite packages which let `apt` use packages over HTTPS:
```bash
sudo apt install apt-transport-https ca-certificates curl software-properties-common
```

Then add the GPG key for the official Docker repository to your system:
```bash
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```

Add the Docker repository to APT sources:
```bash
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

Update your existing list of packages again for the addition to be recognized:
```bash
sudo apt update
```

Make sure you are about to install from the Docker repo instead of the default Ubuntu repo:
```bash
apt-cache policy docker-ce
```

You’ll see output like this, although the version number for Docker may be different:

Output of apt-cache policy docker-ce
```
docker-ce:
  Installed: (none)
  Candidate: 5:20.10.14~3-0~ubuntu-jammy
  Version table:
     5:20.10.14~3-0~ubuntu-jammy 500
        500 https://download.docker.com/linux/ubuntu jammy/stable amd64 Packages
     5:20.10.13~3-0~ubuntu-jammy 500
        500 https://download.docker.com/linux/ubuntu jammy/stable amd64 Packages
```

Notice that `docker-ce` is not installed, but the candidate for installation is from the Docker repository for Ubuntu 22.04 (`jammy`).

Finally, install Docker:
```bash
sudo apt install docker-ce  docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

Docker should now be installed, the daemon started, and the process enabled to start on boot. Check that it’s running:
```bash
sudo systemctl status docker
```

The output should be similar to the following, showing that the service is active and running:
```
Output● docker.service - Docker Application Container Engine
     Loaded: loaded (/lib/systemd/system/docker.service; enabled; vendor preset: enabled)
     Active: active (running) since Fri 2022-04-01 21:30:25 UTC; 22s ago
TriggeredBy: ● docker.socket
       Docs: https://docs.docker.com
   Main PID: 7854 (dockerd)
      Tasks: 7
     Memory: 38.3M
        CPU: 340ms
     CGroup: /system.slice/docker.service
             └─7854 /usr/bin/dockerd -H fd:// --containerd=/run/containerd/containerd.sock
```

Installing Docker now gives you not just the Docker service (daemon) but also the `docker` command line utility, or the Docker client.

```bash
sudo docker --version 
```

## Step 2 - Executing the Docker Command Without Sudo (Optional)

By default, the `docker` command can only be run the **root** user or by a user in the **docker** group, which is automatically created during Docker’s installation process. If you attempt to run the `docker` command without prefixing it with `sudo` or without being in the **docker** group, you’ll get an output like this:
```
Outputdocker: Cannot connect to the Docker daemon. Is the docker daemon running on this host?.
See 'docker run --help'.
```

If you want to avoid typing `sudo` whenever you run the `docker` command, add your username to the `docker` group:
```
sudo usermod -aG docker ${USER}
```

To apply the new group membership, log out of the server and back in, or type the following:
```
su - ${USER}
```

You will be prompted to enter your user’s password to continue.

Confirm that your user is now added to the **docker** group by typing:
```
groups
```

```
Output
sammy sudo docker
```

If you need to add a user to the `docker` group that you’re not logged in as, declare that username explicitly using:
```bash
sudo usermod -aG docker username
```

## Step 3 - Configure Docker to start on boot with systemd

Many modern Linux distributions use [systemd](https://docs.docker.com/config/daemon/systemd/) to manage which services start when the system boots. On Debian and Ubuntu, the Docker service starts on boot by default. To automatically start Docker and containerd on boot for other Linux distributions using systemd, run the following commands:

```bash
sudo systemctl enable docker.service
sudo systemctl enable containerd.service
```

## Step 4 - Manage Docker service

Docker should now be installed and running as a background service. To check the status of the Docker service, run:

```
sudo systemctl status docker 
```

If the Docker service is not running, you can start it with:

```
sudo systemctl start docker 
```

To enable the Docker service to start automatically at boot, run:

```
sudo systemctl enable docker 
```

# Uninstall Docker Engine

1. Uninstall the Docker Engine, CLI, containerd, and Docker Compose packages:

```bash
sudo apt-get purge docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin docker-ce-rootless-extras
```

1. Images, containers, volumes, or custom configuration files on your host aren't automatically removed. To delete all images, containers, and volumes:

```bash
sudo rm -rf /var/lib/docker
sudo rm -rf /var/lib/containerd
```

You have to delete any edited configuration files manually.

https://docs.docker.com/config/daemon/