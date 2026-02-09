#git #gogs

---
**INDEX**

- [[#Introduction|Introduction]]
- [[#Prerequisites|Prerequisites]]
- [[#Install Steps|Install Steps]]
	- [[#Install Steps#Step 1 - ...|Step 1 - ...]]

---
# Introduction

# Prerequisites

- Docker installed on your server: [[How To Install Docker on Ubuntu 22.04]]
- Docker compose installed on your server: [[How To Install Docker Compose on Ubuntu 22.04]]
- Git installed on your server: [[How to install GIT]]
# Install Steps

## Step 1 - Create a compose file

```dockerfile
  gogs-ui:
    container_name: gogs-ui
    image: gogs/gogs:latest
    networks:
      tools-net:
        aliases:
          - gogs-ui
    ports:
      - 10022:22
      - 3000:3000
    restart: always
    volumes:
      - ./volumes/gogs-ui:/data
```
