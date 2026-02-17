---
name: email
description: Email management and automation. Send, read, search, and organize emails.
metadata:
  {
    "openclaw":
      {
        "emoji": "📧",
        "requires": {},
      },
  }
---

# Email Skill

E-Mail Management und Automatisierung. Unterstützt SMTP zum Senden und IMAP zum Empfangen.

## SMTP-Konfiguration (Senden)

```yaml
# config.yaml
skills:
  email:
    smtp:
      host: smtp.gmail.com      # oder smtp.ionos.de, etc.
      port: 587                 # 587 für STARTTLS, 465 für SSL
      secure: true
      user: deine@email.de
      # Passwort aus Umgebungsvariable oder Passwort-Manager
      password: "${EMAIL_PASSWORD}"
    default_from: "deine@email.de"
    default_name: "Dein Name"
```

## IMAP-Konfiguration (Empfangen)

```yaml
# config.yaml
skills:
  email:
    imap:
      host: imap.gmail.com
      port: 993
      secure: true
      user: deine@email.de
      password: "${EMAIL_PASSWORD}"
```

## Verwendung

### E-Mail senden

```bash
# Einfache E-Mail
message send --target user@example.com --message "Hallo!"

# Mit Betreff
message send --target user@example.com --message "Hallo!" --subject "Wichtig"

# Mit Anhang
message send --target user@example.com --message "Siehe Anhang" --filePath document.pdf
```

### E-Mail lesen

```bash
# Ungelesene E-Mails prüfen
email check --unread

# Letzte E-Mails anzeigen
email list --limit 10

# E-Mails suchen
email search --query "from:boss@company.com"
```

## Provider-Beispiele

### Gmail

```yaml
smtp:
  host: smtp.gmail.com
  port: 587
  secure: true
imap:
  host: imap.gmail.com
  port: 993
  secure: true
```

**Hinweis:** Für Gmail musst du ein [App-Passwort](https://myaccount.google.com/apppasswords) erstellen.

### Ionos (1&1)

```yaml
smtp:
  host: smtp.ionos.de
  port: 587
  secure: true
imap:
  host: imap.ionos.de
  port: 993
  secure: true
```

### Outlook/Office365

```yaml
smtp:
  host: smtp.office365.com
  port: 587
  secure: true
imap:
  host: outlook.office365.com
  port: 993
  secure: true
```

## Automatisierung

### Cron-Job für E-Mail-Prüfung

```yaml
# In HEARTBEAT.md oder cron job
cron:
  - name: "Email Check"
    schedule: "every 30m"
    action: "email check --unread --notify"
```

### Auto-Responder

```javascript
// Beispiel: Auto-Reply für bestimmte Absender
if (email.from.includes("newsletter")) {
  email.moveToFolder("Newsletter");
}
```

## Sicherheit

⚠️ **Wichtig:**
- **Niemals** Passwörter in Config-Dateien speichern
- Verwende Umgebungsvariablen: `export EMAIL_PASSWORD="..."`
- Oder besser: Passwort-Manager Integration
- App-Passwörter statt Hauptpasswörter verwenden

## Troubleshooting

### "Authentication failed"
- Prüfe Benutzername und Passwort
- Für Gmail: App-Passwort erforderlich
- Für Outlook: Modern Auth möglicherweise nötig

### "Connection refused"
- Firewall prüfen
- Richtigen Port verwenden (587 vs 465)
- SSL/TLS Einstellungen prüfen

## Links

- **Nodemailer (SMTP):** https://nodemailer.com
- **Gmail App-Passwörter:** https://myaccount.google.com/apppasswords
