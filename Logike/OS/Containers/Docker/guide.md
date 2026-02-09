
Using `docker` consists of passing it a chain of options and commands followed by arguments. The syntax takes this form:
```
docker [option] [command] [arguments]
```

To view all available subcommands, type:
```
docker
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

### Remove a network
To remove the network named 'my-network':

```
docker network rm my-network
```

## Running an Interactive Shell in a Docker Container
```docker
docker exec -it container-name sh
```

## [Running a Non-interactive Command in a Docker Container](https://www.digitalocean.com/community/tutorials/how-to-use-docker-exec-to-run-commands-in-a-docker-container#running-a-non-interactive-command-in-a-docker-container)

docker exec container-name tail /var/log/date.log