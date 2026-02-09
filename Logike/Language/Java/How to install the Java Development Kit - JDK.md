#java #JDK #ubuntu
___
**INDEX**

- [[#Overview|Overview]]
	- [[#Overview#What you’ll learn|What you’ll learn]]
	- [[#Overview#What you’ll need|What you’ll need]]
- [[#Installation instructions|Installation instructions]]
	- [[#Installation instructions#Stage 1 - Download the JDK|Stage 1 - Download the JDK]]
		- [[#Stage 1 - Download the JDK#Oracle JVM|Oracle JVM]]
		- [[#Stage 1 - Download the JDK#Alibaba Dragonwell JVM|Alibaba Dragonwell JVM]]
		- [[#Stage 1 - Download the JDK#Eclipse Temurin|Eclipse Temurin]]
	- [[#Installation instructions#Stage 2 - Install the JDK|Stage 2 - Install the JDK]]
	- [[#Installation instructions#Stage 3 - Update java alternatives|Stage 3 - Update java alternatives]]

___
# Overview

The Java Development Kit (JDK) is a distribution of Java technology by Oracle Corporation. It implements the Java Language Specification (JLS) and the Java Virtual Machine Specification (JVMS) and provides the Standard Edition (SE) of the Java Application Programming Interface (API). It is derivative of the community driven OpenJDK which Oracle stewards. It provides software for working with Java applications. Examples of included software are the Java virtual machine, a compiler, performance monitoring tools, a debugger, and other utilities that Oracle considers useful for Java programmers.

## What you’ll learn

- How to install and configure a Java development environment.

## What you’ll need

* Linux operative system.
* Root user.

# Installation instructions

## Stage 1 - Download the JDK

### Oracle JVM

JDK binaries are free to use in production and free to redistribute, at no cost, under the [Oracle No-Fee Terms and Conditions](https://www.java.com/freeuselicense) (NFTC).

Is recommend to use long term support (LTS) versions, available at:

https://www.oracle.com/co/java/technologies/downloads/#java21
https://www.oracle.com/co/java/technologies/downloads/#java17

Use the archive download for historical Java releases:
https://www.oracle.com/co/java/technologies/downloads/archive/

For our development environment we use **JDK-17**

### Alibaba Dragonwell JVM

https://dragonwell-jdk.io/#/index

### Eclipse Temurin

https://adoptium.net/en-GB/temurin

## Stage 2 - Install the JDK

- The `/opt` directory is reserved for the software and packages that aren't part of the default install, Create a JDK install directory (you must use the sudo user):
``` shell
sudo mkdir /opt/java
```

- Locate the folder where you downloaded the file, extract the tar file to the folder:
``` shell
sudo tar -zxf {jvm-vendor-file}.tar.gz -C /opt/java
```

- Configure the installed JDK as default, In this guide, the Java executable is located at `/opt/java/{jvm-vendor}/bin/java`

For Java compile:
``` shell
sudo update-alternatives --install /usr/bin/javac javac /opt/java/{jvm-vendor}/bin/javac 1000
```

For Java JRE:
``` shell
sudo update-alternatives --install /usr/bin/java java /opt/java/{jvm-vendor}/bin/java 1000
```
## Stage 3 - Update java alternatives

- If you need to check the java alternatives, you can select the JDK version installed to use:
``` shell
sudo update-alternatives --config java
```

- To check if the java version is correct:
``` shell
java -version
```

- If the console print something like this, Congratulations you have now Java installed!

- For Oracle JDK:
``` shell
java version "17.0.8" 2023-07-18 LTS
Java(TM) SE Runtime Environment (build 17.0.8+9-LTS-211)
Java HotSpot(TM) 64-Bit Server VM (build 17.0.8+9-LTS-211, mixed mode, sharing)
```

- For Alibaba Dragonwell:
``` shell
openjdk version "25.0.0.0.1" 2025-09-24
OpenJDK Runtime Environment (Alibaba Dragonwell Standard Edition)-25.0.0.0.1+36-GA (build 25.0.0.0.1)
OpenJDK 64-Bit Server VM (Alibaba Dragonwell Standard Edition)-25.0.0.0.1+36-GA (build 25.0.0.0.1, mixed mode, sharing)
```

- For Eclipse Temurin:
``` shell
openjdk version "25.0.1" 2025-10-21 LTS
OpenJDK Runtime Environment Temurin-25.0.1+8 (build 25.0.1+8-LTS)
OpenJDK 64-Bit Server VM Temurin-25.0.1+8 (build 25.0.1+8-LTS, mixed mode, sharing)
```

