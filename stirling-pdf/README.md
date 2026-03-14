# 📄 Stirling-PDF

A powerful, locally hosted, web-based tool to manage, split, merge, and edit PDF files without relying on external cloud services.

## ✨ Features
* Merge, split, and rotate PDFs
* Add/remove passwords and watermarks
* OCR (Optical Character Recognition) support
* Completely private and runs entirely on the local network

## ⚙️ Configuration
This service is deployed using Docker Compose. All settings, including port mappings and volume mounts for persistent data (like custom files, OCR training data, and logs), are defined in the [`docker-compose.yml`](./docker-compose.yml) file located in this directory

## 🚀 Usage

### Start the service:
Navigate to this directory on the server and run:
```bash
docker compose up -d
```

### 🌐 Access the web interface:
* **Locally:** `http://homelab:8080` (or the local IP address)
*  **Remotely (via Tailscale):** `http://homelab:8080` (using MagicDNS) or `http://<your-tailscale-ip>:8080`

### 🛑 Stop the service:
If you need to shut down the container, run:
```bash
docker compose down
```

### 🔄 Update the service:
To pull the latest updates for Stirling-PDF, run these commands in the directory:
```bash
docker compose pull
docker compose up -d
```
