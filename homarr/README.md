# 🎯 Homarr & Dashdot

A sleek, modern dashboard that acts as the central hub for all self-hosted services. It provides quick access to apps, while Dashdot runs in the background to feed it real-time monitoring of server health, CPU, and RAM.

## 🔗 Access & Links
* **Homarr Interface:** [http://homelab:7575](http://homelab:7575)
* **Dashdot Interface:** [http://homelab:3001](http://homelab:3001)
* **Official Documentation:** [Homarr Docs](https://homarr.dev/) | [Dashdot Docs](https://getdashdot.com/)

---

## ⚙️ Configuration & Architecture

This stack is deployed using the `docker-compose.yml` file located in this directory.

### 📦 Containers in this Stack
| Container Name | Image | Purpose |
| :--- | :--- | :--- |
| `homarr` | `ghcr.io/homarr-labs/homarr:latest` | The main dashboard application and web interface. |
| `dashdot` | `mauricenino/dashdot:latest` | System monitor that provides live CPU, RAM, and temperature data. |

### 🚪 Exposed Ports
| Port | Protocol | Purpose |
| :--- | :--- | :--- |
| `7575` | TCP | Homarr Web Interface. |
| `3001` | TCP | Dashdot Web Interface / API. |

### 💾 Volumes & Mounts (Persistent Data)
| Local Path / Volume | Container Path | Description |
| :--- | :--- | :--- |
| `./appdata` | `/appdata` | **Crucial:** Stores all your Homarr layouts, settings, configurations, and custom icons. |
| `/var/run/docker.sock` | `/var/run/docker.sock` | Allows Homarr to read Docker status and manage your containers. |
| `/` | `/mnt/host:ro` | Allows Dashdot read-only access to monitor the host machine's hardware. |
