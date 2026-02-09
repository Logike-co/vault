#java #maven #windows 
___
**INDEX**

- [[#Overview|Overview]]
	- [[#Overview#What you’ll learn|What you’ll learn]]
	- [[#Overview#What you’ll need|What you’ll need]]
- [[#Installation Instructions|Installation Instructions]]
	- [[#Installation Instructions#Stage 1 - Download Maven|Stage 1 - Download Maven]]
	- [[#Installation Instructions#Stage 2 - Set Up Environment Variables|Stage 2 - Set Up Environment Variables]]
- [[#Install JAR into local repository|Install JAR into local repository]]

___
# Overview

Apache Maven is a software project management and comprehension tool. Based on the concept of a project object model (POM), Maven can manage a project's build, reporting and documentation from a central piece of information.

## What you’ll learn

- How to install and configure Maven management tool.

## What you’ll need

* Linux operative system.
* Root user.
* Running JVM.
# Installation Instructions

## Stage 1 - Download Maven

The latest Maven version is listed in the _Files_ section of the official website. Earlier versions are available in the _Previous Releases_ section. Follow the procedure below to download and install Maven on an Ubuntu system:

- The `/opt` directory is reserved for the software and packages that aren't part of the default install, Create a Maven install directory (you must use the sudo user):
``` shell
sudo mkdir /opt/maven
```

- Download from: https://maven.apache.org/download.cgi or Download the Maven installation file to the _/tmp_ directory using the **wget** command, the syntax is:
```
wget [link] -P /tmp
```
Replace **`[link]`** with the link to the Maven version you copied in the previous step.

- Once the download is complete, extract the installation file to the  _/opt_ directory:
```
sudo tar xf /tmp/apache-maven-*.tar.gz -C /opt/maven
```

## Stage 2 - Set Up Environment Variables

The Maven installation is located at `/opt/maven/apache-maven-*`, add this location to the `~/.bashrc` file:

- Create and open the _maven.sh_ script file in the _/etc/profile.d/_ directory:
``` shell
sudo nano /etc/profile.d/maven.sh
```

- Add the following lines to the _maven.sh_ file:

``` shell
export JAVA_HOME=/opt/java/dragonwell-25.0.0.0.1+36-GA
export M2_HOME=/opt/maven/apache-maven-3.9.11
export MAVEN_HOME=/opt/maven/apache-maven-3.9.11
export PATH=${M2_HOME}/bin:${PATH}
```

- Use the **chmod** command to make the _maven.sh_ file executable:
``` shell
sudo chmod +x /etc/profile.d/maven.sh
```

- Execute the _maven.sh_ script file with the **source** command to set up the new environment variables:
``` shell
source /etc/profile.d/maven.sh
```

- Check the current version of Maven to verify the installation:
``` shell
mvn -version
```

- If the console print something like this, Congratulations you have now Maven installed!
``` shell
Apache Maven 3.9.11 (3e54c93a704957b63ee3494413a2b544fd3d825b)
Maven home: /opt/maven/apache-maven-3.9.11
Java version: 25.0.0.0.1, vendor: Alibaba, runtime: /opt/java/dragonwell-25.0.0.0.1+36-GA
Default locale: en_US, platform encoding: UTF-8
OS name: "linux", version: "6.14.0-29-generic", arch: "amd64", family: "unix"
```

# Install JAR into local repository

```xml
mvn install:install-file \
   -Dfile=<path-to-file> \
   -DgroupId=<group-id> \
   -DartifactId=<artifact-id> \
   -Dversion=<version> \
   -Dpackaging=<packaging> \
   -DgeneratePom=true
```

