---
name: github
description: Interact with GitHub using the gh CLI.
metadata:
  {
    "openclaw":
      {
        "emoji": "🐙",
        "requires": { "bins": ["gh"] },
        "install":
          [
            {
              "id": "brew",
              "kind": "brew",
              "formula": "gh",
              "bins": ["gh"],
              "label": "Install GitHub CLI (brew)",
            },
            {
              "id": "apt",
              "kind": "apt",
              "package": "gh",
              "bins": ["gh"],
              "label": "Install GitHub CLI (apt)",
            },
          ],
      },
  }
---

# GitHub Skill

Integration mit GitHub über die offizielle GitHub CLI (`gh`).

## Installation

```bash
# macOS
brew install gh

# Ubuntu/Debian
curl -fsSL https://cli.github.com/packages/githubcli-archive-keyring.gpg | sudo dd of=/usr/share/keyrings/githubcli-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/githubcli-archive-keyring.gpg] https://cli.github.com/packages stable main" | sudo tee /etc/apt/sources.list.d/github-cli.list > /dev/null
sudo apt update
sudo apt install gh
```

## Authentifizierung

```bash
# Einmalig anmelden
gh auth login

# Mit Token (für CI/CD)
gh auth login --with-token < token.txt
```

## Verwendung

### Repositories

```bash
# Repository klonen
exec gh repo clone owner/repo

# Repository erstellen
exec gh repo create my-project --public

# Repository-Info anzeigen
exec gh repo view owner/repo
```

### Pull Requests

```bash
# PRs auflisten
exec gh pr list --repo owner/repo

# PR erstellen
exec gh pr create --title "Fix bug" --body "Description"

# PR Checks anzeigen
exec gh pr checks 55 --repo owner/repo

# PR mergen
exec gh pr merge 55 --squash
```

### Issues

```bash
# Issues auflisten
exec gh issue list --repo owner/repo

# Issue erstellen
exec gh issue create --title "Bug report" --body "Description"

# Issue schließen
exec gh issue close 123 --repo owner/repo
```

### Actions/Workflows

```bash
# Workflows auflisten
exec gh run list --repo owner/repo --limit 10

# Workflow-Logs anzeigen
exec gh run view <run-id> --repo owner/repo --log-failed
```

## API-Zugriff

Für erweiterte Operationen:

```bash
# API-Abfrage
exec gh api repos/owner/repo/pulls/55 --jq '.title, .state'

# Mit JSON-Output
exec gh api user/repos --jq '.[] | "\(.name): \(.description)"'
```

## Konfiguration

```yaml
# ~/.config/gh/config.yml
git_protocol: https
editor: vim
prompt: enabled
pager: less
```

## Sicherheit

⚠️ **Wichtig:**
- `gh auth login` speichert Token sicher im Keyring
- Für Scripts: Verwende `GH_TOKEN` Umgebungsvariable
- Token niemals in Code committen!

## Links

- **GitHub CLI:** https://cli.github.com
- **Dokumentation:** https://cli.github.com/manual
