# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This repository contains a Docker-based setup for running Uptime Kuma with an API extension. The setup consists of:

1. **Uptime Kuma**: An open-source monitoring tool
2. **Uptime Kuma API**: A custom API extension for Uptime Kuma
3. **Nginx**: A web server that proxies requests to both services and handles SSL

## Project Structure

- `docker-compose.yml`: Defines the three services (nginx, uptime-kuma, uptime-kuma-api)
- `nginx.conf.d/`: Contains Nginx configuration
- `ssl/`: Contains SSL certificates and parameters
- `uptime_kuma/`: Volume mount for Uptime Kuma data (created by Docker)
- `uptime_kuma_api/`: Volume mount for Uptime Kuma API data (created by Docker)

## Common Commands

### Starting the Services
```bash
docker-compose up -d
```

### Stopping the Services
```bash
docker-compose down
```

### Viewing Logs
```bash
# All services
docker-compose logs

# Specific service
docker-compose logs uptime-kuma
docker-compose logs uptime-kuma-api
docker-compose logs nginx
```

### Rebuilding or Updating Services
```bash
docker-compose pull  # Get latest images
docker-compose up -d --force-recreate  # Recreate containers
```

## Configuration

### Environment Variables
The `uptime-kuma-api` service requires several environment variables which are defined in the `docker-compose.yml` file:
- `KUMA_SERVER`: The URL to the Uptime Kuma instance
- `KUMA_USERNAME`: Username for Uptime Kuma
- `KUMA_PASSWORD`: Password for Uptime Kuma
- `ADMIN_PASSWORD`: Admin password for the API

Make sure to update these from the default values before deployment.

### SSL Configuration
The default setup uses self-signed certificates located in the `ssl/` directory. For production, replace these with valid certificates.

## Accessing the Services

After starting the services:
- Uptime Kuma dashboard: https://localhost/
- Uptime Kuma API: https://localhost/api/v1/