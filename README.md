# pyriand3r/restyaboard

Open source, Trello like Kanban board, based on Restya platform.
http://restya.com/board

## Build

```
docker build -t restya:0.6.3 .
```

## `docker-compose.yml`

```
restyaboard:
  image: restya:0.6.3
  ports:
    - "8080:80"
  volumes: # optional
    - /home/gabriel/ressourcen/docker/restya/media:/var/www/html/media
  links:
    - postgres
    - elasticsearch # optional
  environment:
    - DB_HOST=postgres
    - DB_PORT=5432 # optional, default: 5432
    - DB_USER=restyaboard
    - DB_PASSWORD=restyaboard # optional, default: DB_USER
    - DB_NAME=restyaboard # optional, default: restyaboard
postgres:
  image: postgres
  volumes: # optional
    - /home/gabriel/ressourcen/docker/restya/db:/var/lib/postgresql/data
  environment:
    - POSTGRES_USER=restyaboard
    - POSTGRES_PASSWORD=restyaboard
elasticsearch: # optional
  image: elasticsearch
  volumes: # optional
    - /home/gabriel/ressourcen/docker/restya/search:/usr/share/elasticsearch/data
```

## Default users

```
Username: admin
Password: restya

Username: user
Password: restya
```
