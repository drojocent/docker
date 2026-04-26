# WODTracker Docker Infrastructure

Configuración Docker Compose para desplegar la stack completa de WODTracker con todos los servicios, bases de datos y herramientas de desarrollo.

## Servicios

| Servicio | Puerto | Descripción |
|----------|--------|-------------|
| Frontend | 3000 | Aplicación Vue.js (Nginx) |
| User Service | 8080 | API de usuarios y autenticación |
| WOD Service | 8081 | API de WODs y entrenamientos |
| PostgreSQL (WOD) | 5433 | Base de datos de WODs |
| PostgreSQL (User) | 5434 | Base de datos de usuarios |
| Adminer | 8082 | Gestor web de bases de datos |
| Mailpit | 8025/1025 | Testing de emails |

## Requisitos

- Docker 20.10+
- Docker Compose 2.0+
- Puertos disponibles: 3000, 8080, 8081, 8082, 5433, 5434

## Inicio rápido

```bash
cd docker/

# Crear archivo .env
cp .env.example .env

# Iniciar todo
docker compose up
```

Espera a que los servicios estén listos.

Acceso:
- Frontend: http://localhost:3000
- User Service: http://localhost:8080
- WOD Service: http://localhost:8081
- Adminer: http://localhost:8082
- Mailpit: http://localhost:8025


## Comandos útiles

```bash

# Reiniciar
docker compose restart

# Parar
docker compose down

# Parar y eliminar todo (incluyendo datos)
docker compose down -v

# Reconstruir imágenes
docker compose build

# Descargar versiones actualizadas
docker compose pull

```

## Acceso a servicios

### Frontend
```
http://localhost:3000
Usuarios demo:
  Email: user@user.com
  Password: user

  Email: admin@admin.com
  Password: admin
```

### APIs

User Service:
```
Endpoint: http://localhost:8080
Swagger: http://localhost:8080/swagger-ui.html
```

WOD Service:
```
Endpoint: http://localhost:8081
Swagger: http://localhost:8081/swagger-ui.html
```

### Herramientas

Adminer (gestor de bases de datos):
```
http://localhost:8082
Sistema: PostgreSQL
Servidor: postgres-wod o postgres-user
Usuario: postgres
Contraseña: password
Base de datos: woddb o userdb
```

Mailpit (pruebas de email):
```
http://localhost:8025
```

## Variables de entorno

Crea `.env` desde `.env.example`:

```env
# CAMBIAR EN PRODUCCIÓN
JWT_SECRET=secret-key
```

## CI/CD

Los repositorios construyen y publican imágenes automáticamente con GitHub Actions al hacer push a `main`.

Actualizar imágenes:

```bash
docker compose pull
docker compose up -d
```