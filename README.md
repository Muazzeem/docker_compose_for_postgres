# Docker Compose Configuration for PostgreSQL Databases

This Docker Compose configuration sets up two PostgreSQL database services: one for development and one for production.

## Services

### 1. postgres_dev (Development Database)

- **Image**: Custom-built from `./compose/dev/postgres/Dockerfile`
- **Volumes**:
  - `dev_postgres_data`: Stores PostgreSQL data
  - `dev_postgres_data_backups`: Stores database backups
- **Environment**: Configured via `./.envs/.dev/.postgres`
- **Port**: 5432 (host) -> 5432 (container)

### 2. postgres (Production Database)

- **Image**: Custom-built from `./compose/production/postgres/Dockerfile`
- **Volumes**:
  - `postgres_data`: Stores PostgreSQL data
  - `postgres_data_backups`: Stores database backups
- **Environment**: Configured via `./.envs/.production/.postgres`
- **Port**: 15432 (host) -> 5432 (container)

## Volumes

- `dev_postgres_data`
- `dev_postgres_data_backups`
- `postgres_data`
- `postgres_data_backups`

## Usage

To start the services:

```bash
docker compose up -d
```

#### Stop the services:

```bash
docker compose down
````
#### Delete volumes:

```bash
docker volume rm jobkhuzi_dev_postgres_data jobkhuzi_dev_postgres_data_backups postgres_data postgres_data_backups
```

#### Delete everything:

```bash
docker system prune -a
```