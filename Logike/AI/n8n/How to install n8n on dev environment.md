#ubuntu #dev #n8n
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

In this guide, you will learn how to install a n8n develop environment using Ubuntu Desktop 

## What you’ll learn

- How to install and configure a n8n develop environment
- Further configuration options

## What you’ll need

- Minimal Ubuntu desktop installed.
- docker and docker compose installed.
- sudo terminal

# Installation instructions

## Stage 1 - create docker compose

- Create opt folder: 
``` shell
mkdir /opt/n8n
```

- create compose yaml file:
``` yaml
# Compose file for n8n development compose environment.
# 
# @author <a href="mailto:javier.latorre@logike.co">Javier Latorre</a>
# @profile localhost
# @version 1.0 2026-01-20
services:
  n8n-db:
    image: postgres:14
    command: -p 5438
    container_name: n8n-db
    environment:
      - POSTGRES_USER=n8n
      - POSTGRES_PASSWORD=n8npass
      - POSTGRES_DB=n8n
    expose:
      - "5438"
    volumes:
      - ./volumes/n8n-db:/var/lib/postgresql/data
    ports:
      - "5438:5438"

  n8n:
    image: n8nio/n8n
    container_name: n8n
    ports:
      - "5678:5678"
    environment:
      - DB_TYPE=postgresdb
      - DB_POSTGRESDB_HOST=n8n-db
      - DB_POSTGRESDB_DATABASE=n8n
      - DB_POSTGRESDB_PORT=5438
      - DB_POSTGRESDB_USER=n8n
      - DB_POSTGRESDB_PASSWORD=n8npass
      - N8N_BASIC_AUTH_ACTIVE=true
      - N8N_BASIC_AUTH_USER=admin
      - N8N_BASIC_AUTH_PASSWORD=strongpass
    depends_on:
      - n8n-db
    volumes:
      - ./volumes/n8n:/home/node/.n8n

volumes:
  n8n-db:
  n8n:
```

**What this file does:**

- **image:** Uses the official n8n Docker image.
- **ports:** Exposes n8n on port `5678`.
- **environment:** Sets up basic authentication so only you can log in.
- **volumes:** Persists your n8n workflows locally so they don’t get lost when containers restart.

- start docker compose: 
``` shell
docker compose up -d
```

- Error: EACCES: permission denied, open '/home/node/.n8n/config': 
``` shell
sudo chown -R 1000:1000 /opt/n8n
```

## Stage 2:  access the n8n dashboard

http://localhost:5678

## Useful links

> [!HANDBOOK]
> the n8n docs: [[https://docs.n8n.io/hosting/installation/docker/#starting-n8n]]
> https://www.digitalocean.com/community/tutorials/how-to-setup-n8n
 



