# 📄 Stirling PDF

A powerful, locally hosted, web-based PDF manipulation tool that allows you to split, merge, convert, and edit PDFs without sending data to the cloud.

## 🔗 Links
* **Local Access:** `http://192.168.0.79:8080` (or via Tailscale IP)
* **Official Documentation:** [GitHub - Stirling-Tools](https://github.com/Stirling-Tools/Stirling-PDF)

---

## ⚙️ Configuration & Data

This service is deployed using the `docker-compose.yml` file located in this directory. 

**Exposed Ports:**
* `8080` (Web UI)

**Volumes (Persistent Data):**
* `./trainingData:/usr/share/tesseract-ocr/5/tessdata` *(Used for OCR language packs)*
* `./extraConfigs:/configs` *(Custom settings)*
* `./customFiles:/customFiles` *(Custom logos and branding)*

*Note: All persistent data is saved locally in this folder. To back up this service, simply copy the entire `stirling-pdf` directory.*

---

## 🔄 Updates

This service follows the **Standard Update Routine**. 

Please refer to the [Main README](../README.md#🔄-updating-services-standard-routine) in the root of the repository for step-by-step update instructions. 

*(No special update steps or database migrations are typically required for Stirling PDF).*
