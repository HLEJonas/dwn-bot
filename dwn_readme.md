# Diamond Wings Nation Discord Bot ◆

## Commands
| Command | Beschreibung |
|---|---|
| `/rangsystem` | Zeigt alle 9 Ränge |
| `/anforderungen` | Zeigt Beitrittsvoraussetzungen |
| `/clubregeln` | Zeigt den DWN-Kodex |
| `/clubinfo` | Allgemeine Club-Infos |
| `/ctidee` | Zufällige Clubtreffen-Idee |
| `/diamant` | Zufälliges Diamanten-Zitat |
| `/pferdename` | Generiert einen Pferdenamen |

---

## Setup

### Schritt 1 — Bot auf Discord erstellen
1. Geh auf https://discord.com/developers/applications
2. "New Application" → Name: "DWN Bot"
3. Links auf "Bot" → "Add Bot"
4. Token kopieren (geheim halten!)
5. Unter "Privileged Gateway Intents" → alle drei aktivieren
6. Links auf "OAuth2" → "URL Generator"
7. Scopes: `bot` + `applications.commands`
8. Bot Permissions: `Send Messages`, `Use Slash Commands`, `Embed Links`
9. Generierten Link öffnen → Bot zu deinem Server einladen

### Schritt 2 — Railway.app Hosting
1. Geh auf https://railway.app
2. Mit GitHub einloggen (kostenlos)
3. "New Project" → "Deploy from GitHub repo"
4. Diese Dateien in ein GitHub Repository hochladen
5. Bei Railway: Variables → `DISCORD_TOKEN` = dein Bot-Token einfügen
6. Deploy klicken → Bot läuft 24/7!

### Schritt 3 — Lokal testen (optional)
```bash
pip install -r requirements.txt
set DISCORD_TOKEN=dein_token_hier
python bot.py
```
