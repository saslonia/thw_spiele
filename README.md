# THW Spiele

Sammlung von Browser-Spielen für THW-Veranstaltungen. Jedes Spiel läuft vollständig lokal – kein Internet, kein Server nötig.

## Verfügbare Spiele

| Spiel | Beschreibung |
|-------|-------------|
| [Wer wird Millionär?](games/wer-wird-millionaer/) | Das klassische Ratequiz mit 15 Fragen und Jokern |
| [Jeopardy!](games/jeopardy/) | Kategorien-Wissensquiz für 2–4 Teams mit Punkteanimationen |

## Schnellstart

1. **Repository herunterladen:** Oben auf dieser Seite → grüner Button „Code" → „Download ZIP" → entpacken
2. **Spiel starten:** Ins Spielverzeichnis wechseln (z.B. `games/wer-wird-millionaer/`) und `index.html` doppelt anklicken
3. **Fragendatei laden:** Eine YAML-Datei aus dem Ordner `configs/` auswählen (Drag & Drop oder Klick)
4. **Spielvariante wählen** und losspielen!

> **Hinweis:** Falls der Browser eine Sicherheitswarnung zeigt, einmalig über *Rechtsklick → Öffnen mit → Browser* starten.

## Vorgefertigte Fragendateien

| Datei | Inhalt |
|-------|--------|
| [configs/wer-wird-millionaer/thw-grundwissen.yaml](configs/wer-wird-millionaer/thw-grundwissen.yaml) | 15 Fragen rund um das THW (Wer wird Millionär?) |
| [configs/wer-wird-millionaer/beispiel.yaml](configs/wer-wird-millionaer/beispiel.yaml) | Allgemeinwissen-Vorlage (Wer wird Millionär?) |
| [configs/jeopardy/thw-grundwissen.yaml](configs/jeopardy/thw-grundwissen.yaml) | 5 Kategorien THW-Wissen für Jeopardy (35 Fragen) |
| [configs/jeopardy/beispiel.yaml](configs/jeopardy/beispiel.yaml) | Allgemeinwissen-Vorlage für Jeopardy |

## Eigene Fragen erstellen

1. Eine Datei aus `configs/wer-wird-millionaer/` kopieren und umbenennen
2. Fragen anpassen (genau 15 Fragen, aufsteigend nach Schwierigkeit)
3. Im Spiel hochladen – fertig!

Alle Details zum YAML-Format: [games/wer-wird-millionaer/README.md](games/wer-wird-millionaer/README.md)

> **Tipp:** Unter den [Tools](tools/) verbergen sich Fragen-Manager mit einer komfortablen Web-Oberfläche zum Erstellen und Bearbeiten von Fragendateien – mit Live-Validierung und direktem YAML-Export.

## Tools

| Tool | Beschreibung |
|------|--------------|
| [Fragen-Manager (Wer wird Millionär?)](tools/wer-wird-millionaer-fragen-manager/) | Web-Interface zum Erstellen und Bearbeiten von Fragendateien |
| [Fragen-Manager (Jeopardy!)](tools/jeopardy-fragen-manager/) | Web-Interface zum Erstellen und Bearbeiten von Jeopardy-Kategorien |

## Für Entwickler & Contributors

→ [CONTRIBUTING.md](CONTRIBUTING.md)  
→ [docs/neues-spiel-erstellen.md](docs/neues-spiel-erstellen.md)
