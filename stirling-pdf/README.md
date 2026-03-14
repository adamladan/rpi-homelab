# Stirling-PDF

A powerful, locally hosted, web-based tool to manage, split, merge, and edit PDF files without relying on external cloud services.

## Features
* Merge, split, and rotate PDFs
* Add/remove passwords and watermarks
* OCR (Optical Character Recognition) support
* Completely private and runs entirely on the local network

## Configuration
This service is deployed using Docker Compose. The configuration maps local folders to the container to ensure data (like custom files, training data for OCR, and logs) is saved persistently across restarts.

### `docker-compose.yml`
```yaml
services:
  stirling-pdf:
    image: frooodle/s-pdf:latest
    container_name: stirling-pdf
    ports:
      - "8080:8080"
    volumes:
      - ./trainingData:/usr/share/tessdata
      - ./extraConfigs:/configs
      - ./customFiles:/customFiles
      - ./logs:/logs
    environment:
      - DOCKER_ENABLE_SECURITY=false
    restart: unless-stopped
```
## Usage

### Start the service:
Navigate to this directory on the server and run:
```bash
docker compose up -d
```

### Access the web interface:
* **Locally:** `http://homelab:8080` (or the local IP address)
*  **Remotely (via Tailscale):** `http://homelab:8080` (using MagicDNS) or `http://<your-tailscale-ip>:8080`

### Stop the service:
If you need to shut down the container, run:
```bash
docker compose down
```

### Update the service:
To pull the latest updates for Stirling-PDF, run these commands in the directory:
```bash
docker compose pull
docker compose up -d
```
