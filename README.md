# 🍓 rpi-homelab

Welcome to my home lab documentation! This repository contains the configurations, scripts, and notes for setting up and maintaining my personal server on a Raspberry Pi.

## ⚙️ Hardware & OS
* **Device:** Raspberry Pi 4 Model B (8GB RAM)
* **OS:** Raspberry Pi OS Lite (64-bit)
* **Storage:** USB 3.1 Flash Drive

---

## 🐳 Initial Setup: Docker
To keep the system modular, clean, and easy to back up, all services are deployed as Docker containers.

### 1. Install Docker
Download and run the official convenience script:
```bash
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh
```

### 2. Grant User Permissions
This allows you to run Docker commands without typing `sudo` every time.
```bash
sudo usermod -aG docker $USER
```
*(Note: You must log out and log back in via SSH for this to take effect).*

---

## 🔒 Remote Access: Tailscale
To securely access the server and its services from outside the local network (without opening router ports), Tailscale is used to create a private, encrypted VPN.

### 1. Install and Connect
```bash
curl -fsSL https://tailscale.com/install.sh | sh
sudo tailscale up
```

### 2. Accessing Services
Once connected to the Tailnet, services can be accessed remotely using the Pi's Tailscale IP or MagicDNS name (e.g., `http://homelab:8080`).

---

## 🔄 Updating Services (Standard Routine)
Following the DRY (Don't Repeat Yourself) principle, most services in this homelab follow the exact same update procedure. Unless specified otherwise in a service's specific README, use these steps to update a container to its latest version:

1. Navigate to the directory containing the service's `docker-compose.yml` (example):
   ```bash
   cd ~/homelab/homarr
   ```
2. Pull the latest image:
   ```bash
   docker compose pull
   ```
3. Recreate and start the container in the background:
   ```bash
   docker compose up -d
   ```
4. *(Optional but recommended)* Clean up old, unused Docker images to save disk space:
   ```bash
   docker image prune -f
   ```

---

## 🚀 Hosted Services
Here is a list of the services currently running on this server. Click on any service to see its specific `docker-compose.yml` and setup instructions:

| Service | Description | Port |
| :--- | :--- | :--- |
| [**Homarr**](./homarr) | A visually appealing, intuitive dashboard to make it easier to access locally hosted apps. Uses **Dashdot** to monitor system resources. | `7575` |
| [**Stirling PDF**](./stirling-pdf) | A powerful, locally hosted tool to manage, split, merge, and edit PDF files. | `8080` |
| [**AdGuard Home**](./adguard-home) | Network-wide ad and tracker blocking DNS server. Acts as a sinkhole to protect all connected devices. | `8090` (Web)<br>`53` (DNS) |
