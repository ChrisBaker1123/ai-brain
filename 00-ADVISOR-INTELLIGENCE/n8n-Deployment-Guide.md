---
type: reference
status: active
created: 2026-03-24
updated: 2026-03-24
domain: business
tags:
  - n8n
  - docker
  - deployment
  - infrastructure
  - self-hosted
---

# n8n Docker Deployment Guide

Last Updated: 2026-03-24

## Overview

Production deployment guide for n8n workflow automation using Docker Compose. This is infrastructure for [[Service-Playbook]] deliverables — building client-facing automation workflows for RIA firms like [[DLK-HUB]].

## Architecture: Production Stack

```
                    ┌─────────────┐
                    │   Clients   │
                    └──────┬──────┘
                           │ HTTPS (443)
                    ┌──────▼──────┐
                    │    Nginx    │  ← SSL termination
                    │  (reverse   │
                    │   proxy)    │
                    └──────┬──────┘
                           │ HTTP (5678)
                    ┌──────▼──────┐
                    │    n8n      │  ← Workflow engine
                    │  container  │
                    └──────┬──────┘
                           │ TCP (5432)
                    ┌──────▼──────┐
                    │  PostgreSQL │  ← Persistent storage
                    │  container  │
                    └─────────────┘
```

## PostgreSQL vs SQLite

| Factor | PostgreSQL | SQLite |
|--------|-----------|--------|
| **Concurrency** | Handles concurrent workflows well | Single-writer lock; bottleneck under load |
| **Data integrity** | ACID-compliant, designed for production | Good for single-user, risky under concurrent writes |
| **Backup** | pg_dump, streaming replication, point-in-time recovery | File copy (must stop n8n first or risk corruption) |
| **Scalability** | Scales to thousands of workflows | Degrades with large execution history |
| **Recommended for** | Production deployments | Development/testing only |

**Verdict**: Always use PostgreSQL for production. This is the established best practice per n8n docs and community consensus.

## Production Docker Compose Configuration

```yaml
services:
  postgres:
    image: postgres:15
    container_name: n8n-postgres
    restart: always
    environment:
      POSTGRES_USER: ${POSTGRES_USER}
      POSTGRES_PASSWORD: ${POSTGRES_PASSWORD}
      POSTGRES_DB: n8n
    volumes:
      - ./postgres_data:/var/lib/postgresql/data
    healthcheck:
      test: ["CMD-SHELL", "pg_isready -U ${POSTGRES_USER}"]
      interval: 10s
      timeout: 5s
      retries: 5

  n8n:
    image: n8nio/n8n:latest
    container_name: n8n
    restart: always
    environment:
      DB_TYPE: postgresdb
      DB_POSTGRESDB_HOST: postgres
      DB_POSTGRESDB_PORT: 5432
      DB_POSTGRESDB_USER: ${POSTGRES_USER}
      DB_POSTGRESDB_PASSWORD: ${POSTGRES_PASSWORD}
      DB_POSTGRESDB_DATABASE: n8n
      N8N_HOST: ${N8N_HOST}
      N8N_PORT: 5678
      N8N_PROTOCOL: https
      WEBHOOK_URL: https://${N8N_HOST}/
      NODE_ENV: production
      N8N_EXECUTION_TIMEOUT: 300
      N8N_MAX_EXECUTION_TIMEOUT: 3600
      GENERIC_TIMEZONE: America/Los_Angeles
    volumes:
      - ./n8n_data:/home/node/.n8n
      - ./local-files:/files
    depends_on:
      postgres:
        condition: service_healthy
    expose:
      - "5678"
    deploy:
      resources:
        limits:
          cpus: '2.0'
          memory: 4G
        reservations:
          cpus: '1.0'
          memory: 2G

  nginx:
    image: nginx:stable-alpine
    container_name: n8n-nginx
    restart: always
    ports:
      - "80:80"
      - "443:443"
    volumes:
      - ./nginx/conf.d:/etc/nginx/conf.d
      - ./nginx/certs:/etc/nginx/certs
    depends_on:
      - n8n
```

## Nginx Configuration (SSL)

```nginx
server {
    listen 80;
    server_name your-domain.com;
    return 301 https://$host$request_uri;
}

server {
    listen 443 ssl;
    server_name your-domain.com;

    ssl_certificate /etc/nginx/certs/fullchain.pem;
    ssl_certificate_key /etc/nginx/certs/privkey.pem;

    location / {
        proxy_pass http://n8n:5678;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
        proxy_cache_bypass $http_upgrade;
    }
}
```

### SSL Options
1. **Let's Encrypt + Certbot** — Free, auto-renews. Use certbot Docker container or host certbot.
2. **Traefik** — Alternative to Nginx; auto-provisions SSL certificates. More complex but automated.
3. **Cloudflare proxy** — Simplest option; point DNS through Cloudflare, enable "Full (strict)" SSL mode.

## Backup Strategy

### PostgreSQL Backups
```bash
# Daily automated backup
docker exec n8n-postgres pg_dump -U n8nuser n8n > backup_$(date +%Y%m%d).sql

# Compressed backup
docker exec n8n-postgres pg_dump -U n8nuser n8n | gzip > backup_$(date +%Y%m%d).sql.gz
```

