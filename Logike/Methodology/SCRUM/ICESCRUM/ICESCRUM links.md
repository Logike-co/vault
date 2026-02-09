http://192.168.1.107:8088/icescrum/api

anadir token

https://www.icescrum.com/es/documentation/rest-api/
# instalacion
 
# Compose file for ICEScrum development compose environment.
# 
# @author <a href="mailto:javier.latorre@logike.co">Javier Latorre</a>
# @profile localhost
# @version 1.0 25-01-2026
services:
  icescrum-db:
    image: postgres:11
    command: -p 5439
    container_name: icescrum-db
    environment:
      - POSTGRES_USER=icescrum
      - POSTGRES_PASSWORD=myPass
      - POSTGRES_DB=icescrum
    expose:
      - "5439"
    volumes:
      - ./volumes/icescrum-db:/var/lib/postgresql/data
    ports:
      - "5439:5439"

  icescrum:
    image: icescrum/icescrum
    container_name: icescrum
    ports:
      - "8088:8080"
    depends_on:
      - icescrum-db
    volumes:
      - ./volumes/icescrum:/root

volumes:
  icescrum-db:
  icescrum:
