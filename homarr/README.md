# 🏠 Homarr

A sleek, modern dashboard that acts as the central hub for all my self-hosted services. It provides quick access to apps and real-time monitoring of server health.

## 🔗 Links
* **Local Access:** `http://192.168.0.49:7575` (or via Tailscale IP)
* **Official Documentation:** [Homarr Docs](https://homarr.dev/docs/getting-started/)

---

## 🚀 Start Service
To spin up the dashboard, navigate to this directory and run:
```bash
docker compose up -d
```

---

## ⚙️ Configuration & Data

Homarr stores all your dashboard layouts, icons, and settings in specific folders to ensure they persist through updates.

**Exposed Ports:**
* `7575` (Web UI)

**Volumes (Persistent Data):**
* `./configs:/app/data/configs` *(Your layouts, widgets, and app settings)*
* `./icons:/app/data/icons` *(Custom icons you've uploaded)*

*Note: The `configs` folder is the most important one. Without it, you lose your entire dashboard layout.*

---

## 🔄 Updates
This service follows the **Standard Update Routine**. 

Please refer to the [Main README](../README.md#🔄-updating-services-standard-routine) for step-by-step update instructions.
