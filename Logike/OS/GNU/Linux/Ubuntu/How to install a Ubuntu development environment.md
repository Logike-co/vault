#ubuntu #dev
___
**INDEX**

- [[#Overview|Overview]]
	- [[#Overview#What you’ll learn|What you’ll learn]]
	- [[#Overview#What you’ll need|What you’ll need]]
- [[#Installation instructions|Installation instructions]]
	- [[#Installation instructions#Stage 1 - Operating System Configuration|Stage 1 - Operating System Configuration]]
	- [[#Installation instructions#Stage 2: Install Basic applications|Stage 2: Install Basic applications]]
	- [[#Installation instructions#Stage 3 - Install Java Development Environment|Stage 3 - Install Java Development Environment]]
	- [[#Installation instructions#Stage 4 - Repository management|Stage 4 - Repository management]]
	- [[#Installation instructions#Stage 5: Install Docker container engine|Stage 5: Install Docker container engine]]

___
# Overview

In this guide, you will learn how to install a develop environment using Ubuntu Desktop on a virtual machine or personal computer. [VirtualBox](https://www.virtualbox.org/) is a general purpose visualizer that is available across Linux, Mac OS and Windows. [VMWare](https://www.vmware.com/) enables users to set up [virtual machines](https://en.wikipedia.org/wiki/Virtual_machine "Virtual machine") (VMs) on a single physical machine and use them simultaneously along with the host machine. It’s a great way to experience Ubuntu regardless of your current operating system.

**Note:** This tutorial will also work for other distributions, so try it out with some of the Ubuntu [flavours](https://ubuntu.com/download/flavours) as well!

## What you’ll learn

- How to run a virtual instance of Ubuntu Desktop.
- How to install and configure a JDK - Java develop environment.
- Further configuration options.

## What you’ll need

- A PC, or VM with internet access.
- Minimal Ubuntu desktop installed.

# Installation instructions

## Stage 1 - Operating System Configuration

- Create root user password: 
- @default: `ma$t3rK3y`
``` shell
sudo passwd root
```

> "With great power comes a great responsibility", Please don't forget the root password!

- Install network tools:
``` shell
sudo apt install net-tools
```

## Stage 2: Install Basic applications

Using the Ubuntu App Center, search and install:

* Chromium: As an internet browser.
* Obsidian: To document and consult information.
* Visual Studio Code or IntelliJ IDEA CE: To write code in an IDE (Integrated Development Environment).
* DBeaver: To connect and write SQL code to any Database.

## Stage 3 - Install Java Development Environment

> [!HANDBOOK]
> Install the JDK from: [[How to install the Java Development Kit - JDK]]

> [!HANDBOOK]
> Install the Maven from: [[How to install Maven in Linux]]
## Stage 4 - Repository management

- Git is likely already installed in your Ubuntu server. You can confirm this is the case on your server with the following command:
``` shell
git --version
```

- If you receive output similar to the following, then Git is already installed.
```
Output
git version 2.43.0
```

- If not, you can install GIT using the package manager:
``` shell
sudo apt update
sudo apt-get install git
git --version
```

## Stage 5: Install Docker container engine

> [!HANDBOOK]
> Install the Docker from: [[How to install docker on ubuntu]]
> Install the Docker compose from: [[How to install docker compose on ubuntu]]
 


## Setting a static IP address

### Step 1: Note information about the current network

We will need our current network details such as the current assigned IP, subnet mask, and the network adapter name so that we can apply the necessary changes in the configurations.

Use the command below to find details of the available adapters and the respective IP information.
 
```bash
ip a
```

![[Pasted image 20230803111524.png]]

For my network, the current adapter is `ens160`. It could be different for your system

* Note the subnet

We can find the subnet mask details using the command below:

```bash
ifconfig -a
```

if the command is not installed, you must install the net-tools:

```bash
sudo apt install net-tools
```

![[Pasted image 20230803111614.png]]

### Step 2: Make configuration changes

[Netplan](https://netplan.io/) is the default network management tool for the latest Ubuntu versions. Configuration files for Netplan are written using YAML and end with the extension `.yaml`.

```bash
cd /etc/netplan
ls
```

If you do not see any files, you can create one. The name by convention, should start with a number like `01-` and end with `.yaml`. The number sets the priority if you have more than one configuration file. by default the file found is: 00-installer-config.yaml

```bash
nano 00-installer-config.yaml
```

![[Pasted image 20230804130640.png]]

### Step 3: Apply and test the changes

We can test the changes first before permanently applying them using this command:

```bash
sudo netplan try
```

or the set the changes use the command:

```bash
sudo netplan apply
```

Set timezone

timedatectl set-timezone America/Bogota
