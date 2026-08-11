# ERPNext v15 Docker Automation

## Project Overview

This project automates the deployment of ERPNext v15 using Docker and Docker Compose based on the provided manual installation guide. Instead of manually installing dependencies such as Python, Node.js, MariaDB, Redis, and ERPNext, the entire deployment is containerized for consistency and easier management.

---

## Technologies Used

- Docker
- Docker Compose
- Ubuntu 22.04
- ERPNext v15
- Frappe Framework
- MariaDB 10.6
- Redis 6.2
- Node.js 18

---

## Project Structure

```
erpnext-docker/
│
├── Dockerfile
├── docker-compose.yml
├── README.md
└── screenshots/
    ├── docker-build.png
    ├── docker-ps.png
    ├── docker-logs.png
    └── erpnext-running.png
```

---

## Prerequisites

- Ubuntu 22.04
- Docker Engine
- Docker Compose

Verify installation:

```bash
docker --version
docker compose version
```

---

## Build the Docker Image

```bash
docker build -t custom-erpnext:v15 .
```

---

## Start ERPNext

```bash
docker compose up -d
```

---

## Verify Running Containers

```bash
docker ps
```

Expected containers include:

- backend
- frontend
- db
- redis-cache
- redis-queue
- scheduler
- websocket
- queue-short
- queue-long

---

## View Container Logs

```bash
docker compose logs
```

Or

```bash
docker compose logs -f
```

---

## Access ERPNext

Open your browser:

```
http://localhost:8080
```

---

## Default Credentials

### MariaDB

```
Username : root
Password : Admin@123
```

### ERPNext Administrator

```
Administrator
Password : Admin@123
```

---

## Docker Commands Used

### Build

```bash
docker build -t custom-erpnext:v15 .
```

### Start

```bash
docker compose up -d
```

### Stop

```bash
docker compose down
```

### Restart

```bash
docker compose restart
```

### Check Containers

```bash
docker ps
```

### View Logs

```bash
docker compose logs -f
```

---

## Approach

The objective of this project was to automate the manual ERPNext installation process using Docker.

The implementation includes:

- Dockerfile for building the ERPNext environment.
- Docker Compose for orchestrating multiple containers.
- Separate containers for ERPNext Backend, Frontend, MariaDB, Redis, Scheduler, Queue Workers, and WebSocket.
- Persistent Docker volumes for database, logs, and ERPNext sites.
- Automatic ERPNext site creation using the `create-site` service.
- Configuration automation using the `configurator` service.

This approach follows containerization best practices by separating application services into independent containers, making deployment easier, scalable, and reproducible.

---

## Assumptions

- Docker and Docker Compose are installed.
- Internet connectivity is available for pulling required Docker images.
- Port **8080** is available.
- Default credentials are used for demonstration purposes.
- Custom application installation (`library_management`) is not included.

---

## Screenshots Included

The following screenshots are attached as part of the submission:

- Docker Image Build
- Running Containers (`docker ps`)
- Docker Logs
- ERPNext Login Page

---

## Conclusion

This project successfully automates the ERPNext deployment using Docker and Docker Compose, replacing the manual installation process with a reproducible and containerized deployment.