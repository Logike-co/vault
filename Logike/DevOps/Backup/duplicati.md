

```dockerfile
 duplicati-ui:
    container_name: duplicati-ui
    image: ghcr.io/linuxserver/duplicati
    environment:
      - PUID=0
      - PGID=0
      - TZ=Colombia/Bogota
    volumes:
      - ./volumes/duplicati/config:/config
      - ./volumes/duplicati/backups:/backups
      - ./volumes/duplicati:/source
    ports:
      - 8200:8200
    restart: always
    networks:
      tools-net:
        aliases:
          - duplicati-ui
```

