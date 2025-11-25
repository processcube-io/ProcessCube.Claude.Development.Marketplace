# ProcessCube Release Manager Plugin

Dieses Plugin unterstützt das Release-Management für ProcessCube Komponenten nach GitFlow und Semantic Versioning Prinzipien.

## Features

- 🎯 **Semantic Versioning**: Automatische Versionsvergabe nach semver
- 📝 **Changelog Generation**: Automatische Changelog-Erstellung aus Commits (aus Nutzersicht)
- 🔄 **GitFlow Support**: Vollständige Unterstützung für GitFlow Workflow
- 🚀 **Drei Release-Typen**: Stable, Insiders und Development Releases

## Verfügbare Commands

### `/release-stable`
Erstellt einen stabilen Release vom `main` Branch.

**Verwendung:**
- Für Production-Releases
- Von `main` Branch
- Vollständiges Semantic Versioning (MAJOR.MINOR.PATCH)
- Erstellt Git Tag und optional Push zum Remote

**Beispiel-Version:** `v1.2.0`

### `/release-insiders`
Erstellt einen Insiders/Preview Release vom `develop` Branch.

**Verwendung:**
- Für Early Access und Testing
- Von `develop` Branch
- Version mit Insiders-Suffix und Timestamp
- Erstellt Git Tag und optional Push zum Remote

**Beispiel-Version:** `v1.2.0-insiders.20251125143000`

### `/release-development`
Erstellt einen Development Release vom aktuellen Feature-Branch.

**Verwendung:**
- Für lokale Tests und Entwicklung
- Von beliebigem Feature-Branch
- Version mit Branch-Name und Timestamp
- Nur lokale Tags, kein automatischer Push

**Beispiel-Version:** `v1.2.0-dev.feature-auth.20251125143000`

## GitFlow Workflow

```
main (stable releases)
  ↑
  └─── develop (insiders releases)
         ↑
         ├─── feature/new-feature (development releases)
         ├─── feature/bug-fix (development releases)
         └─── feature/experiment (development releases)
```

## Semantic Versioning Schema

### Stable Releases
```
MAJOR.MINOR.PATCH
```
- **MAJOR**: Breaking Changes
- **MINOR**: Neue Features (backwards compatible)
- **PATCH**: Bug Fixes

### Insiders Releases
```
MAJOR.MINOR.PATCH-insiders.TIMESTAMP
```
Beispiel: `1.2.0-insiders.20251125143000`

### Development Releases
```
MAJOR.MINOR.PATCH-dev.BRANCH.TIMESTAMP
```
Beispiel: `1.2.0-dev.feature-auth.20251125143000`

## Changelog Format

Alle Changelogs werden aus **Nutzersicht** geschrieben:

- ✅ Klare, verständliche Sprache
- ✅ Was bedeutet die Änderung für den Nutzer?
- ✅ Gruppierung nach Kategorien (Features, Fixes, Breaking Changes)
- ❌ Keine technischen Implementation-Details
- ❌ Keine internen Code-Änderungen

### Beispiel

```markdown
## [1.2.0] - 2025-11-25

### Neue Features
- Prozesse können jetzt exportiert und als Vorlage gespeichert werden
- Dashboard zeigt Echtzeit-Statistiken für alle laufenden Prozesse

### Verbesserungen
- Schnellere Ladezeiten beim Öffnen großer Diagramme
- Bessere Fehlerbehandlung bei Netzwerkproblemen

### Behobene Fehler
- Prozesse werden nun korrekt beendet bei Task-Fehlern
- Layout-Problem auf mobilen Geräten behoben

### Breaking Changes
- API-Methode `startProcess()` benötigt jetzt einen `context` Parameter
```

## Workflow Beispiel

### Stable Release erstellen

1. Wechsle zu `main` Branch
2. Führe `/release-stable` aus
3. Wähle Release-Typ (MAJOR/MINOR/PATCH)
4. Review Changelog
5. Bestätige und pushe zum Remote

### Insiders Release erstellen

1. Wechsle zu `develop` Branch
2. Führe `/release-insiders` aus
3. Review Changelog
4. Bestätige und pushe zum Remote

### Development Build erstellen

1. Auf Feature-Branch arbeiten
2. Führe `/release-development` aus
3. Review Changelog
4. Optional: Lokalen Tag erstellen
5. Teste den Build lokal

## Best Practices

1. **Commits sauber halten**: Nutze aussagekräftige Commit-Messages
2. **Regelmäßige Insiders**: Erstelle regelmäßig Insiders-Releases für Early Feedback
3. **Development nur lokal**: Development Releases niemals pushen
4. **Changelog Review**: Immer das generierte Changelog reviewen und anpassen
5. **Tests vor Release**: Vor Stable Releases alle Tests durchführen

## Technische Details

- **Branch Detection**: Automatische Erkennung des aktuellen Branches
- **Version Parsing**: Unterstützung für package.json und andere Format
- **Git Integration**: Native Git Commands für Tags und Commits
- **Timestamp Format**: YYYYMMDDHHmmss für eindeutige Versionierung

## Anforderungen

- Git installiert und konfiguriert
- Node.js Projekt mit package.json (optional)
- GitFlow Branch-Struktur (main, develop, feature/*)

## Support

Bei Problemen oder Fragen:
- Erstelle ein Issue im ProcessCube Repository
- Kontaktiere das ProcessCube Development Team

---

**Version:** 1.0.0
**Author:** ProcessCube UG
**License:** MIT
