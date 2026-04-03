# 🛡️ AdGuard Home

A network-wide software for blocking ads and tracking. After you set it up, it’ll cover ALL your home devices, and you don’t need any client-side software for that. It operates as a DNS server that re-routes tracking domains to a "black hole".

## 🔗 Links
* **Local Access (Web UI):** `http://192.168.0.49:8090` (or via Tailscale IP)
* **Official Documentation:** [AdGuard Home GitHub](https://github.com/AdguardTeam/AdGuardHome)

---

## 🚀 Start Service
To spin up the DNS server and web interface, navigate to this directory and run:
```bash
docker compose up -d
```

---

## ⚙️ Configuration & Data

This service is deployed using the `docker-compose.yml` file located in this directory. Because it acts as a DNS server, it requires specific ports to be open to the local network.

**Exposed Ports:**
* `53` (TCP & UDP) - **Critical:** This is the standard DNS port.
* `8090` (TCP) - Web Admin Interface.

**Volumes (Persistent Data):**
* `./workdir:/opt/adguardhome/work` *(Stores query logs, statistics, and downloaded filter lists)*
* `./confdir:/opt/adguardhome/conf` *(Stores your `AdGuardHome.yaml` config file, custom rules, and settings)*

*Note: The `confdir` is crucial. If you lose this, you lose all your custom blocklists, client settings, and the admin password.*

---

## 🔄 Updates
This service follows the **Standard Update Routine**. 

Please refer to the [Main README](../README.md#🔄-updating-services-standard-routine) for step-by-step update instructions. 
