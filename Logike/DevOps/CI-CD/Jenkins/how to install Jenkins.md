#jenkins

---

---

# Introduction

Jenkins is an automation server. While you can use it to automate just about any task, it’s most often associated with building source code and deploying the results. For many, Jenkins is synonymous with continuous integration and continuous delivery (CI/CD).

One of Jenkins’s most powerful features is its ability to distribute jobs across multiple nodes. A Jenkins controller sends jobs to the appropriate agent based on the job requirements and the resources available at the time.

While it’s possible to run jobs on the controller, it’s considered a best practice to always create at least one agent and run your jobs there. So, we’ll use Docker Compose to do just that.

# Prerequisites

- Docker installed on your server: [[How To Install Docker on Ubuntu 22.04]]
- Docker compose installed on your server: [[How To Install Docker Compose on Ubuntu 22.04]]

# Install Steps

## Step 1 - Installing 


```dockerfile

	jenkins-ui:
	    container_name: jenkins-ui
	    image: jenkins/jenkins:jdk17
	    networks:
	      tool-net:
	        aliases:
	          - jenkins-ui
	    ports:
	      - 8080:8080
	      - 50000:50000
	    privileged: true  
	    restart: always
	    user: root
	    volumes:
	      - ./volumes/jenkins-ui:/var/jenkins_home
	      - /var/run/docker.sock:/var/run/docker.sock
jenkins-ui:

container_name: jenkins-ui

image: jenkins/jenkins:jdk17

networks:

tool-net:

aliases:

- jenkins-ui

ports:

- 8080:8080

- 50000:50000

privileged: true

restart: always

user: root

volumes:

- ./volumes/jenkins-ui:/var/jenkins_home

- /var/run/docker.sock:/var/run/docker.sock

jenkins-db:

command: -p 5434

container_name: jenkins-db

environment:

POSTGRES_USER: dev

POSTGRES_PASSWORD: pd_admin

POSTGRES_DB: jenkins

image: postgres:latest

networks:

tool-net:

aliases:

- jenkins-db

ports:

- 5434:5434

restart: always

volumes:

- ./volumes/jenkins-db:/var/lib/postgresql/data
	      
```

- Open the URL `localhost:8080`in a browser.

- To ensure Jenkins is securely set up by the administrator, a password has been written to the log and this file on the server:
```
/var/jenkins_home/secrets/initialAdminPassword
```

- Use this command to check the password:
```
docker exec jenkins-ui tail /var/jenkins_home/secrets/initialAdminPassword
```

- Please copy the password from either location and paste it in the page opened.

#### Getting Started

Plugins extend Jenkins with additional features to support many different needs. you can install plugins suggested, and **install**.

### Create First Admin User

Usuario: admin
Contraseña: admin123
Nombre completo
Jenkins admin
Dirección email:

* Set URL:  http://localhost:8079/

### Admin Jenkins

##### Credentials

- System
- gogs
##### System

- SSH remote hosts
- SSH sites

	- Hostname
	- Port
	- Credentials
#### Plugins

- Maven integration

- Docker API
- Docker commons plugin
- Docker pipeline
- Docker plugin

- SSH
- SSH Server
#### Tools

##### Instalaciones JDK

- name: JDK 17
- JAVA_HOME: /opt/java/openjdk

/opt/java/jdk-17.0.8

add maven pluging

##### Git installations

- name: Default
- Path to Git executable: git

##### instalaciones de Maven

- Nombre: Maven
- Install automatically from Apache 3.9.8

##### instalaciones de docker

- Name: Docker
- Install automaticamente
- Download from docker.com
- Docker version: latest

manage/configure
--- add host site

sudo apt-get install sshpass

create directories in /home/dev/Builds
mkdir bitar-ui