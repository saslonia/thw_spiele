# THW Spiele – Agent Instructions

## Projektübersicht
Sammlung von Browser-basierten Quiz- und Partyspielen für THW-Veranstaltungen. Alle Spiele laufen vollständig lokal ohne Internet oder Server.

## Architektur-Prinzipien

### Single-File Spiele
- Jedes Spiel ist **eine einzige `index.html`-Datei**
- HTML, CSS, JavaScript und externe Bibliotheken sind alle inline eingebettet
- Kein Build-System, keine Package-Manager, keine Node.js-Abhängigkeiten
- Zielpersonen sind Nicht-Techniker: Doppelklick auf die Datei muss genügen

### YAML als Config-Format
- Spielinhalte (Fragen, Texte, etc.) werden als YAML-Dateien bereitgestellt
- Der Spieler lädt die YAML-Datei im Browser per Datei-Upload (Drag & Drop oder Klick)
- js-yaml 4.1.0 (MIT) wird inline in die HTML-Datei eingebettet
- Spielstand wird ebenfalls als YAML exportiert/importiert

### Spielzustand vs. Spielinhalt
- **Config-Datei** enthält: Fragen, Antworten, Joker-Texte, Titel, Beschreibung
- **Spielstand (game_state)** enthält: aktueller Fortschritt, gewählte Variante, verbrauchte Joker
- Spielstand wird in der `game_state`-Sektion der Config-YAML eingebettet und als neue Datei exportiert
- Die **Spielvariante** wird vom Spieler beim Start selbst gewählt, nicht in der Config definiert; sie ist Teil des game_state

## Verzeichnisstruktur

```
games/<spielname>/
  index.html          # Das vollständige Spiel (alles inline)
  README.md           # Spielanleitung + Config-Format-Dokumentation
configs/<spielname>/
  beispiel.yaml       # Minimales Beispiel als Vorlage mit Kommentaren
  *.yaml              # Weitere fertige Konfigurationen
docs/
  neues-spiel-erstellen.md  # Anleitung für neue Spiele
```

## Bestehende Spiele

### Wer wird Millionär? (`games/wer-wird-millionaer/`)
- 15 Fragen, klassisches Multiple-Choice-Format (A/B/C/D)
- Zwei Varianten: Klassisch (3 Joker, 2 Sicherheitsstufen) oder Risiko (4 Joker, 1 Sicherheitsstufe)
- **Variantenwahl durch den Spieler beim Spielstart** – nicht in der Config, sondern im game_state gespeichert
- Joker: 50:50, Publikum, Telefon, Zusatzjoker (nur Risiko)
- Publikumsjoker-Prozente kommen aus der YAML-Config (Fallback: zufällige Simulation)
- Sicherheitsstufen: 1.000 € (Frage 5) immer; 16.000 € (Frage 9) nur in Classic
- Gewinnstufen: 100, 200, 300, 500, 1.000, 2.000, 4.000, 8.000, 16.000, 32.000, 64.000, 125.000, 250.000, 500.000, 1.000.000 €

### YAML-Config-Format (Wer wird Millionär)
```yaml
title: "Spieltitel"
description: "Optionale Beschreibung"

questions:                         # Genau 15 Fragen
  - question: "Fragetext?"
    answers: ["A-Text", "B-Text", "C-Text", "D-Text"]
    correct: 0                     # Index 0-3 (0=A, 1=B, 2=C, 3=D)
    jokers:                        # Optional
      audience: [72, 12, 9, 7]    # Publikums-% für A, B, C, D
      phone: "Hinweistext"
      additional: "Hinweistext"

game_state:                        # Optional – beim Speichern automatisch hinzugefügt
  current_question: 5              # 0-basiert
  variant: "risk"                  # "risk" oder "classic"
  jokers_used: ["fifty_fifty"]
```

## Code-Konventionen
- **Sprache**: Code/Variablen/Kommentare auf **Englisch**, UI-Texte auf **Deutsch**
- Keine TypeScript, keine Frameworks (nur Vanilla JS)
- Keine externen CDN-Calls zur Laufzeit
- Bibliotheken: MIT-lizenziert, inline eingebettet
- Fehlerbehandlung: Ungültige YAML-Dateien → benutzerfreundliche Fehlermeldung, kein Crash
- Kein `eval()`, keine dynamisch generierten Script-Tags (XSS-Schutz)
- Input-Validierung bei Config-Upload (Struktur, Anzahl Fragen, Antwortindex-Range)

## Neues Spiel hinzufügen
Siehe [docs/neues-spiel-erstellen.md](../docs/neues-spiel-erstellen.md)
