# docker
This repository contains the docker-compose.yml file required to start all the infrastructure and services needed for the basic walking skeleton of the WODTracker system.

## Cómo ejecutar
1. Desde la carpeta `docker/`, ejecuta: `docker-compose up --build`
2. Accede al frontend en http://localhost:3000
3. APIs en http://localhost:8080 (user-service) y http://localhost:8081 (wod-service)
4. Bases de datos PostgreSQL en localhost:5433 (woddb) y localhost:5434 (userdb)
