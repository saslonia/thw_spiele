# Beitragen zu THW Spiele

Herzlich willkommen! Ob neue Fragen, Bugfixes oder ein komplett neues Spiel – alle Beiträge sind willkommen.

## Fragen beisteuern (kein Code nötig)

1. Repo forken (oder direkt im Browser bearbeiten)
2. Neue YAML-Datei in `configs/<spielname>/` anlegen
3. Pull Request erstellen

Format-Referenz: [games/wer-wird-millionaer/README.md](games/wer-wird-millionaer/README.md)

> **Tipp:** Für beide Spiele gibt es einen Fragen-Manager: [Wer wird Millionär?](tools/wer-wird-millionaer-fragen-manager/) und [Jeopardy!](tools/jeopardy-fragen-manager/) – Web-Oberfläche zum Erstellen von Fragendateien, kein manuelles YAML-Schreiben nötig.

## Bugfixes & Verbesserungen

1. Issue erstellen oder bestehendes Issue kommentieren
2. Repo forken, Branch erstellen, Änderung implementieren
3. Pull Request mit kurzer Beschreibung öffnen

## Neues Spiel hinzufügen

→ Detaillierte Anleitung: [docs/neues-spiel-erstellen.md](docs/neues-spiel-erstellen.md)

## Code-Konventionen

- **Sprache:** Code und Kommentare auf Englisch, Benutzeroberfläche auf Deutsch
- **Architektur:** Jedes Spiel ist eine einzige `index.html`-Datei (HTML, CSS, JS und Bibliotheken inline)
- **Keine externen Abhängigkeiten** zur Laufzeit – alles muss offline funktionieren
- **YAML** als Config-Format für Spielinhalte; Variante und Spielstand gehören in `game_state`, nicht in die Config
- Bibliotheken (js-yaml) werden **inline eingebettet** (MIT-lizenziert)
- Kein `eval()`, kein dynamisches `<script>`-Einfügen – kein XSS-Risiko
- Ungültige Config-Dateien erzeugen eine verständliche Fehlermeldung, keinen Absturz

## Verzeichnisstruktur

```
games/<spielname>/index.html      # Das Spiel (alles inline)
games/<spielname>/README.md       # Spielanleitung + Config-Format
configs/<spielname>/<name>.yaml   # Spielkonfigurationen
tools/<spielname>/index.html      # Hilfswerkzeuge (z.B. Fragen-Editor), optional
docs/                             # Projektweite Anleitungen
```
