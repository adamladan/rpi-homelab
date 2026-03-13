# rpi-homelab
Documentation and configurations for my home lab on a Raspberry Pi.

## Hardware & OS
* **Device:** Raspberry Pi 4B 8GB RAM
* **OS:** Raspberry Pi OS Lite (64-bit)

---

## Initial Setup: Docker
To keep the system modular and clean, all services run inside Docker containers.

### 1. Install Docker
```bash
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh
```

### 2. Grant user permissions:
*(Required to run Docker without typing `sudo` every time. Log out and back in after running this step).*
```bash
sudo usermod -aG docker $USER
```
---
## Remote Access: Tailscale
To securely access the server and services from outside the local network, Tailscale is used to create a private VPN.

### 1. Install and connect:
```bash
curl -fsSL https://tailscale.com/install.sh | sh
sudo tailscale up
```
