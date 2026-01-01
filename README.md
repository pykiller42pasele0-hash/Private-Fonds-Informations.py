# Private-Fonds-Informations.py

---

# 📘 AXIOM MASTER-HANDBUCH: Fonds-CrowdFunding

Dieses Handbuch dokumentiert die autonome Brücke zwischen dem **Frontend (GitHub)** und dem **Backend (Lokaler DB-Kern)**.

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
| `%db%` | `C:\...\DB_Fonds-CrowdFunding` | `server_logic.py`, `data_storage.json`, `transactions.log` |
| `%src%` | `C:\Fonds-CrowdFunding-main` | `index.html`, `assets/js/script.js`, `backend-examples/` |

---

## 💻 Zentrale Kommandos (CMD / PowerShell)

### Schnell-Navigation (Strings)

Um diese Kürzel zu nutzen, muss die `Axiom_Start.bat` oder das `set`-Kommando ausgeführt worden sein.

* **Gehe zu Backend:** `cd /d %db%`
* **Gehe zu Frontend:** `cd /d %src%`

### Editor-Direktzugriff

* **Server-Logik:** `notepad %db%\server_logic.py`
* **Frontend-JS:** `notepad %src%\assets\js\script.js`
* **C++ Validator:** `notepad %src%\backend-examples\cpp\axiom_check.cpp`

---

## ⚙️ Kern-Logiken

### 1. BTC & Referral Axiom (25% Provision)

Die Berechnung erfolgt über C-Datentypen, um Rundungsfehler im mBTC-Bereich zu verhindern.

* **Rate:**  (25%)
* **BTC-Fixpreis:**  € (Axiomatischer Wert für Testphase)
* **Formel:** 


### 2. Energie-Metrik (Sats/vByte)

Jeder State-Shift (Admin-Update) erzeugt eine Testnet-Signatur im Log:
`[TIMESTAMP] AXIOM_REWARD: Energy used: 375.0 Test-Sats`

---

## 🚀 Deployment-Workflow

Wenn du Änderungen am Code vornimmst, folge immer dieser Kette:

1. **Code ändern:** `notepad ...`
2. **Server Neustart (Fenster 1):** `STRG+C` -> `python server_logic.py`
3. **Git-Push (Fenster 3):**
```bash
git add .
git commit -m "Axiom Update: [Beschreibung]"
git push origin main

```



---

## 🛠 Troubleshooting (Fehlerbehebung)

* **"Not Found" (404):** Der Tunnel steht, aber die URL im Browser ist falsch. Nur `/api/sync` ist ein gültiger Endpunkt.
* **"Login Failed":** Prüfe, ob die `TUNNEL_URL` in der `script.js` noch mit der URL in Fenster 2 übereinstimmt.
* **Tunnel-Passwort:** Falls gefragt, gib deine öffentliche IP an (Befehl: `curl ifconfig.me`).

---

## 📝 Zukünftige Mainnet-Transformation

Um das Handbuch für die Veröffentlichung (Public) vorzubereiten, müssen folgende Punkte erfüllt sein:

1. [ ] Real-time BTC Price API Integration.
2. [ ] OAuth / JWT Authentifizierung für den Admin-Bereich.
3. [ ] Multi-Node Validierung des `transactions.log`.

---

