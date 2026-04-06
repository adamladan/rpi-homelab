# 🏠 Homarr

A sleek, modern dashboard that acts as the central hub for all my self-hosted services. It provides quick access to apps and real-time monitoring of server health.

## 🔗 Links
* **Local Access:** http://192.168.0.49:7575 (or via Tailscale IP)
* **Official Documentation:** [Homarr Docs](https://homarr.dev/docs/getting-started/)

---

## ⚙️ Configuration & Data
	
This service is deployed using the `docker-compose.yml` file located in this directory.

**Note:** This compose file actually spins up **two** containers that work together: Homarr (the dashboard) and Dashdot (the system monitor that feeds CPU/RAM data to Homarr).

**Exposed Ports:**
* `7575` (Web UI)
* `3001` (Dashdot Web UI / API)

**Volumes (Persistent Data):**
* `./appdata:/appdata` *(All your Homarr layouts, settings, databases and custom icons are stored here)*
* `/var/run/docker.sock:/var/run/docker.sock` *(Allows Homarr to read Docker status and manage containers)*
* `/:/mnt/host:ro` *(Allows Dashdot read-only access to monitor the host's hardware)*

*Note: The `./appdata` folder is the most important one. Without it, you lose your entire dashboard layout and configuration.*
