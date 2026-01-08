# Projekt einrichten – Setup-Anleitung

## Ziel des Setups

Ziel dieses Setups ist es, ein GitHub-Repository so einzurichten, dass:

- der `main`-Branch stabil und geschützt ist
- Releases reproduzierbar und versioniert sind
- Changelogs und Release Notes automatisch entstehen
- Entwickler\*innen sich nur auf saubere Commits konzentrieren müssen
- alle Änderungen über Pull Requests laufen

---

## 1. Repository in der GitHub-Organisation anlegen

- Neues Repository in der Organisation erstellen
- Repository sichtbar für alle Beteiligten machen
- Initial **README.md** hinzufügen
- Standard-Branch auf `main` setzen

---

## 2. Branch Protection für `main` konfigurieren

In den Repository Settings unter „Branches“:

- Branch Protection Rule für `main` anlegen
- „Require a pull request before merging“ aktivieren
- „Require status checks to pass before merging“ aktivieren
- Optional: „Require linear history“
- Direktes Pushen auf `main` deaktivieren

Ziel: **Kein Commit darf direkt auf `main` landen**

---

## 3. Release-Branch-Konzept festlegen

Es wird ein **Release-Branch pro Version** verwendet.

Namensschema:

- release/vMAJOR.MINOR.PATCH
- Beispiele:

  - release/v0.1.0
  - release/v1.2.3

Release-Branches:

- werden aus `main` erstellt
- sammeln alle Änderungen für genau eine Version
- werden nach Fertigstellung zurück nach `main` gemerged

---

## 4. Branch-Namenskonvention definieren

Kurzlebige Arbeitsbranches verwenden folgendes Schema:

- feat/kurze-beschreibung
- fix/kurze-beschreibung
- docs/kurze-beschreibung
- refactor/kurze-beschreibung
- chore/kurze-beschreibung
- test/kurze-beschreibung

Beispiele:

- feat/user-login
- fix/nullpointer-on-startup
- docs/api-overview

Diese Branches werden **niemals direkt nach `main`** gemerged.

---

## 5. Conventional Commits als Standard festlegen

Alle Commits müssen dem **Conventional Commits Standard** folgen.

Grundformat:

- type(optional-scope): kurze beschreibung

Erlaubte Typen:

- feat
- fix
- docs
- refactor
- chore
- test
- ci

Regeln:

- Präsens verwenden
- keine Großbuchstaben am Anfang
- Beschreibung maximal ein Satz

Ziel: Commits sind maschinenlesbar und verständlich.

---

## 6. Commit-Regeln im Projekt durchsetzen

Im Projekt wird Commit-Linting eingerichtet, um fehlerhafte Commit Messages zu verhindern.

Dazu:

- Commitlint konfigurieren
- Husky oder vergleichbare Git Hooks aktivieren
- Commits ohne korrektes Format blockieren

Ergebnis: **Kein schlechter Commit verlässt das lokale System**

---

## 7. Automatisierung für Changelog & Releases einrichten

Folgende Automatisierung wird eingerichtet:

- automatische Ermittlung der nächsten Version anhand der Commits
- automatische Generierung von CHANGELOG.md
- automatische Erstellung von GitHub Releases
- automatische Tags (z. B. v1.2.0)

Das Changelog wird **niemals manuell** bearbeitet.

---

## 8. GitHub Actions aktivieren

Im Repository werden GitHub Actions eingerichtet für:

- Validierung der Commit Messages in Pull Requests
- automatische Generierung von PR-Zusammenfassungen
- Release-Erstellung beim Merge eines Release-Branches nach `main`

Ziel: **PRs und Releases dokumentieren sich selbst**

---

## 9. Repository-Dokumentation ergänzen

Folgende Dateien werden empfohlen:

- README.md
  Kurze Projektbeschreibung und Link zum Workflow
- CONTRIBUTING.md
  Commit-Regeln, Branch-Namen, Release-Ablauf
- CHANGELOG.md
  Wird automatisch gepflegt

---

## 10. Initialen Release-Branch erstellen

Zum Abschluss:

- Release-Branch `release/v0.1.0` aus `main` erstellen
- erste leere Version vorbereiten
- Projekt ist jetzt releasefähig
