# Fragen-Manager – Jeopardy!

Web-basiertes Tool zum Erstellen und Bearbeiten von Fragendateien für das Spiel [Jeopardy!](../../games/jeopardy/).

## Starten

Datei `index.html` im Browser öffnen (Doppelklick genügt).

## Funktionen

- **6 Kategorie-Karten** (aufklappbar): Jede Karte zeigt den Kategorienamen als Vorschau sowie einen Vollständigkeitsindikator (⬜ = unvollständig, ✅ = vollständig)
- **Felder pro Kategorie:** Kategoriename, 7 Frage-Antwort-Paare mit Punktwert-Anzeige (100–1.000)
- **Dynamische Kategorien:** Kategorien können hinzugefügt (bis max. 6) oder gelöscht (min. 3 bleiben) werden
- **Reihenfolge ändern:** Kategorien per Drag & Drop umsortieren (Griff-Symbol ⠿ am linken Rand)
- **Fortschrittsanzeige:** „X / 6 Kategorien vollständig" wird live aktualisiert
- **YAML laden:** Bestehende Fragendatei per Drag & Drop oder Klick hochladen – alle Kategorien werden befüllt
- **Validieren:** Prüft Titel, Kategorienanzahl (3–6) und Vollständigkeit aller Fragen und Antworten; springt zum ersten Fehler
- **Vorschau:** Zeigt die fertige YAML-Struktur im Browser an
- **Exportieren:** Lädt die fertige Datei als `<titel>.yaml` herunter (nur bei bestandener Validierung)

## Workflow

1. Tool öffnen
2. Titel eingeben
3. Kategorienamen und alle Fragen/Antworten ausfüllen (überflüssige Kategorien löschen)
4. „Exportieren" klicken → YAML-Datei wird heruntergeladen
5. Datei im Spiel hochladen und losspielen

Alternativ: bestehende Config laden, bearbeiten und re-exportieren.

## Hinweise

- Beim Start werden 6 leere Kategorien angezeigt – nicht benötigte einfach löschen (mindestens 3 müssen bleiben)
- Das Tool erzeugt **keinen** `game_state`-Abschnitt – der wird ausschließlich vom Spiel selbst beim Speichern hinzugefügt
- Wird eine gespeicherte Spielstanddatei (mit `game_state`-Abschnitt) geladen und re-exportiert, geht der `game_state` verloren – das Tool eignet sich nur zum Bearbeiten von Frageinhalten, nicht von Spielständen
- Das erzeugte YAML ist direkt kompatibel mit dem Spiel und mit der Beispiel-Config [`configs/jeopardy/beispiel.yaml`](../../configs/jeopardy/beispiel.yaml)
