📘 HANDBUCH – Fonds‑CrowdFunding & DB‑Master
Technische Dokumentation – Architektur, Struktur, Komponenten & Systemlogik

---

🧩 Inhalt

1. Frontend‑Repository Struktur  
2. DB‑Master‑Serverstruktur (lokal, privat)  
3. Funktionsbeschreibung aller Dateien  
4. Systemlogik & Zusammenspiel der Komponenten

Dieses Dokument dient als technische Grundlage für:

- Betrieb  
- Weiterentwicklung  
- Audits  
- institutionelle Validierung  
- interne Qualitätssicherung  

---

1️⃣ Frontend‑Repository: Fonds-CrowdFunding-main

📁 Strukturübersicht

```text
Fonds-CrowdFunding-main/
├── index.html
├── assets/
│   ├── css/
│   │   └── style.css
│   └── js/
│       └── script.js
├── backend-examples/
│   ├── python/
│   │   └── donate_api.py
│   ├── php/
│   │   └── donate.php
│   └── cpp/
│       ├── donation_service.cpp
│       └── axiom_check.cpp
├── .config
├── .yml
├── LICENSE
├── NOJEKYLL
├── README.md
├── package-lock.json
```

📝 Beschreibung

Das Frontend‑Repository ist:

- öffentlich  
- GitHub‑Pages‑fähig  
- rein statisch  
- ohne sensible Daten  
- UI‑Layer für Nutzerinteraktion

Es bildet die Präsentationsschicht des Systems.

---

2️⃣ DB‑Master‑Serverstruktur (lokal, privat, isoliert)

📁 Strukturübersicht

```text
C:\MASTERPROJEKTORDNERSICHER\MEINESICHEREDB\DBFonds-CrowdFunding\
├── data_storage.json
├── transactions.txt
├── backups/
│   └── (zeitgestempelte Snapshots)
├── auto_sync.bat
├── master_start.bat
├── start_bridge.bat
├── Axiom_Start.bat
├── watchdog.py
├── python.py
├── cd
├── notepad
```

📝 Beschreibung

Diese Struktur ist:

- kein Repository  
- nicht öffentlich  
- nicht synchronisiert  
- nur lokal auf deinem Master‑Laptop  
- enthält sensible Daten & interne Logik  
- stellt den privaten Serverkern dar

Sie bildet die Daten‑ und Logikschicht des Systems.

---

3️⃣ Funktionsbeschreibung aller Dateien

---

🔵 Frontend‑Repository – Dateirollen

index.html
Rolle:  
Zentrale Benutzeroberfläche der Crowdfunding‑Plattform.

Funktionen:  
- Spendenformular  
- Fortschrittsanzeige  
- Unterstützerliste  
- Einbindung von CSS & JS  
- GitHub‑Pages‑kompatibel

---

assets/css/style.css
Rolle:  
Visuelle Gestaltung.

Funktionen:  
- Layout  
- Farben  
- Buttons  
- Progress‑Bar  
- Responsive‑Design  
- Corporate Identity

---

assets/js/script.js
Rolle:  
Client‑seitige Logik.

Funktionen:  
- Demo‑Spenden via localStorage  
- Fortschrittsberechnung  
- UI‑Updates  
- Grundlage für API‑Integration

---

backend-examples/python/donate_api.py
Rolle:  
Beispiel‑API.

Funktionen:  
- POST /api/donate  
- GET /api/donations  
- Vorlage für echten Serverbetrieb

---

backend-examples/php/donate.php
Rolle:  
PHP‑Spendenendpoint.

Funktionen:  
- JSON‑Input  
- Validierung  
- Antwort  
- Für klassische Webserver

---

backend-examples/cpp/donation_service.cpp
Rolle:  
High‑Performance‑Backend‑Stub.

Funktionen:  
- Platzhalter für Payment‑Integration  
- C++‑Basis für spätere Optimierungen

---

backend-examples/cpp/axiom_check.cpp
Rolle:  
Axiomatische Prüfungen.

Funktionen:  
- Datenintegrität  
- Hash‑Vergleiche  
- Validierungsregeln

---

.config
Konfiguration für Build, Deployment oder lokale Einstellungen.

---

.yml
GitHub Actions Workflow für automatisierte Deployments.

---

LICENSE
Regelt Nutzung & Weitergabe.

---

NOJEKYLL
Erzwingt statische Auslieferung auf GitHub Pages.

---

README.md
Dokumentation des Frontend‑Repos.

---

package-lock.json
Deterministische Node‑Abhängigkeiten.

---

4️⃣ DB‑Master – Dateirollen (lokal, privat)

---

data_storage.json
Rolle:  
Zentrale JSON‑Datenbank.

Inhalt:  
- Benutzer  
- Wallets  
- Rollen  
- Salden  
- Systemparameter  

Funktion:  
Grundlage für Fonds‑Logik & Runden.

---

transactions.txt
Rolle:  
Revisionssicheres Transaktionslog.

Funktion:  
- Zeitstempel  
- Historie  
- Audit‑fähig

---

backups/
Rolle:  
Wiederherstellung & Historisierung.

Funktion:  
- Snapshots  
- Archivierung  
- optional verschlüsselt

---

auto_sync.bat
Rolle:  
Automatischer Prozessstarter.

Funktion:  
- interne Syncs  
- Backups  
- Trigger

---

master_start.bat
Rolle:  
Startpunkt des gesamten Systems.

Funktion:  
- Initialisierung  
- Variablen  
- Pfade  
- Start von Bridge/Watchdog/API

---

start_bridge.bat
Rolle:  
Verbindung zwischen Frontend & DB‑Master.

Funktion:  
- API starten  
- Node‑Bridge starten  
- WebSocket‑Verbindungen

---

Axiom_Start.bat
Rolle:  
Axiomatische Prüfungen.

Funktion:  
- Datenintegrität  
- Logikkonsistenz  
- Round‑Validierung  
- Hash‑Vergleiche

---

watchdog.py
Rolle:  
Überwachung & Trigger.

Funktion:  
- Dateiänderungen erkennen  
- automatische Backups  
- interne Trigger

---

python.py
Rolle:  
Logikmodul.

Funktion:  
- Wallet‑Checks  
- Hashing  
- Validierung  
- API‑Erweiterungen

---

cd
Rolle:  
Steuerdatei / Shortcut.

---

notepad
Rolle:  
Freiform‑Notizen & Meta‑Informationen.

---

5️⃣ Systemlogik – Zusammenspiel

Frontend (öffentlich)
- UI  
- Spendenannahme (Demo/API)  
- Fortschritt  
- Unterstützerliste  

DB‑Master (lokal, privat)
- Datenhaltung  
- Validierung  
- Backups  
- interne Logik  

Bridge (lokal)
- verbindet Frontend ↔ DB‑Master  
- läuft nur auf deinem Laptop  
- keine Cloud‑Abhängigkeit  







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

