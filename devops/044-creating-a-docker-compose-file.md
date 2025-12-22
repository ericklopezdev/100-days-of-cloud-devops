# Day 44 - Creating A Docker Compose File

## Context
The Nautilus application development team shared static website content that needs to be hosted on the httpd web server using a containerised platform. The team has shared details with the DevOps team, and we need to set up an environment according to those guidelines. Below are the details:

On App Server 3 in Stratos DC create a container named httpd using a docker compose file /opt/docker/docker-compose.yml (please use the exact name for file).

Use httpd (preferably latest tag) image for container and make sure container is named as httpd; you can use any name for service.

Map 80 number port of container with port 3003 of docker host.

Map container's /usr/local/apache2/htdocs volume with /opt/itadmin volume of docker host which is already there. (please do not modify any data within these locations).

## Solution
```yaml
services:
  httpd:
    image: httpd:latest
    container_name: httpd
    ports:
      - 3003:80
    volumes:
      - /var/www/html:/usr/local/apache2/htdocs
```

```bash
docker compose -f /opt/itadmin/docker-compose.yml up -d
```

### Compose Commands

- **Up**: `docker-compose up -d` (start services)
- **Down**: `docker-compose down` (stop and remove)
- **Logs**: `docker-compose logs` (view service logs)
- **Scale**: `docker-compose up --scale service=3`
