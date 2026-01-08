# Contributing Guide

Danke, dass du zu diesem Projekt beitragen möchtest.  
Dieses Dokument beschreibt **verbindlich**, wie Branches, Commits, Pull Requests und Releases in diesem Repository funktionieren.

Abweichungen von diesen Regeln werden in Pull Requests nicht akzeptiert.

---

## Grundprinzipien

- Es wird **niemals direkt auf `main` gearbeitet**
- Jede Änderung erfolgt in einem eigenen Branch
- Jeder Commit muss dem **Conventional Commits Standard** folgen
- Releases entstehen ausschließlich über **Release-Branches**
- `CHANGELOG.md` wird **niemals manuell bearbeitet**

---

## Geschützte Branches

### `main`

Der Branch `main` ist geschützt.

Regeln:
- Kein Direkt-Push erlaubt
- Änderungen nur über Pull Requests
- `main` enthält immer den **letzten veröffentlichten Stand**

---

## Branch-Namenskonventionen

### Erlaubte Branch-Typen

Alle Branches müssen einem der folgenden Muster entsprechen:

- feat/kurze-beschreibung  
  Für neue Features

- fix/kurze-beschreibung  
  Für Bugfixes

- docs/kurze-beschreibung  
  Für Dokumentation

- refactor/kurze-beschreibung  
  Für interne Code-Verbesserungen ohne neues Feature

- chore/kurze-beschreibung  
  Für Wartung, Abhängigkeiten, Konfiguration

- test/kurze-beschreibung  
  Für Tests

- ci/kurze-beschreibung  
  Für CI/CD-Änderungen

- release/vMAJOR.MINOR.PATCH  
  Für Release-Vorbereitung

### Regeln für Branch-Namen

- nur Kleinbuchstaben
- Wörter mit Bindestrichen trennen
- keine Sonderzeichen
- maximal 3–5 Wörter

### Beispiele

Gültig:
- feat/user-login
- fix/startup-crash
- docs/api-authentication
- release/v1.2.0

Ungültig:
- feature/login
- Bugfix123
- meinBranch
- release/1.2.0

---

## Commit-Regeln (Pflicht)

Dieses Projekt verwendet **Conventional Commits**.

### Commit-Format

Jeder Commit muss folgendes Format haben:

type(optional-scope): kurze beschreibung

### Erlaubte Types

- feat
- fix
- docs
- refactor
- chore
- test
- ci

### Regeln für Commit Messages

- Beschreibung im Präsens
- keine Großbuchstaben am Anfang
- keine Punkte am Ende
- genau ein Zweck pro Commit

### Beispiele (gültig)

- feat(auth): add password reset endpoint
- fix(auth): validate token expiration
- docs(api): describe authentication flow
- chore(deps): update dependencies

### Beispiele (ungültig)

- added login
- Fix Bug
- FEAT: new stuff
- update

Commits mit ungültigem Format werden **lokal blockiert** und **in Pull Requests abgelehnt**.

---

## Arbeitsablauf (Workflow)

### 1. Neue Arbeit beginnen

- Ausgangspunkt ist immer `main`
- Neuer Branch wird von `main` erstellt
- Branch-Typ entsprechend der Aufgabe wählen

---

### 2. Entwickeln und committen

- kleine, logische Commits
- ein Zweck pro Commit
- Commit Messages strikt nach den Regeln

---

### 3. Pull Request erstellen

Wenn die Arbeit abgeschlossen ist:

- Pull Request vom Arbeitsbranch erstellen
- Ziel-Branch ist immer ein `release/*`-Branch
- PR-Titel kurz und sachlich
- PR-Beschreibung wird automatisch generiert

Nach Review:
- Pull Request mergen
- Arbeitsbranch löschen

---

## Release-Workflow

### Release-Branches

Für jede Version existiert genau ein Release-Branch:

- release/vMAJOR.MINOR.PATCH

Beispiele:
- release/v0.1.0
- release/v1.2.3

Regeln:
- Release-Branches werden aus `main` erstellt
- Sie enthalten ausschließlich Änderungen für diese Version
- Nach dem Release werden sie gelöscht

---

### Release durchführen

1. Pull Request von `release/vX.Y.Z` nach `main` erstellen
2. Pull Request mergen

Nach dem Merge passiert automatisch:
- Version wird bestimmt
- Git-Tag wird erstellt
- CHANGELOG.md wird aktualisiert
- GitHub Release wird veröffentlicht

---

## Changelog

- `CHANGELOG.md` wird automatisch generiert
- niemals manuell bearbeiten
- Änderungen am Changelog erfolgen ausschließlich über Releases

---

## Zusammenfassung (Kurzfassung)

- ❌ niemals auf `main` pushen
- ✅ immer Feature-Branches verwenden
- ✅ immer Conventional Commits schreiben
- ✅ Pull Requests gehen in `release/*`
- ❌ Changelog nicht manuell ändern

---

Bei Fragen oder Unsicherheiten bitte vor dem Commit nachfragen.
