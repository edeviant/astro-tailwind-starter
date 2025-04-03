# 1077 Development Environment

A minimal Docker Compose setup for Node.js development.

## Project Structure
```
1077/
├── app/                  # Directory to be mounted to /app in the container
├── docker-compose.yml    # Docker Compose configuration
├── Dockerfile            # Docker image definition
└── README.md             # Setup instructions
```

## File Contents

### docker-compose.yml
```yaml
version: '3'
services:
  app:
    build: .
    container_name: 1077-app
    volumes:
      - ./app:/app
    working_dir: /app
    tty: true
    stdin_open: true

networks:
  default:
    name: 1077-network
```

### Dockerfile
```dockerfile
FROM node:22-slim

WORKDIR /app

CMD ["bash"]
```

## Setup

1. Make sure Docker and Docker Compose are installed on your system.
2. Clone this repository.
3. Run `docker-compose up -d` to start the container.
4. Run `docker-compose exec app bash` to access the container shell.
5. Install your Node.js application in the `/app` directory.

## Structure

- `./app`: This directory is mounted to `/app` in the container. Place your application code here.
- `docker-compose.yml`: Docker Compose configuration file.
- `Dockerfile`: Defines the Node.js container image.

## Commands

- Start the container: `docker-compose up -d`
- Stop the container: `docker-compose down`
- Access the container shell: `docker-compose exec app bash`