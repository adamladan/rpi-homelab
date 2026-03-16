# 🦊 Homarr Dashboard

This is the configuration for my personal homepage and control panel, built with Homarr. This is the central hub where I manage and monitor my entire homelab!

## 🌐 Access

* **Local URL:** `http://homelab:7575`
* **IP Address:** `http://192.168.0.49:7575` *(Update this if the local IP changes)*

## ⚙️ Start and Stop

Navigate to this directory (`~/homelab/homarr`) and run the following Docker Compose commands:

**Start the services in the background:**
`bash
docker compose up -d
`

**Stop the services:**
`bash
docker compose down
`

## 📦 Contents of this Compose File

* **Homarr:** The main dashboard application.
* **Dashdot:** Monitors the Raspberry Pi's CPU, RAM, and network to display live system graphs on the dashboard via port `3001`.

## 💾 Data and Backups

Homarr's settings, boards, and icons are saved persistently in mapped volumes within this directory. If the Raspberry Pi restarts or the container is recreated, all custom designs and configurations remain safely stored here.
