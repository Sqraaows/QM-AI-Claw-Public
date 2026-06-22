# Docker Commands

**Source**: Custom workspace skill

Common Docker commands for containers, images, and compose.

## Images

```bash
# List images
docker images
docker image ls

# Pull image
docker pull nginx:latest

# Build image
docker build -t myapp:latest .

# Tag image
docker tag myapp:latest myrepo/myapp:v1

# Push to registry
docker push myrepo/myapp:v1

# Remove image
docker rmi myapp:latest
docker image prune          # Remove unused

# Inspect
docker image inspect nginx:latest
```

## Containers

```bash
# List running
docker ps
docker ps -a                # All (including stopped)

# Run container
docker run -d --name web nginx
docker run -p 8080:80 nginx # Port mapping
docker run -v /host:/container nginx  # Volume

# Interactive
docker run -it ubuntu bash
docker exec -it web bash

# Stop/Start
docker stop web
docker start web
docker restart web

# Remove
docker rm web
docker rm -f web            # Force remove running

# Logs
docker logs web
docker logs -f web          # Follow
docker logs --tail 100 web

# Inspect
docker inspect web
docker stats web            # Resource usage
```

## Docker Compose

```bash
# Start services
docker compose up -d

# Stop services
docker compose down

# Rebuild
docker compose up -d --build

# Logs
docker compose logs -f

# Scale
docker compose up -d --scale web=3
```

## Cleanup

```bash
docker system df            # Disk usage
docker system prune         # Remove unused
docker system prune -a       # Remove all unused
docker volume prune         # Remove unused volumes
docker network prune         # Remove unused networks
```

## Tips

- Use `docker compose` (v2) not `docker-compose` (v1)
- `--rm` flag removes container when it exits
- `-e VAR=value` sets environment variables
- `--network` connects to specific network
- Use `docker login` before pushing

---

*Install date: 2026-04-27*