### n8n Data Directory
```bash
# Backup encryption keys and custom nodes
tar -czf n8n_data_backup_$(date +%Y%m%d).tar.gz ./n8n_data
```

### Backup Schedule
- **Database**: Daily pg_dump, retain 30 days
- **n8n data directory**: Weekly tar backup (contains encryption keys for credentials)
- **Workflow exports**: Monthly JSON export of all workflows via n8n API
- **Off-site**: Sync backups to S3/B2 or another VPS

### Critical: Encryption Key
The `n8n_data` directory contains the encryption key for all stored credentials. If lost, all credentials must be re-entered. Always back up this directory and store copies securely.

## Monitoring and Alerting

### Health Check Endpoint
n8n exposes `/healthz` for basic health monitoring.

### Recommended Monitoring Stack
1. **Uptime monitoring**: UptimeRobot or Hetrixtools (free tier) — ping `/healthz` every 5 minutes
2. **Container monitoring**: `docker stats` or Portainer for real-time resource usage
3. **Log monitoring**: `docker logs n8n --follow` or ship to Grafana Loki
4. **Disk space**: Cron job alerting when disk usage exceeds 80%
5. **Execution monitoring**: n8n's built-in execution list; set up a workflow that checks for failed executions daily

### Alerting
- Webhook-based alerts to Slack/Discord/email when:
  - Container restarts
  - Execution failures exceed threshold
  - Disk space low
  - SSL certificate nearing expiration

## Security Hardening

1. **Basic auth**: Set `N8N_BASIC_AUTH_ACTIVE=true` with strong credentials
2. **Network isolation**: Only expose ports 80/443 through Nginx; n8n and PostgreSQL should not be directly accessible
3. **Environment variables**: Store secrets in `.env` file, never commit to git
4. **Firewall**: UFW or iptables — only allow 80, 443, and SSH (22)
5. **Docker socket**: Do not mount Docker socket into n8n container
6. **Regular updates**: Pin n8n version in docker-compose; update deliberately, not automatically
7. **Webhook security**: Use webhook authentication (header-based or query parameter tokens)
8. **Credential encryption**: n8n encrypts credentials at rest; ensure encryption key is backed up
9. **Non-root user**: n8n Docker image runs as `node` user by default — do not change to root
10. **Rate limiting**: Configure Nginx rate limiting for webhook endpoints

## Recommended VPS Specs

| Use Case | CPU | RAM | Storage | Monthly Cost |
|----------|-----|-----|---------|-------------|
| **Light** (< 10 workflows, few daily executions) | 2 vCPU | 2 GB | 40 GB SSD | ~$5-10/mo |
| **Standard** (10-50 workflows, hourly executions) | 2 vCPU | 4 GB | 80 GB SSD | ~$12-24/mo |
| **Heavy** (50+ workflows, frequent executions, AI nodes) | 4 vCPU | 8 GB | 160 GB SSD | ~$24-48/mo |

### VPS Providers
- **Hetzner** — Best value (EU/US). 2 vCPU / 4GB from ~$5/mo
- **Contabo** — Pre-installed n8n VPS plans from ~$5/mo
- **DigitalOcean** — $12/mo for 2 vCPU / 2GB; good US presence
- **Vultr** — Similar to DigitalOcean; multiple US locations

### For Advisor Intelligence
A **Standard** tier ($12-24/mo) VPS is appropriate for running client automation workflows. Scale to Heavy if running AI-powered nodes (Claude API calls within n8n) or processing large data sets.

## Update Process

```bash
# 1. Backup before updating
docker exec n8n-postgres pg_dump -U n8nuser n8n > pre_update_backup.sql
tar -czf n8n_data_pre_update.tar.gz ./n8n_data

# 2. Pull new image
docker compose pull n8n

# 3. Restart with new image
docker compose up -d

# 4. Verify health
curl https://your-domain.com/healthz
```

## Needs Further Investigation
- Whether to use Traefik vs Nginx (Traefik auto-provisions SSL but is more complex)
- Specific VPS location best for DLK (likely US West — Hetzner Hillsboro, OR)
- Whether to run n8n on same VPS as other services or dedicated
- Cost analysis: self-hosted n8n vs n8n Cloud ($24/mo starter, $60/mo pro)
- Disaster recovery plan and RTO/RPO requirements

## Sources
- https://docs.n8n.io/hosting/installation/docker/
- https://docs.n8n.io/hosting/installation/server-setups/docker-compose/
- https://zakops.com/devops/n8n-docker
- https://ginojohn.com/the-definitive-guide-to-a-production-ready-n8n-installation-on-ubuntu-docker
- https://www.aitooldiscovery.com/how-to/install-n8n-docker
- https://latenode.com/blog/low-code-no-code-platforms/self-hosted-automation-platforms/n8n-self-hosted-installation-guide-2025
- https://latenode.com/blog/low-code-no-code-platforms/self-hosted-automation-platforms/n8n-docker-installation-complete-setup-guide-production-configuration-examples-2025

## Related Notes
- [[n8n-Salesforce-Integration]]
- [[Tech-Stack]]
- [[Service-Playbook]]
- [[DLK-HUB]]
- [[Business-Infrastructure]]
