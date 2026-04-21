# docker
This repository contains the docker-compose.yml file required to start all the infrastructure and services needed for the basic walking skeleton of the WODTracker system.

## Como ejecutar
1. Crea el archivo `.env` a partir de `.env.example` y ajusta los valores necesarios.
2. Desde la carpeta `docker/`, ejecuta: `docker compose pull`
3. Levanta el entorno con: `docker compose up`
4. Accede al frontend en http://localhost:3000
5. APIs en http://localhost:8080 (user-service) y http://localhost:8081 (wod-service)
6. Bases de datos PostgreSQL en localhost:5433 (woddb) y localhost:5434 (userdb)

Este compose usa imagenes ya publicadas en GHCR. Los repositorios de frontend, user-service y wod-service construyen y publican sus imagenes con GitHub Actions al hacer push a `main`.
