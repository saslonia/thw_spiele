# Neues Spiel erstellen

Anleitung zum Hinzufügen eines weiteren Spiels zum THW-Spiele-Repo.

## Grundstruktur

```
games/<spielname>/
  index.html     # Das vollständige Spiel (alles inline)
  README.md      # Spielanleitung + Config-Format-Dokumentation
configs/<spielname>/
  beispiel.yaml  # Vorlage mit allen Feldern und Kommentaren
tools/<spielname>/
  index.html     # Hilfswerkzeuge (z.B. Fragen-Editor), optional
```

Ersetze `<spielname>` durch einen kurzen, lowercase Namen mit Bindestrichen,  
z.B. `quiz-buzzers` oder `buchstaben-salat`.

## Anforderungen

Jedes Spiel **muss**:

- Eine einzige `index.html`-Datei sein (alles inline: HTML, CSS, JS, Bibliotheken)
- Vollständig offline laufen (keine externen Requests zur Laufzeit)
- Eine Datei-Upload-Möglichkeit für die YAML-Config bieten (Drag & Drop + Klick)
- Spielstand als YAML exportieren und importieren können
- Eine deutschsprachige Benutzeroberfläche haben

Jedes Spiel **sollte**:

- Auf Desktop-Browsern (Chrome, Firefox, Edge) funktionieren
- Auf Tablets nutzbar sein
- Sound per Toggle ein-/ausschaltbar haben (Web Audio API, standardmäßig aus)
- Valide YAML-Fehler mit verständlichen Meldungen abfangen

## Schritt-für-Schritt

### 1. Ordner anlegen

```
games/<spielname>/
configs/<spielname>/
tools/<spielname>/   # optional, für Hilfswerkzeuge
```

### 2. Beispiel-Config erstellen

`configs/<spielname>/beispiel.yaml` mit allen Pflichtfeldern und erklärenden Kommentaren.

### 3. Spiel implementieren (`games/<spielname>/index.html`)

Empfohlene Struktur:

```html
<!DOCTYPE html>
<html lang="de">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Spielname – THW Spiele</title>
  <style>/* CSS inline */</style>
</head>
<body>
  <!-- Screens: Start, Spiel, Ende -->
  <script>
    /* js-yaml 4.1.0 (MIT) – aus games/wer-wird-millionaer/index.html kopieren */
    /* Spiellogik */
  </script>
</body>
</html>
```

Bausteine, die aus `games/wer-wird-millionaer/index.html` übernommen werden können:

- js-yaml Inline-Bibliothek (MIT)
- YAML-Upload (Drag & Drop + Click, FileReader API)
- Spielstand-Export (Blob + URL.createObjectURL)
- Sound-System (Web Audio API + Toggle)
- Fehlerbehandlung beim Config-Laden

### 4. README erstellen

`games/<spielname>/README.md` mit:

- Spielregeln
- Config-Format (alle Felder mit Beispiel und Erklärung)
- Spielstand-Format

### 5. Root-README aktualisieren

Spiel in der Tabelle in `README.md` ergänzen.

## Config-Design-Empfehlungen

- Spielstand-relevante Entscheidungen (z.B. Schwierigkeitsstufe, Variante) gehören in `game_state`, nicht in die Config
- Config enthält nur den Spielinhalt (Fragen, Texte, etc.)
- Alle Felder im game_state optional machen – ein Spiel ohne gespeicherten Stand fängt von vorne an
- YAML-Struktur so einfach wie möglich halten (an Nicht-Techniker denken)
