# Jeopardy! – THW Spiele

Moderatorgesteuertes Kategorien-Quiz für 2–4 Teams. Teams wählen Kategorien und Punktwerte, der Moderator bewertet die Antworten.

## Schnellstart

1. Datei `index.html` doppelt anklicken
2. YAML-Fragendatei aus dem Ordner `configs/jeopardy/` hochladen
3. Teams einrichten, Spielmodus wählen und losspielen

## Spielmodi

| Modus | Beschreibung |
| ----- | ----------- |
| **Quiz** | Fragetext wird angezeigt – Team nennt die Antwort |
| **Jeopardy** | Antworttext wird angezeigt – Team formuliert die passende Frage |

Der Modus wird **beim Spielstart gewählt**, nicht in der Config festgelegt.

## Teams

- 2–4 Teams, jeweils mit Name (Pflicht) und optionaler Mitgliederliste
- Mitglieder werden durch Komma getrennt eingegeben und auf dem Scoreboard angezeigt
- Das Team, das zuletzt richtig geantwortet hat, wählt die nächste Frage

## Punktwerte und Spielfeld

Das Spielfeld besteht aus **3–6 Kategorien** mit jeweils genau **7 Fragen**. Die Punktwerte sind aufsteigend nach Schwierigkeit:

| Reihe | Punkte |
| ----- | ------ |
| 1 | 100 |
| 2 | 200 |
| 3 | 300 |
| 4 | 400 |
| 5 | 500 |
| 6 | 750 |
| 7 | 1.000 |

## Spielablauf

1. **Feld wählen**: Das aktive Team wählt eine Kategorie und einen Punktwert
2. **Frage anzeigen**: Die Frage (oder im Jeopardy-Modus: die Antwort) erscheint in einem Overlay; ein „Auflösen"-Button zeigt die Lösung
3. **Buzzer**: Team-Buttons erscheinen – ein Team gibt an, geantwortet zu haben
4. **Bewertung**: Der Moderator klickt „✓ Richtig" oder „✗ Falsch"
   - **Richtig**: Das Team erhält die Punkte; alle Teams, die zuvor falsch geantwortet haben, verlieren dieselben Punkte
   - **Falsch**: Das Team verliert die Punkte (vorläufig); ein weiteres Team kann buzzern
5. **Niemand richtig**: Der Moderator kann die Frage mit „Niemand richtig" schließen – es werden keine Punkte vergeben oder abgezogen
6. **Nächste Frage**: Das Feld wird als gespielt markiert; das erfolgreiche Team wählt die nächste Frage

Das Spiel endet, wenn alle Felder gespielt wurden. Die Teams werden nach Punktzahl gerankt.

## Spielstand speichern und fortsetzen

Am Ende des Spiels (oder zu jedem Zeitpunkt über die Speichern-Schaltfläche) kann der Spielstand als YAML-Datei gespeichert werden. Beim nächsten Start diese Datei hochladen – das Spiel setzt an der gespeicherten Stelle fort.

## Sound

Das Spiel enthält Soundeffekte (Web Audio API). Der Sound-Toggle oben rechts (🔊/🔇) schaltet den Ton ein bzw. aus. Standardmäßig ist der Ton ausgeschaltet.

## YAML-Config-Format

```yaml
title: "Spieltitel"
description: "Optionale Beschreibung"  # optional

categories:            # Pflicht: 3 bis 6 Kategorien
  - name: "Geografie"
    questions:         # Pflicht: genau 7 Fragen pro Kategorie, aufsteigend nach Schwierigkeit
      - question: "Welche Stadt ist die Hauptstadt von Deutschland?"
        answer: "Berlin"
      - question: "Welcher Fluss fließt durch Wien?"
        answer: "Die Donau"
      # … insgesamt 7 Fragen

  - name: "Geschichte"
    questions:
      # … 7 Fragen

# Spielstand (wird beim Speichern automatisch hinzugefügt)
game_state:                          # optional
  teams:
    - name: "Team A"
      members: ["Alice", "Bob"]
      score: 500
    - name: "Team B"
      members: []
      score: -200
  mode: "quiz"                       # "quiz" oder "jeopardy"
  active_team: 0                     # Index des wählenden Teams (0-basiert)
  revealed: [[0, 1], [1, 2]]         # bereits gespielte Felder als [Kategorie-Index, Frage-Index]
  status: "playing"                  # "playing" oder "finished"
```

### Feldbeschreibung

| Feld | Typ | Pflicht | Beschreibung |
| ---- | --- | ------- | ------------ |
| `title` | String | ja | Spieltitel (wird auf dem Startbildschirm angezeigt) |
| `description` | String | nein | Kurzbeschreibung |
| `categories` | Liste | ja | 3–6 Kategorien |
| `categories[].name` | String | ja | Kategoriename (Spaltenüberschrift im Board) |
| `categories[].questions` | Liste[7] | ja | Genau 7 Fragen pro Kategorie |
| `categories[].questions[].question` | String | ja | Fragetext (Quiz: angezeigt; Jeopardy: Lösung) |
| `categories[].questions[].answer` | String | ja | Antworttext (Quiz: Lösung; Jeopardy: angezeigt) |
| `game_state.teams` | Liste | nein | Teamdaten inkl. Name, Mitglieder und Punktstand |
| `game_state.mode` | String | nein | `"quiz"` oder `"jeopardy"` |
| `game_state.active_team` | Integer | nein | Index des aktuell wählenden Teams (0-basiert) |
| `game_state.revealed` | Liste | nein | Bereits gespielte Felder als `[Kategorie-Index, Frage-Index]`-Paare |
| `game_state.status` | String | nein | `"playing"` oder `"finished"` |

### Hinweise zur Fragendatei

- Die Reihenfolge der Fragen entspricht der Schwierigkeit: Frage 1 (100 Punkte) bis Frage 7 (1.000 Punkte).
- Im **Quiz-Modus** wird `question` angezeigt; `answer` ist die Lösung.
- Im **Jeopardy-Modus** wird `answer` angezeigt; `question` ist die Lösung.
- Beide Felder sind in beiden Modi vorhanden – der Modus bestimmt nur, was zuerst sichtbar ist.

## Fertige Konfigurationen

| Datei | Inhalt |
|-------|--------|
| [../../configs/jeopardy/thw-grundwissen.yaml](../../configs/jeopardy/thw-grundwissen.yaml) | Fragen rund um das THW |
| [../../configs/jeopardy/beispiel.yaml](../../configs/jeopardy/beispiel.yaml) | Allgemeinwissen-Vorlage |

## Fragen-Manager

Der [Fragen-Manager](../../tools/jeopardy-fragen-manager/) ist ein web-basiertes Tool zum komfortablen Erstellen und Bearbeiten von Fragendateien – mit Live-Validierung, Drag &amp; Drop-Sortierung, YAML-Vorschau und direktem Export. Datei `tools/jeopardy-fragen-manager/index.html` einfach im Browser öffnen.
