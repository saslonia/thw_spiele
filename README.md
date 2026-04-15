# THW Spiele

Sammlung von Browser-Spielen für THW-Veranstaltungen. Jedes Spiel läuft vollständig lokal – kein Internet, kein Server nötig.

## Verfügbare Spiele

| Spiel | Beschreibung |
|-------|-------------|
| [Wer wird Millionär?](games/wer-wird-millionaer/) | Das klassische Ratequiz mit 15 Fragen und Jokern |

## Schnellstart

1. **Repository herunterladen:** Oben auf dieser Seite → grüner Button „Code" → „Download ZIP" → entpacken
2. **Spiel starten:** Ins Spielverzeichnis wechseln (z.B. `games/wer-wird-millionaer/`) und `index.html` doppelt anklicken
3. **Fragendatei laden:** Eine YAML-Datei aus dem Ordner `configs/` auswählen (Drag & Drop oder Klick)
4. **Spielvariante wählen** und losspielen!

> **Hinweis:** Falls der Browser eine Sicherheitswarnung zeigt, einmalig über *Rechtsklick → Öffnen mit → Browser* starten.

## Vorgefertigte Fragendateien

| Datei | Inhalt |
|-------|--------|
| [configs/wer-wird-millionaer/thw-grundwissen.yaml](configs/wer-wird-millionaer/thw-grundwissen.yaml) | 15 Fragen rund um das THW |
| [configs/wer-wird-millionaer/beispiel.yaml](configs/wer-wird-millionaer/beispiel.yaml) | Allgemeinwissen-Vorlage |

## Eigene Fragen erstellen

1. Eine Datei aus `configs/wer-wird-millionaer/` kopieren und umbenennen
2. Fragen anpassen (genau 15 Fragen, aufsteigend nach Schwierigkeit)
3. Im Spiel hochladen – fertig!

Alle Details zum YAML-Format: [games/wer-wird-millionaer/README.md](games/wer-wird-millionaer/README.md)

## Für Entwickler & Contributors

→ [CONTRIBUTING.md](CONTRIBUTING.md)  
→ [docs/neues-spiel-erstellen.md](docs/neues-spiel-erstellen.md)
