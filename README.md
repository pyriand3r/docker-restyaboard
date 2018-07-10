Originally created by viossat, i updated the files for the latest restyaboard version

# pyriand3r/restyaboard

Open source, Trello like Kanban board, based on Restya platform.
http://restya.com/board

## Build

```
docker build -t pyriand3r/restyaboard .
```

## `docker-compose.yml`

```
restyaboard:
  image: pyriand3r/restyaboard
  ports:
    - "8080:80"
  volumes: # optional
    - /restya/media:/var/www/html/media
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
    - /restya/db:/var/lib/postgresql/data
  environment:
    - POSTGRES_USER=restyaboard
    - POSTGRES_PASSWORD=restyaboard
elasticsearch: # optional
  image: elasticsearch
  volumes: # optional
    - /restya/search:/usr/share/elasticsearch/data
```

## Default users

```
Username: admin
Password: restya

Username: user
Password: restya
```
