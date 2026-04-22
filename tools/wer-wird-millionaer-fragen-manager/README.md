# Fragen-Manager – Wer wird Millionär?

Web-basiertes Tool zum Erstellen und Bearbeiten von Fragendateien für das Spiel [Wer wird Millionär?](../../games/wer-wird-millionaer/).

## Starten

Datei `index.html` im Browser öffnen (Doppelklick genügt).

## Funktionen

- **15 Fragenkarten** (aufklappbar): Jede Karte zeigt eine Vorschau des Fragetexts sowie einen Vollständigkeitsindikator (⬜ = unvollständig, ✅ = vollständig)
- **Feldbeschreibung pro Frage:** Fragetext, vier Antworttexte (A–D), Auswahl der richtigen Antwort
- **Joker-Daten (optional):** Publikumsprozente (A, B, C, D) mit Echtzeit-Summenvalidierung, Telefonjoker-Text, Zusatzjoker-Text
- **Fortschrittsanzeige:** „X / 15 vollständig" wird live aktualisiert
- **YAML laden:** Bestehende Fragendatei per Drag & Drop oder Klick hochladen – alle 15 Karten werden befüllt
- **Validieren:** Prüft Vollständigkeit aller Fragen und Korrektheit der Publikumsprozente; springt zum ersten Fehler
- **Vorschau:** Zeigt die fertige YAML-Struktur im Browser an
- **Exportieren:** Lädt die fertige Datei als `<titel>.yaml` herunter (nur bei bestandener Validierung)

## Workflow

1. Tool öffnen
2. Titel eingeben
3. Alle 15 Fragen ausfüllen (Joker-Daten sind optional)
4. „Exportieren" klicken → YAML-Datei wird heruntergeladen
5. Datei im Spiel hochladen und losspielen

Alternativ: bestehende Config laden, bearbeiten und re-exportieren.

## Hinweise

- Audience-Prozente sollten sich zu 100 addieren (Tool warnt, blockiert aber nicht)
- Das Tool erzeugt **keinen** `game_state`-Abschnitt – der wird ausschließlich vom Spiel selbst beim Speichern hinzugefügt
- Wird eine gespeicherte Spielstanddatei (mit `game_state`-Abschnitt) geladen und re-exportiert, geht der `game_state` verloren – das Tool eignet sich nur zum Bearbeiten von Frageinhalten, nicht von Spielständen
- Das erzeugte YAML ist direkt kompatibel mit dem Spiel und mit der Beispiel-Config [`configs/wer-wird-millionaer/beispiel.yaml`](../../configs/wer-wird-millionaer/beispiel.yaml)
