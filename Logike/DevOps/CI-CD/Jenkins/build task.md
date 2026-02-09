
# Jenkins Task  - bitar-rest_qa_deploy
*Deploy bitar-rest docker container in QA environment* 
  
## Source code management: 

* GIT:
	* Repositories:
		* Repository URL: http://172.18.22.63:3000/BCO/bitar-rest.git
		* Credentials: 
	* Branches to build:
		* Branch Specifier: */master
	* Repository browser: gogs
		* URL: http://172.18.22.63:3000/BCO/bitar-rest

## Build environment

* Delete workspace before build starts  
  
## Pre steps  
*Preparing the workspace*
*@todo: deactivate for the first run*

* Execute shell script on remote host using ssh:
	* SSH site: dev@172.18.22.63:22
	* Command:  
		 echo "Loading . . . Preparing the workspace"
		 docker rmi bitar/bitar-rest

## Build

* Root POM: pom.xml
* Goals and options: clean package -Pproduction  dockerfile:build
## Post Steps
*Exporting image*
*Deploying container image*

* Run only if build succeeds

1. Execute shell script on remote host using ssh:
	* SSH site: dev@172.18.22.63:22
	* Command:  
		echo "Loading . . . Exporting image"
		rm /home/dev/Builds/latest/bitar-rest-latest.tar.gz
		echo "Removed ... tar.gz image"
		docker save bitar/bitar-rest | gzip > /home/dev/Builds/latest/bitar-rest-latest.tar.gz
		echo "Saved ... sib-ui-latest.tar.gz image"
		sshpass -p "dev123" scp /home/dev/Builds/latest/bitar-rest-latest.tar.gz 
		dev@172.18.22.61:/home/dev/Downloads/latest/
		echo "SSH copied ... sib-ui-latest.tar.gz image"
	* Execute each line

2. Execute shell script on remote host using ssh:
	* SSH site: dev@172.18.22.61:22
	* Command:  
		echo "Loading . . . Deploying container image"
		docker stop bitar-rest  
		docker rm bitar-rest
		docker rmi bitar/bitar-rest  
		zcat /home/dev/Downloads/latest/bitar-rest-latest.tar.gz | docker load  
		echo "Loaded ... sib-ui image"
		docker compose -f /opt/bco/bitar/compose.yaml up -d
		echo "Compose Up! ... sib-ui container"
	* Execute each line
