# Regeln für Claude Code in diesem Repo

## Modellwahl: nur so viel Modell wie nötig

Preise (Stand September 2026, Eingabe / Ausgabe je 1 Mio. Token):

| Modell     | Eingabe | Ausgabe | Einsatz                                                        |
|------------|---------|---------|----------------------------------------------------------------|
| Haiku 4.5  | 1 $     | 5 $     | Suchen, Lesen, Fragen zum Code, kleine Textänderungen          |
| Sonnet 5.5 | 2 $     | 10 $    | Normale Änderungen, Bugfixes, Tests, Doku (Standard hier)      |
| Opus 5.5   | 4 $     | 20 $    | Änderungen über mehrere Dateien, schwierige Bugs, Architektur  |
| Fable 5.1  | 10 $    | 50 $    | Nur wenn Opus nachweislich nicht reicht                        |

Standardmodell für dieses Projekt ist Sonnet 5.5 (gesetzt in `.claude/settings.json`).

### Ablauf zu Beginn jeder Aufgabe

1. Aufgabe einstufen: einfach, mittel oder schwer.
2. Passendes Modell nach der Tabelle bestimmen.
3. Läuft die Sitzung auf einem teureren Modell als nötig, das in einem Satz sagen und den
   Wechsel empfehlen (Befehl `/model` oder die Modellauswahl in der App). Claude kann das
   laufende Modell nicht selbst umschalten, der Wechsel liegt beim Nutzer.
4. Läuft die Sitzung auf einem zu schwachen Modell (Haiku bei einer schweren Aufgabe),
   ebenfalls sagen und Sonnet oder Opus empfehlen, statt es mit Haiku zu erzwingen.
5. Unteragenten (Agent-Tool) für Suche, Recherche und Lesen immer mit `model: haiku`
   starten. Nur bei komplexen Teilaufgaben `sonnet`, nie teurer als das Hauptmodell.
6. Keine Modellnamen in Commits, Code, Kommentaren oder PR-Texten.

### Feste Erinnerungszeile

Passt das laufende Modell nicht zur Aufgabe, steht ganz oben in meiner Antwort genau eine Zeile
in diesem Format, mit dem Befehl zum Kopieren:

> Modell-Check: Diese Aufgabe braucht Opus 5.5. Bitte umstellen mit `/model claude-opus-5-5`

Befehle je Modell:

- Haiku 4.5: `/model claude-haiku-4-5`
- Sonnet 5.5: `/model claude-sonnet-5-5`
- Opus 5.5: `/model claude-opus-5-5`
- Fable 5.1: `/model claude-fable-5-1`

Passt das Modell bereits, schweige ich dazu. Die Zeile erscheint höchstens einmal pro Aufgabe.
Nach dem Wechsel gilt sie als erledigt, und ich frage nicht erneut.

### Sparsam arbeiten

- Nur die Dateien und Zeilen lesen, die für die Aufgabe nötig sind.
- Erst besprechen, dann bauen: Vorschlag in wenigen Sätzen, dann auf Freigabe warten.
- Kurze Antworten, keine Wiederholung bekannter Fakten.

## Schreibstil

- Deutsch.
- Keine Gedankenstriche (kein Em-Dash, kein En-Dash). Stattdessen Komma, Doppelpunkt,
  Punkt oder Klammern. Bindestriche in zusammengesetzten Wörtern sind in Ordnung.
