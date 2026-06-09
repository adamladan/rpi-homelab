# 🎯 Ollama & Open WebUI

A complete, self-hosted local AI stack. Ollama acts as the backend engine running the large language models (LLMs), while Open WebUI provides a sleek, ChatGPT-like frontend interface to chat with the models.

*Note: This stack is intentionally kept offline when not in use to save RAM on the Raspberry Pi.*

## 🔗 Access & Links
* **Web Interface:** [http://homelab:8080](http://homelab:8080)
* **Official Documentation:** [Ollama](https://docs.ollama.com/) | [Open WebUI GitHub](https://github.com/open-webui/open-webui)

---

## ⚙️ Configuration & Architecture

This stack is deployed using the `docker-compose.yml` file located in this directory.

### 📦 Containers in this Stack
| Container Name | Image | Purpose |
| :--- | :--- | :--- |
| `ollama` | `ollama/ollama:latest` | The core AI engine. Downloads and runs the models in the background. |
| `open-webui` | `ghcr.io/open-webui/open-webui:main` | The frontend web application. Connects to Ollama's API. |

### 🚪 Exposed Ports
| Port | Protocol | Purpose |
| :--- | :--- | :--- |
| `8080` | TCP | Open WebUI Web Interface (where you actually chat). |
| `11434` | TCP | Ollama API. Open WebUI uses this to talk to the AI engine. |

### 💾 Volumes & Mounts (Persistent Data)
| Local Path / Volume | Container Path | Description |
| :--- | :--- | :--- |
| `./ollama_data` | `/root/.ollama` | **Crucial:** Stores the downloaded AI models (weights). Saves you from re-downloading them every time you start the container. |
| `./webui_data` | `/app/backend/data` | Stores your chat history, user accounts, and UI settings for Open WebUI. |
