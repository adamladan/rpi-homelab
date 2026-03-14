# 🍓 rpi-homelab

Welcome to my home lab documentation! This repository contains the configurations, scripts, and notes for setting up and maintaining my personal server on a Raspberry Pi.

## ⚙️ Hardware & OS
* **Device:** Raspberry Pi 4 Model B (8GB RAM)
* **OS:** Raspberry Pi OS Lite (64-bit)
* **Storage:** USB 3 Stick

---

## 🐳 Initial Setup: Docker
To keep the system modular, clean, and easy to back up, all services are deployed as Docker containers.

### 1. Install Docker
Download and run the official convecnience script:
```bash
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh
```

### 2. Grant user permissions:
This allows you to run Docker commands without typing `sudo`every time.
```bash
sudo usermod -aG docker $USER
```
*(Note: You must log out and log back in via SSH for this to take effect).*

---
## 🔒 Remote Access: Tailscale
To securely access the server and its services from outside the local network (without opening router ports), Tailscale is used to create a private, encrypted VPN.

### 1. Install and connect:
```bash
curl -fsSL https://tailscale.com/install.sh | sh
sudo tailscale up
```

### 2. Accessing Services
Once connected to the Tailnet, services can be accessed remotely using the Pi's Tailscale IP or MagicDNS name (e.g., `http://homelab:8080`).

---

## 🚀 Hosted Services
Here is a list of the services currently running on this server. Click on any service to see its specific `docker-compose.yml` and setup instructions:
* [Stirling-PDF](./stirling-pdf) - A powerful, locally hosted tool to manage, split, merge and edit PDF files.
