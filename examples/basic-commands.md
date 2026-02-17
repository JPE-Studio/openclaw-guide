# OpenClaw Beispiel-Befehle

Diese Datei zeigt typische Anwendungsfälle für OpenClaw-Skills.

---

## 🌤️ Wetter

```bash
# Aktuelles Wetter anzeigen
Wie ist das Wetter in Berlin?
→ exec curl -s "wttr.in/Berlin?format=3"

# Wettervorhersage
Wettervorhersage für München die nächsten 3 Tage
→ exec curl -s "wttr.in/München" | head -20
```

---

## 🐙 GitHub

```bash
# Repository-Status prüfen
Status vom neovie-dev/website repo
→ exec gh repo view neovie-dev/website

# Offene PRs anzeigen
Zeige meine offenen Pull Requests
→ exec gh pr list --state open --author @me

# Letzte Workflow-Runs
Letzte CI-Runs im Repo anzeigen
→ exec gh run list --limit 5
```

---

## 📧 E-Mail

```bash
# E-Mail senden
Sende E-Mail an team@company.com mit Betreff "Meeting morgen"
→ message send --target team@company.com --subject "Meeting morgen" --message "..."

# Ungelesene E-Mails
Hast du neue E-Mails?
→ email check --unread
```

---

## 🔍 Web-Recherche

```bash
# Websuche
Suche nach OpenClaw Dokumentation
→ web_search query="OpenClaw documentation"

# URL-Inhalt extrahieren
Lies den Inhalt von example.com
→ web_fetch url="https://example.com"
```

---

## ⏰ Erinnerungen (Cron)

```bash
# Erinnerung in 30 Minuten
Erinnere mich in 30 Minuten an das Meeting
→ cron add --schedule "in 30m" --message "Meeting beginnt!"

# Tägliche Erinnerung
Erinnere mich jeden Tag um 9 Uhr an Daily Standup
→ cron add --schedule "cron 0 9 * * *" --message "Daily Standup!"
```

---

## 📁 Datei-Operationen

```bash
# Datei lesen
Zeige mir den Inhalt von README.md
→ read file_path="README.md"

# Datei erstellen
Erstelle eine neue Datei notes.txt mit "Wichtige Notizen"
→ write file_path="notes.txt" content="Wichtige Notizen"

# Datei bearbeiten
Füge eine Zeile zu config.yaml hinzu
→ edit file_path="config.yaml" old_string="key: value" new_string="key: new_value"
```

---

## 🖥️ System-Befehle

```bash
# Disk-Nutzung
Wie viel Speicherplatz ist noch frei?
→ exec df -h

# Prozesse
Zeige laufende Node-Prozesse
→ exec ps aux | grep node

# Dateien finden
Finde alle .log Dateien im aktuellen Verzeichnis
→ exec find . -name "*.log" -type f
```

---

## 🤖 Sub-Agenten

```bash
# Komplexe Aufgabe delegieren
Analysiere dieses Projekt und erstelle eine Zusammenfassung
→ sessions_spawn task="Analysiere das Projekt im aktuellen Verzeichnis..."
```

---

## Tipps & Tricks

1. **Kombiniere Skills:** 
   ```
   Suche nach Wetter in Berlin und sende es per E-Mail
   ```

2. **Verwende Pipes:**
   ```
   exec curl -s "wttr.in/Berlin?format=3" | tee weather.txt
   ```

3. **Automatisierung mit Heartbeat:**
   - Trage regelmäßige Aufgaben in `HEARTBEAT.md` ein
   - OpenClaw prüft diese automatisch

4. **Sicherheit:**
   - Sensitive Daten immer in Passbolt speichern
   - API-Keys in Umgebungsvariablen oder Config-Dateien mit `chmod 600`
