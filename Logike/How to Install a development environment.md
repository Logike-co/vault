#ubuntu #dev
___
**INDEX**

- [Overview](#Overview)
	- [What you’ll learn](#What%20you%E2%80%99ll%20learn)
	- [What you’ll need](#What%20you%E2%80%99ll%20need)
- [Installation instructions](#Installation%20instructions)
	- [Stage 1 - Operating System Configuration](#Stage%201%20-%20Operating%20System%20Configuration)
	- [Stage 2: Install Basic applications](#Stage%202:%20Install%20Basic%20applications)
	- [Stage 3 - Java Development Environment](#Stage%203%20-%20Java%20Development%20Environment)
	- [Stage 4 - Repository management](#Stage%204%20-%20Repository%20management)
	- [Stage 5: Install Docker container engine](#Stage%205:%20Install%20Docker%20container%20engine)

___
# Overview

In this guide, you will learn how to install a develop environment using Ubuntu Desktop on a virtual machine. [VirtualBox](https://www.virtualbox.org/) is a general purpose visualizer that is available across Linux, Mac OS and Windows. [VMWare](https://www.vmware.com/) enables users to set up [virtual machines](https://en.wikipedia.org/wiki/Virtual_machine "Virtual machine") (VMs) on a single physical machine and use them simultaneously along with the host machine. It’s a great way to experience Ubuntu regardless of your current operating system.

**Note:** This tutorial will also work for other distributions, so try it out with some of the Ubuntu [flavours](https://ubuntu.com/download/flavours) as well!

## What you’ll learn

- How to run a virtual instance of Ubuntu Desktop
- How to install and configure a Java develop environment
- Further configuration options

## What you’ll need

- A PC with internet access.
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
* Visual Studio Code: To write code in an IDE (Integrated Development Environment).
* DBeaver: To connect to any Database.

## Stage 3 - Install Java Development Environment

> [!HANDBOOK]
> Install the JDK from: [[How to install the Java Developer Kit - JDK]]

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
 



