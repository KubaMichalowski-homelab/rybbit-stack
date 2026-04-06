# rybbit-stack
This repository contains the configuration for my [Rybbit](https://github.com/rybbit-io/rybbit) deployment.

## Environment Setup
The stack relies on the following environment variables:

| Variable | Description | Example |
| :--- | :--- | :--- |
| `TUNNEL_TOKEN` | Cloudflare Tunnel token | `(Secret)` |
| `BASE_URL` | Public URL of the backend API | `https://analytics.domain.tld` |
| `BETTER_AUTH_ALLOWED_ORIGINS` | Allowed frontend origins (comma-separated) | `https://rybbit.domain.tld` |
| `BETTER_AUTH_TRUSTED_ORIGINS` | Allowed frontend origins (comma-separated) | `https://rybbit.domain.tld` |
| `BETTER_AUTH_URL` | Public URL of the backend API | `https://analytics.domain.tld` |
| `BETTER_AUTH_SECRET` | 32-byte random string | `(Secret)` |
| `CLICKHOUSE_PASSWORD` | Random string | `(Secret)` |
| `POSTGRES_PASSWORD` | Random string | `(Secret)` |
| `MAPBOX_TOKEN` | Token for Mapbox integration | `(Secret)` |

## Persistent Storage
I use bind mounts for data persistence. Ensure these paths exist on the Docker host:
* `/opt/docker/rybbit/postgres` - PostgreSQL database data
* `/opt/docker/rybbit/clickhouse-data` - ClickHouse analytics data

## Deployment
1. Clone this repository.
2. Copy `.env.example` and adjust values.
```bash
cp .env.example .env
```
3. Deploy using Docker Compose:
```bash
docker compose up -d --build
```

---

[Back to Homelab Overview](https://github.com/KubaMichalowski-homelab)
