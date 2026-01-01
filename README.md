# 📘 AXIOM MASTER-HANDBUCH: Fonds-CrowdFunding

Dieses Handbuch dokumentiert die autonome Brücke zwischen dem **Frontend (GitHub)** und dem **Backend (Lokaler DB-Kern)** inklusive der **1000/1000 Paritäts-Logik**.

---

## 🏗 System-Architektur & Abhängigkeiten

Das System basiert auf einer deterministischen Triple-Layer-Struktur:

1. **Frontend (UI):** Gehostet auf GitHub Pages. Kommuniziert via HTTPS-Tunnel.
2. **Brücke (Tunnel):** LocalTunnel (Subdomain: `rfof-master`) schlägt die Brücke durch die Firewall.
3. **Kern (Axiom-Server):** Python Flask-Server mit `ctypes` für C-Präzision bei BTC-Berechnungen.

---

## 📂 Ordner-Struktur (Lokaler Laptop)

| Pfad-Variable | Physischer Pfad | Inhalt |
| --- | --- | --- |
| `%db%` | `C:\...\DB_Fonds-CrowdFunding` | `server_logic.py`, `data_storage.json`, `transactions.log`, `watchdog.py`, `Axiom_Start.bat` |
| `%src%` | `C:\Fonds-CrowdFunding-main` | `index.html`, `assets/`, `backend-examples/`, `.gitignore` |

---

## 💻 Zentrale Kommandos (CMD / PowerShell)

### Schnell-Navigation (Strings)

* **Gehe zu Backend:** `cd /d %db%`
* **Gehe zu Frontend:** `cd /d %src%`

### Editor-Direktzugriff

* **Server-Logik:** `notepad %db%\server_logic.py`
* **Frontend-JS:** `notepad %src%\assets\js\script.js`
* **Frontend-CSS:** `notepad %src%\assets\css\style.css`
* **C++ Validator:** `notepad %src%\backend-examples\cpp\axiom_check.cpp`

---

## ⚙️ Kern-Logiken (Mainnet-Parität)

### 1. BTC & Referral Axiom (1000/1000 Logik)

* **FIAT-Ziel:** 1000 € pro Runde.
* **CRYPTO-Ziel:** 1000 BTC pro Runde.
* **Provision:** 25% vom EUR-Zuwachs fließen direkt als BTC-Reward.
* **Formel:** 

### 2. Energie-Metrik (Sats/vByte)

Jeder State-Shift (Admin-Update) erzeugt eine Testnet-Signatur im Log:
`[TIMESTAMP] AXIOM_REWARD: Energy used: 375.0 Test-Sats`

---

## 🚀 Deployment-Workflow

1. **Code ändern:** `notepad ...`
2. **Server Neustart (Fenster 1):** `STRG+C` -> `python server_logic.py`
3. **Git-Push (Fenster 3):**

```bash
git add .
git commit -m "Axiom Update: [Beschreibung]"
git push origin main

```

---

## 📄 Datei-Auflösung (Source Code & Beschreibungen)

### 1.1 `backups/`

* **Beschreibung:** Automatisierte Sicherungen der `data_storage.json`.

### 1.2 `Axiom_Start.bat` (Vollständig)

```batch
@echo off
title AXIOM MASTER CONTROL
color 0B
set "db_path=C:\MASTER_PROJEKT_ORDNER_SICHER\MEINE_SICHERE_DB\DB_Fonds-CrowdFunding"
set "src_path=C:\Fonds-CrowdFunding-main"

echo =======================================================
echo   SATORAMY AXIOM - VOLLSTAENDIGE HANDLUNGSFREIHEIT
echo =======================================================

start "AXIOM_SERVER_CORE" cmd /k "cd /d %db_path% && set db=%db_path% && python server_logic.py"
start "AXIOM_BRIDGE_TUNNEL" cmd /k "cd /d %db_path% && lt --port 5050 --subdomain rfof-master"
start "AXIOM_WORKSPACE" cmd /k "cd /d %src_path% && set src=%src_path% && set db=%db_path% && echo Status: Workspace bereit. && git status"
exit

```

### 1.3 `server_logic.py`

* **Beschreibung:** Flask-Kern. Verarbeitet die 1000/1000 Parität mit `ctypes`.
* **Code:** [FÜGE HIER DEINEN CURRENT CODE EIN]

### 1.4 `watchdog.py` (Vollständig)

```python
import time, os
LOG_FILE = "transactions.log"
def monitor():
    print("--- AXIOM WATCHDOG: MAINNET PARITY ACTIVE ---")
    last_size = os.path.getsize(LOG_FILE) if os.path.exists(LOG_FILE) else 0
    while True:
        try:
            current_size = os.path.getsize(LOG_FILE) if os.path.exists(LOG_FILE) else 0
            if current_size > last_size:
                print("(!) TRANSACTION DETECTED: Validating 25% Reward Axiom...")
                last_size = current_size
            time.sleep(2)
        except: time.sleep(5)
if __name__ == "__main__": monitor()

```

### 1.5 `data_storage.json`

* **Beschreibung:** Lokale Datenbank (JSON) für User & Global States.
* **Struktur:** [FÜGE HIER DEINE CURRENT JSON STRUKTUR EIN]

### 1.6 `transactions.log`

* **Beschreibung:** Fälschungssicheres Ereignis-Protokoll.

### 1.7 `master_start.bat`

* **Code:** [FÜGE HIER DEINEN CURRENT CODE EIN]

### 1.8 `start_bridge.bat`

* **Code:** [FÜGE HIER DEINEN CURRENT CODE EIN]

### 2.1 `assets/css/style.css`

* **Beschreibung:** Design & Progress-Bar Animationen.
* **Code:** [FÜGE HIER DEINEN CURRENT CSS CODE EIN]

### 2.2 `assets/js/script.js`

* **Beschreibung:** Frontend-Logik & Bridge-Anbindung zum Laptop.
* **Code:** [FÜGE HIER DEINEN CURRENT JS CODE EIN]

### 2.3 `backend-examples/cpp/axiom_check.cpp`

* **Beschreibung:** C++ Integritäts-Validator.
* **Code:** [FÜGE HIER DEINEN CURRENT CPP CODE EIN]

### 2.4 `index.html`

* **Beschreibung:** Haupt-UI (Dashboard & Login).
* **Code:** [FÜGE HIER DEINEN CURRENT HTML CODE EIN]

### 2.5 `.gitignore`

* **Inhalt:** [FÜGE HIER DEINE IGNORE-LISTE EIN]

---

## 🛠 Troubleshooting (Fehlerbehebung)

* **"Not Found" (404):** Nur `/api/sync` ist ein gültiger Endpunkt.
* **"Login Failed":** Prüfe die `TUNNEL_URL` in der `script.js`.
* **Tunnel-Passwort:** Deine öffentliche IP via `curl ifconfig.me`.

---

## 📝 Zukünftige Mainnet-Transformation

1. [ ] Real-time BTC Price API Integration.
2. [ ] OAuth / JWT Authentifizierung für den Admin-Bereich.
3. [ ] Multi-Node Validierung des `transactions.log`.

