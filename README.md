# KIKA Docker Prototype

This repository contains a prototype deployment of the KIKA system using Docker.

It is designed to run in an **air-gapped environment** (no internet access) after you copy over the prepared images and scripts.

## 🚀 Getting Started

### Prerequisites

Make sure Docker and the Docker Compose plugin are installed on your Linux server:

```bash
docker --version
# Example: Docker version 26.1.0, build 123abc

docker compose version
# Example: Docker Compose version v2.27.0
```

> 💡 The Compose plugin is usually bundled with modern Docker releases.  
> If you see an error, check your Docker installation.

### Preparing the Deployment

1. Copy this repository to your **air-gapped server**.
2. Delete any architecture directories you don’t need (e.g. remove `arm64` if you’re only running `amd64`).
3. Ensure the required Docker images have been loaded from the provided tar archives.

### Starting the Application

Run:

```bash
sh run-all.sh
```

This will start all required containers, create networks and volumes if missing, and launch the services.

### Cleaning Up

To stop and remove containers, networks, and volumes created by this prototype:

```bash
sh clear-all.sh
```

## 🛠️ Notes

- The included scripts handle image loading and container orchestration without requiring `docker compose` on the host.
- Health checks and migration containers are included to ensure services come up in the right order.
- Images are provided for multiple architectures (e.g. `amd64`, `arm64`). Only keep the ones relevant to your environment.

## 📂 Repository Structure

```
├── run-all.sh         # Starts all services
├── clear-all.sh       # Cleans up containers, networks, and volumes
├── amd64/             # AMD64 images (if present)
├── arm64/             # ARM64 images (if present)
├── docker-compose.yml # Docker Compose file to start all services
├── LICENSE
└── README.md          # This file
```

## ✅ Next Steps

- Verify services are running with `docker ps`.
- Access the system via the configured ingress (default port `8082`).
- Review logs with `docker logs <container_name>` if troubleshooting is needed.

## 🌐 Accessing the Website

Once the stack is running, the website will be available at:

```
http://<IP ADDRESS OF LINUX SERVER or LOCALHOST>:8082
```
