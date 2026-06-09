# Salma Platform
A SageMaker-like multi-user notebook platform. Each user gets their own isolated JupyterLab container on a single VM.

## How it works
One VM → JupyterHub → DockerSpawner → one isolated container per user.

## Requirements
- Docker Desktop installed and running

## Run it

```bash
# 1. Clone
git clone https://github.com/Salma-87/salma-platform.git
cd salma-platform

# 2. Build notebook image
docker build -f Dockerfile.notebook -t salma-platform-notebook:latest .

# 3. Start
docker compose up -d

# 4. Open browser
http://localhost:8000
```

Sign up as `admin`, create more users to test isolation.

## Prove isolation works
```bash
docker ps
# Shows one container per logged-in user
# jupyter-admin, jupyter-salma, etc.
```

## Stop
```bash
docker compose down
```
