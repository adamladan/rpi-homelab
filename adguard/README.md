# 🎯 AdGuard Home & Unbound

A network-wide ad-and-tracker blocking DNS server. It acts as a shield for the entire home network, re-routing malicious or tracking domains to a "black hole". This stack is supercharged with **Unbound**, a local recursive DNS server that resolves queries directly with the internet's root servers to maximize your privacy.

## 🔗 Access & Links
* **Web Interface:** [http://homelab:8090](http://homelab:8090)
* **Official Documentation:** [AdGuard Home](https://github.com/AdguardTeam/AdGuardHome) | [Unbound (klutchell)](https://github.com/klutchell/unbound)

---

## ⚙️ Configuration & Architecture

This stack is deployed using the `docker-compose.yml` file located in this directory.

### 📦 Containers in this Stack
| Container Name | Image | Purpose |
| :--- | :--- | :--- |
| `adguardhome` | `adguard/adguardhome` | The primary DNS server and web admin interface for ad blocking. |
| `unbound` | `klutchell/unbound:latest` | Local recursive DNS server acting as the secure upstream for AdGuard. |

### 🚪 Exposed Ports
| Port | Protocol | Purpose |
| :--- | :--- | :--- |
| `53` | TCP/UDP | **Critical:** Standard DNS port. Devices on your network send requests here. |
| `8090` | TCP | AdGuard Web Admin Interface. |
| `3000` | TCP | Initial setup port (only used on the very first run of AdGuard). |
| `5335` | TCP/UDP | Unbound's exposed port. AdGuard routes its upstream queries here. |

### 💾 Volumes & Mounts (Persistent Data)
| Local Path / Volume | Container Path | Description |
| :--- | :--- | :--- |
| `./work` | `/opt/adguardhome/work` | Stores query logs, statistics, and downloaded filter lists. |
| `./conf` | `/opt/adguardhome/conf` | **Crucial:** Stores your `AdGuardHome.yaml` config file, custom rules, client settings, and admin password. |
