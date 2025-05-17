# Uptime Kuma Starter

A Docker-based setup for running Uptime Kuma with an API extension behind Nginx.

## Overview

This starter project includes:

- [Uptime Kuma](https://github.com/louislam/uptime-kuma): An open-source monitoring tool
- [Uptime Kuma API](https://github.com/MedAziz11/Uptime-Kuma-Web-API): An open-source REST API adapter for uptime-kuma
- Nginx: A web server that proxies requests and handles SSL

## Prerequisites

- Docker
- Docker Compose

## Getting Started

1. Clone this repository:
   ```bash
   git clone https://github.com/ehealth-co-id/uptime-kuma-api-starter-pack.git
   cd uptime-kuma-api-starter-pack
   ```

2. Update the environment variables in `docker-compose.yml` with your credentials:
   ```yaml
   environment:
     - KUMA_USERNAME=your-email@example.com
     - KUMA_PASSWORD=your-password
     - ADMIN_PASSWORD=your-admin-password
   ```

3. Start the services:
   ```bash
   docker-compose up -d
   ```

4. Access the services:
   - Uptime Kuma dashboard: https://localhost/
   - Uptime Kuma API: https://localhost/api/v1/

## SSL Certificates

By default, this setup uses self-signed certificates. For production use, replace the files in the `ssl/` directory with your own certificates:

- `ssl/selfsigned.crt`: Your certificate
- `ssl/selfsigned.key`: Your private key
- `ssl/dhparam.pem`: DH parameters for improved security

## Management Commands

```bash
# View logs
docker-compose logs

# Stop all services
docker-compose down

# Update to latest images
docker-compose pull
docker-compose up -d --force-recreate
```

## Configuration

The Nginx configuration in `nginx.conf.d/localhost.conf` can be modified to:
- Change the server name
- Adjust SSL settings
- Modify proxy behavior

## Data Persistence

Data is stored in:
- `./uptime_kuma/`: Uptime Kuma data
- `./uptime_kuma_api/`: API data

Consider backing up these directories regularly.

## License

[MIT](https://opensource.org/licenses/MIT)
