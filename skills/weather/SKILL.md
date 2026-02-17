---
name: weather
description: Get current weather and forecasts (no API key required).
metadata:
  {
    "openclaw":
      {
        "emoji": "🌤️",
        "requires": {},
      },
  }
---

# Weather Skill

Einfacher Wetter-Skill ohne API-Key. Nutzt wttr.in für Wetterdaten.

## Verwendung

```bash
# Aktuelles Wetter
exec curl -s "wttr.in/Berlin?format=3"

# Detaillierte Vorhersage
exec curl -s "wttr.in/Berlin"

# Nur Temperatur
exec curl -s "wttr.in/Berlin?format=%t"

# JSON Format für Automatisierung
exec curl -s "wttr.in/Berlin?format=j1"
```

## Parameter

| Parameter | Beschreibung | Beispiel |
|-----------|--------------|----------|
| `location` | Stadt oder Koordinaten | Berlin, London, 48.1,11.6 |
| `format` | Ausgabeformat | 1=kurz, 2=lang, j1=json |

## Beispiel-Output

```
Berlin: ⛅️  +12°C
```

## Integration mit OpenClaw

Der Agent kann Wetterabfragen direkt ausführen:

```
User: "Wie ist das Wetter in München?"
Agent: exec curl -s "wttr.in/München?format=3"
```

## Links

- **wttr.in:** https://github.com/chubin/wttr.in
