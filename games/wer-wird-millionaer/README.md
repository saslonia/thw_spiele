# Wer wird Millionär? – THW Spiele

Das klassische Quizspiel für THW-Veranstaltungen. 15 Fragen, 4 Joker, eine Million Euro.

## Schnellstart

1. Datei `index.html` doppelt anklicken
2. YAML-Fragendatei aus dem Ordner `configs/wer-wird-millionaer/` hochladen
3. Spielvariante wählen und losspielen

## Spielvarianten

| Variante | Joker | Sicherheitsstufen |
|----------|-------|-------------------|
| **Klassisch** | 50:50 · Publikum · Telefon | 1.000 € und 16.000 € |
| **Risiko** | 50:50 · Publikum · Telefon · **Zusatz** | nur 1.000 € |

Die Variante wird **beim Spielstart gewählt**, nicht in der Config festgelegt.

## Joker

| Joker | Beschreibung |
|-------|-------------|
| **50:50** | Zwei falsche Antworten werden ausgeblendet |
| **👥 Publikum** | Balkendiagramm mit Prozentverteilung aus der Config (oder simuliert) |
| **📞 Telefon** | Hinweistext aus der Config wird in einer Sprachblase angezeigt |
| **🙋 Zusatz** | Zuschauermeinung aus der Config *(nur Risiko-Variante)* |

Jeder Joker kann einmal pro Spiel verwendet werden. Mehrere Joker auf dieselbe Frage sind erlaubt.

## Gewinnstufen

| Frage | Betrag | Sicherheitsstufe |
|-------|--------|-----------------|
| 1 | 100 € | |
| 2 | 200 € | |
| 3 | 300 € | |
| 4 | 500 € | |
| **5** | **1.000 €** | **★ immer** |
| 6 | 2.000 € | |
| 7 | 4.000 € | |
| 8 | 8.000 € | |
| **9** | **16.000 €** | **★ nur Klassisch** |
| 10 | 32.000 € | |
| 11 | 64.000 € | |
| 12 | 125.000 € | |
| 13 | 250.000 € | |
| 14 | 500.000 € | |
| **15** | **1.000.000 €** | |

## Spielstand speichern und fortsetzen

Am Ende des Spiels (oder beim Aufhören) kann der Spielstand als YAML-Datei gespeichert werden. Beim nächsten Start diese Datei hochladen – das Spiel setzt an der gespeicherten Stelle fort.

## YAML-Config-Format

```yaml
title: "Spieltitel"
description: "Optionale Beschreibung"  # optional

questions:            # Pflicht: genau 15 Fragen, aufsteigend nach Schwierigkeit
  - question: "Welche Farbe hat der Himmel?"
    answers:
      - "Grün"    # A
      - "Gelb"    # B
      - "Blau"    # C
      - "Rot"     # D
    correct: 2    # Index der richtigen Antwort: 0=A, 1=B, 2=C, 3=D

    jokers:                          # optional – ohne Angabe werden Zufallswerte verwendet
      audience: [5, 8, 82, 5]        # Publikums-% für A, B, C, D (sollte 100 ergeben)
      phone: "Das ist blau, ganz sicher!"
      additional: "Blau – Antwort C!"

# Spielstand (wird beim Speichern automatisch hinzugefügt)
game_state:                        # optional
  current_question: 7              # nächste zu beantwortende Frage, 0-basiert (0–14)
  variant: "risk"                  # "risk" oder "classic"
  jokers_used:                     # Liste bereits verbrauchter Joker
    - "fifty_fifty"
    - "audience"
```

### Feldbeschreibung

| Feld | Typ | Pflicht | Beschreibung |
|------|-----|---------|-------------|
| `title` | String | ja | Spieltitel (wird auf dem Startbildschirm angezeigt) |
| `description` | String | nein | Kurzbeschreibung |
| `questions` | Liste | ja | Genau 15 Fragen |
| `questions[].question` | String | ja | Fragetext |
| `questions[].answers` | Liste[4] | ja | Genau 4 Antworttexte (A, B, C, D) |
| `questions[].correct` | Integer | ja | Index der richtigen Antwort: 0=A, 1=B, 2=C, 3=D |
| `questions[].jokers.audience` | Liste[4] | nein | Publikums-% für A, B, C, D |
| `questions[].jokers.phone` | String | nein | Text für den Telefonjoker |
| `questions[].jokers.additional` | String | nein | Text für den Zusatzjoker |
| `game_state.current_question` | Integer | nein | Nächste Frage (0-basiert) |
| `game_state.variant` | String | nein | `"risk"` oder `"classic"` |
| `game_state.jokers_used` | Liste | nein | Schlüssel verbrauchter Joker |

### Joker-Schlüssel für `jokers_used`
- `"fifty_fifty"` – 50:50-Joker
- `"audience"` – Publikumsjoker
- `"phone"` – Telefonjoker
- `"additional"` – Zusatzjoker

## Fertige Konfigurationen

| Datei | Inhalt |
|-------|--------|
| [../../configs/wer-wird-millionaer/thw-grundwissen.yaml](../../configs/wer-wird-millionaer/thw-grundwissen.yaml) | 15 Fragen rund um das THW |
| [../../configs/wer-wird-millionaer/beispiel.yaml](../../configs/wer-wird-millionaer/beispiel.yaml) | Allgemeinwissen-Vorlage |
