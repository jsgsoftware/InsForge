# Deploy InsForge with Docker Compose

Use this compose stack when you want InsForge and its required services to start together from the repository.

## Files to Use

1. `docker-compose.selfhost.yml`
2. `.env.selfhost.example`

## Why

InsForge needs multiple services to run correctly:

1. PostgreSQL
2. PostgREST
3. InsForge app
4. Deno runtime

This compose file in the repository starts all of them together.

## Supported Use Cases

You can use this stack with:

1. `docker compose` on a VPS
2. EasyPanel `Compose` service
3. Portainer stacks
4. Any platform that accepts a standard compose file

## Setup

1. Use `docker-compose.selfhost.yml` as your compose file.
2. Copy `.env.selfhost.example` to your own `.env` or platform environment section.
3. Replace these values before deploying:
   1. `API_BASE_URL`
   2. `VITE_API_BASE_URL`
   3. `JWT_SECRET`
   4. `ENCRYPTION_KEY`
   5. `ADMIN_EMAIL`
   6. `ADMIN_PASSWORD`
   7. `POSTGRES_PASSWORD`

## Local Command

```bash
cp .env.selfhost.example .env
docker compose -f docker-compose.selfhost.yml up -d
```

## Notes

1. The app service is built from your selected Git branch.
2. PostgreSQL, PostgREST, and Deno are created by the same stack.
3. Persistent volumes are defined for database data, file storage, and logs.
4. This setup intentionally skips the `vector` service to keep deployment simpler.
