# OpenClaw Installation Guide

Ein umfassender Guide zur Installation und Einrichtung von OpenClaw mit Beispiel-Skills.

## Was ist OpenClaw?

OpenClaw ist ein persönlicher KI-Assistent, der direkt auf deinem System läuft. Er hat Zugriff auf deine Dateien, Tools und kann mit verschiedenen Diensten interagieren.

**GitHub:** https://github.com/openclaw/openclaw  
**Dokumentation:** https://docs.openclaw.ai  
**Community:** https://discord.com/invite/clawd

---

## Schnellstart

```bash
# 1. Repository klonen
git clone https://github.com/openclaw/openclaw.git
cd openclaw

# 2. Abhängigkeiten installieren
npm install

# 3. Konfiguration erstellen
cp config.example.yaml config.yaml
# → Bearbeite config.yaml mit deinen Einstellungen

# 4. OpenClaw starten
npm start
```

---

## Verfügbare Skills

### 🔧 System & Dateien

| Skill | Beschreibung |
|-------|--------------|
| `read` | Dateien lesen (Text, Bilder) |
| `write` | Dateien erstellen/überschreiben |
| `edit` | Präzise Textänderungen |
| `exec` | Shell-Befehle ausführen |

### 🌐 Web & Recherche

| Skill | Beschreibung |
|-------|--------------|
| `web_search` | Websuche mit Brave API |
| `web_fetch` | Inhalte von URLs extrahieren |
| `browser` | Browser-Automatisierung |

### 💬 Kommunikation

| Skill | Beschreibung |
|-------|--------------|
| `message` | Nachrichten senden (Telegram, Discord, etc.) |
| `email` | E-Mails senden und empfangen |
| `tts` | Text-to-Speech |

### ⚡ Produktivität

| Skill | Beschreibung |
|-------|--------------|
| `cron` | Erinnerungen und geplante Aufgaben |
| `sessions_spawn` | Sub-Agenten für komplexe Aufgaben starten |
| `canvas` | UI-Canvas für visuelle Aufgaben |

### 🔐 Sicherheit

| Skill | Beschreibung |
|-------|--------------|
| `passbolt` | Passwort-Manager Integration |
| `passbolt-cli` | CLI-Zugriff auf Passwörter |

---

## Repository-Struktur

```
openclaw-guide/
├── README.md              # Dieser Guide
├── skills/                # Beispiel-Skills
│   ├── weather/           # Wetter-Skill
│   ├── github/            # GitHub Integration
│   └── email/             # Email-Skill
└── examples/              # Nutzungsbeispiele
    └── basic-commands.md
```

---

## Sicherheitshinweise

⚠️ **Wichtig:**

- Speichere Passwörter **immer** in einem Passwort-Manager (z.B. Passbolt), nie in Config-Dateien
- API-Keys gehören in Umgebungsvariablen oder den Passwort-Manager
- Private Keys niemals committen
- Konfigurationsdateien mit sensiblen Daten mit `chmod 600` schützen

---

## Nächste Schritte

1. 📁 Sieh dir die [Beispiel-Skills](./skills/) an
2. 📖 Lies die `SKILL.md` Dateien der Skills, die du nutzen möchtest
3. ⚙️ Konfiguriere die benötigten API-Keys und Zugänge
4. 🚀 Teste die wichtigsten Skills

---

## Support

- **Dokumentation:** https://docs.openclaw.ai
- **Community:** https://discord.com/invite/clawd
- **GitHub:** https://github.com/openclaw/openclaw
