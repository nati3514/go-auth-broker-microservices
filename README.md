# go-auth-broker-microservices

Lightweight Go microservices example implementing an Authentication Service and a Broker Service. The focus is on JSON-based communication between services and a simple local orchestration using Docker Compose.

## Overview

This project contains three main components:

- `authentication-service` — handles user authentication, token generation, and user data.
- `broker-service` — receives events/messages (JSON) and dispatches them to other services.
- `front-end` — minimal web UI for testing flows.

Project layout (top-level):

- `authentication-service/` — auth service source and Dockerfile
- `broker-service/` — broker service source and Dockerfile
- `front-end/` — simple web UI
- `project/` — `docker-compose.yml`, local orchestration and DB volumes

## Goals

- Demonstrate microservice patterns in Go
- Use JSON for inter-service communication
- Provide reproducible local setup via `docker-compose`
- Adopt a Git workflow: feature branches and PRs for all changes

## Prerequisites

- Docker & Docker Compose
- Go 1.20+ (for local builds) — optional if using Docker
- A GitHub account to host the public repository

## Quickstart (local with Docker)

1. From the repository root:

```bash
docker compose -f project/docker-compose.yml up --build
```

2. Services expose APIs under ports configured in `project/docker-compose.yml`.

3. To stop and remove containers:

```bash
docker compose -f project/docker-compose.yml down -v
```

## Running the project

The repository contains three services and a `docker-compose.yml` that brings them up along with a PostgreSQL database for development.

1. Ensure Docker and Docker Compose are installed.
2. From the repository root, start all services:

```bash
docker compose -f project/docker-compose.yml up --build
```

3. The services listen on ports defined in the compose file:
	- authentication-service: `http://localhost:8080` (example)
	- broker-service: `http://localhost:8090`
	- front-end: `http://localhost:3000` (if built)

4. To stop and clean up containers and volumes:

```bash
docker compose -f project/docker-compose.yml down -v
```

Refer to the individual service directories for additional build or run instructions if running outside Docker.
