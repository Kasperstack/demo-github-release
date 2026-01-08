# Contributing Guide

Danke, dass du zu diesem Projekt beitragen möchtest.  
Dieses Dokument beschreibt **verbindlich**, wie Branches, Commits, Pull Requests und Releases in diesem Repository funktionieren.

Abweichungen von diesen Regeln werden in Pull Requests nicht akzeptiert.

---

## Grundprinzipien

- Es wird **niemals direkt auf `main` gearbeitet**
- Es gibt genau zwei Haupt-Branches: `main` (Release) und `dev` (Entwicklung)
- Jede Änderung erfolgt in einem eigenen Branch
- Jeder Commit muss dem **Conventional Commits Standard** folgen
- Releases entstehen ausschließlich durch einen **PR-Merge nach `main`**
- `CHANGELOG.md` wird **niemals manuell bearbeitet**

---

## Haupt-Branches

### `main`

Der Branch `main` ist geschützt.

Regeln:
- Kein Direkt-Push erlaubt
- Änderungen nur über Pull Requests
- `main` enthält immer den **letzten veröffentlichten Stand**
- Ein Merge nach `main` triggert den Release

### `dev`

Der Branch `dev` ist der Integrations-Branch.

Regeln:
- Feature-Branches werden in `dev` gemergt
- `dev` ist **kein** Release-Branch

---

## Branch-Namenskonventionen

### Erlaubte Branch-Typen

- feat/<ticket>-kurzbeschreibung  
  Für neue Features

- fix/<ticket>-kurzbeschreibung  
  Für Bugfixes

- chore/<beschreibung>  
  Für Wartung, Abhängigkeiten, Konfiguration

- docs/<beschreibung>  
  Für Dokumentation

### Regeln für Branch-Namen

- nur Kleinbuchstaben
- Wörter mit Bindestrichen trennen
- keine Sonderzeichen
- `feat/` und `fix/` **müssen** ein Ticket-Präfix enthalten

### Beispiele

Gültig:
- feat/abc-123-login-flow
- fix/bug-456-startup-crash
- docs/api-authentication
- chore/deps-update

Ungültig:
- feature/login
- Bugfix123
- meinBranch
- fix/login

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
- perf
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

- Ausgangspunkt ist immer `dev`
- Neuer Branch wird von `dev` erstellt
- Branch-Typ entsprechend der Aufgabe wählen

### 2. Entwickeln und committen

- kleine, logische Commits
- ein Zweck pro Commit
- Commit Messages strikt nach den Regeln

### 3. Pull Request erstellen

Wenn die Arbeit abgeschlossen ist:

- Pull Request vom Arbeitsbranch nach `dev` erstellen
- PR-Titel kurz und sachlich
- PR-Beschreibung wird automatisch generiert

Nach Review:
- Pull Request mergen
- Arbeitsbranch löschen

### 4. Release

- Pull Request von `dev` nach `main` erstellen
- Nach Merge wird automatisch released (semantic-release)

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
- ✅ Releases entstehen nur über Merge nach `main`
- ❌ Changelog nicht manuell ändern

---

Bei Fragen oder Unsicherheiten bitte vor dem Commit nachfragen.
