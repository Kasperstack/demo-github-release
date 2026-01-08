# Arbeiten mit dem Setup – Workflow-Anleitung

## Grundprinzip

- Es wird **niemals direkt auf `main` gearbeitet**
- Jede Änderung hat einen eigenen Branch
- Jeder Branch hat klare Semantik
- Commits sind die wichtigste Informationsquelle
- Releases entstehen ausschließlich über Release-Branches

---

## 1. Neue Arbeit beginnen

Ausgangspunkt ist immer der aktuelle `main`-Branch.

Vorgehen:

- `main` aktualisieren
- neuen Arbeitsbranch erstellen

Branch-Namen nach Typ wählen:

- feat/… für neue Features
- fix/… für Bugfixes
- docs/… für Dokumentation
- refactor/… für interne Umbauten

---

## 2. Während der Arbeit committen

- häufig committen
- jeder Commit erfüllt genau einen Zweck
- Commit Messages strikt nach Conventional Commits

Beispielhafte Entwicklung:

- feat(auth): add refresh token validation
- fix(auth): prevent crash on empty token
- docs(auth): document refresh flow

---

## 3. Pull Request in den Release-Branch

Wenn die Arbeit abgeschlossen ist:

- Pull Request vom Arbeitsbranch in den aktuellen Release-Branch erstellen
- PR-Beschreibung wird automatisch aus Commits generiert
- Änderungen werden reviewt
- PR wird gemerged

Der Release-Branch enthält jetzt alle Änderungen für die Version.

---

## 4. Release stabilisieren

Im Release-Branch:

- letzte Fixes vornehmen
- Dokumentation prüfen
- ggf. kleine Anpassungen committen

Nur Bugfixes, keine neuen Features.

---

## 5. Release veröffentlichen

Sobald der Release-Branch fertig ist:

- Pull Request von release/vX.Y.Z nach `main` erstellen
- PR enthält automatisch:

  - vollständige Changelog-Einträge
  - strukturierte Release Notes

- Merge des PRs triggert:

  - Tag-Erstellung (vX.Y.Z)
  - GitHub Release
  - Aktualisierung von CHANGELOG.md

---

## 6. Nach dem Release

- Release-Branch kann gelöscht werden
- `main` enthält immer den letzten stabilen Stand
- neuer Release-Branch für nächste Version wird erstellt

---

## 7. Übersicht – Branch-Typen

| Branch-Typ     | Zweck                          |
| -------------- | ------------------------------ |
| main           | stabiler Produktionsstand      |
| release/vX.Y.Z | Vorbereitung einer Version     |
| feat/\*        | neue Funktionalität            |
| fix/\*         | Bugfix                         |
| docs/\*        | Dokumentation                  |
| refactor/\*    | Code-Verbesserung ohne Feature |
| chore/\*       | Wartung                        |
| test/\*        | Tests                          |

---

## 8. Mentales Modell (wichtig)

- Commits erzählen die Geschichte
- Branches strukturieren die Arbeit
- Releases sind Momentaufnahmen
- Automation verhindert menschliche Fehler
