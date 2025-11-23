# Docker Setup Guide

This project uses Docker Compose to orchestrate all services.

## Services

- **PostgreSQL Database** (port 5432)
- **Python Backend (FastAPI)** (port 8081)
- **TypeScript Backend (NestJS)** (port 8080)
- **Frontend (React/Vite + Nginx)** (port 3000)

## Prerequisites

- Docker and Docker Compose installed
- At least 2GB of free disk space

## Quick Start

1. **Create a `.env` file** in the root directory (optional, defaults are provided):
   ```env
   DB_USERNAME=postgres
   DB_PASSWORD=postgres
   DB_DATABASE=colormypicture
   DB_PORT=5432
   JWT_KEY=your-secret-jwt-key-change-in-production
   ```

2. **Build and start all services**:
   ```bash
   docker-compose up -d --build
   ```

3. **View logs**:
   ```bash
   docker-compose logs -f
   ```

4. **Stop all services**:
   ```bash
   docker-compose down
   ```

5. **Stop and remove volumes** (⚠️ This will delete database data):
   ```bash
   docker-compose down -v
   ```

## Important Notes

### Frontend Configuration

⚠️ **The frontend currently uses hardcoded `localhost:8080` URLs**. For Docker to work properly, you need to either:

1. **Update the frontend code** to use environment variables:
   - Update `color-my-picture-front/src/_services/axios.service.tsx` to use an environment variable
   - Build the frontend with the correct backend URL

2. **Or use nginx reverse proxy** (recommended for production):
   - Configure nginx to proxy `/api` requests to the backend service

### Service Communication

Services communicate through Docker's internal network using service names:
- Frontend → TypeScript Backend: `http://typescript-backend:8080`
- TypeScript Backend → Python Backend: `http://python-backend:8081`
- TypeScript Backend → PostgreSQL: `postgres:5432`

### Environment Variables

The TypeScript backend requires these environment variables:
- `DB_HOST` - Database host (default: `postgres`)
- `DB_PORT` - Database port (default: `5432`)
- `DB_USERNAME` - Database username
- `DB_PASSWORD` - Database password
- `DB_DATABASE` - Database name
- `JWT_KEY` - JWT secret key
- `API_URL` - Python backend URL (default: `http://python-backend:8081`)

### Volumes

The following volumes are created for data persistence:
- `postgres_data` - PostgreSQL database data
- `python_temp` - Temporary files for Python backend
- `python_rendered` - Rendered images from Python backend

## Development

For development, you may want to mount source code as volumes:

```yaml
# Add to docker-compose.yml services
volumes:
  - ./color-my-picture-back-ts/src:/app/src
  - ./color-my-picture-back-ts/package.json:/app/package.json
```

## Troubleshooting

1. **Port conflicts**: If ports are already in use, change them in `docker-compose.yml`

2. **Database connection errors**: Ensure PostgreSQL is healthy before starting the backend:
   ```bash
   docker-compose ps
   ```

3. **Build failures**: Clean build cache:
   ```bash
   docker-compose build --no-cache
   ```

4. **View service logs**:
   ```bash
   docker-compose logs [service-name]
   ```

## Production Considerations

1. **Change default passwords** and JWT keys
2. **Use secrets management** (Docker secrets, AWS Secrets Manager, etc.)
3. **Enable HTTPS** with reverse proxy (Traefik, Nginx, etc.)
4. **Set up proper logging** and monitoring
5. **Configure resource limits** in docker-compose.yml
6. **Use production-ready database** backups
7. **Update frontend** to use environment variables for API URLs

