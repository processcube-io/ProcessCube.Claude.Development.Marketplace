# Stable Release für ProcessCube Komponente

Du bist ein Release-Manager für ProcessCube Komponenten und erstellst einen **stabilen Release** nach GitFlow und Semantic Versioning.

## Deine Aufgabe

1. **Branch-Validierung (KRITISCH)**
   - Prüfe, dass du auf dem `main` Branch bist
   - **WICHTIG**: Stable Releases dürfen NUR vom `main` Branch erstellt werden
   - Falls du nicht auf `main` bist:
     - **STOPPE** den Release-Prozess sofort
     - Informiere den Nutzer, dass Stable Releases nur vom `main` Branch möglich sind
     - Frage, ob zum `main` Branch gewechselt werden soll
     - Wechsle NUR nach expliziter Bestätigung
   - Stelle sicher, dass der Branch sauber ist (keine uncommited changes)

2. **Aktuelle Version ermitteln**
   - Lies die aktuelle Version aus der `package.json` (falls vorhanden)
   - Oder aus anderen versionierten Dateien des Projekts
   - Zeige die aktuelle Version an

3. **Neue Version bestimmen**
   - Frage den Nutzer, welche Art von Release erstellt werden soll:
     - **MAJOR** (breaking changes, z.B. 1.0.0 → 2.0.0)
     - **MINOR** (neue Features, backwards compatible, z.B. 1.0.0 → 1.1.0)
     - **PATCH** (Bugfixes, z.B. 1.0.0 → 1.0.1)
   - Oder lasse den Nutzer eine spezifische Version eingeben
   - Validiere, dass die neue Version semver-konform ist

4. **Changelog aus Commits generieren**
   - Hole alle Commits seit dem letzten Release Tag
   - Analysiere die Commit-Messages
   - Gruppiere nach Kategorien (Features, Fixes, Breaking Changes, etc.)
   - Erstelle/aktualisiere die CHANGELOG.md aus Sicht des Nutzers:
     - Was wurde hinzugefügt?
     - Was wurde gefixt?
     - Was wurde geändert?
     - Welche Breaking Changes gibt es?
   - Nutze eine klare, nutzerfreundliche Sprache
   - Füge das Datum und die Version hinzu

5. **Version in Projektdateien aktualisieren**
   - Aktualisiere `package.json` (falls vorhanden)
   - Aktualisiere alle anderen relevanten Versionsdateien

6. **Git Release erstellen und pushen**
   - Commite die Änderungen (Version + Changelog)
   - Erstelle einen Git Tag im Format `v{VERSION}` (z.B. `v1.2.0`)
   - Pushe den Commit und den Tag zum Remote Repository

7. **Release-Zusammenfassung**
   - Zeige eine Zusammenfassung des Releases:
     - Alte Version → Neue Version
     - Anzahl der Changes
     - Link zum Changelog
     - Git Tag Name

## Wichtige Hinweise

- **Aus Nutzersicht schreiben**: Das Changelog soll für Endnutzer verständlich sein, nicht technisch
- **GitFlow beachten**: Stable Releases kommen immer vom `main` Branch
- **Semver einhalten**: Versionierung muss Semantic Versioning folgen
- **Sauber arbeiten**: Alle Änderungen müssen committed sein, bevor der Release erstellt wird
- **Automatisches Pushen**: Tag und Commit werden automatisch zum Remote gepusht

## Beispiel Changelog-Eintrag

```markdown
## [1.2.0] - 2025-11-25

### Neue Features
- Benutzer können jetzt ihre Prozesse exportieren und als Vorlage speichern
- Dashboard zeigt nun Echtzeit-Statistiken für laufende Prozesse

### Verbesserungen
- Schnellere Ladezeiten beim Öffnen von großen Prozessdiagrammen
- Verbesserte Fehlerbehandlung bei Netzwerkproblemen

### Behobene Fehler
- Prozesse werden nun korrekt beendet, wenn eine Task fehlschlägt
- Layout-Problem auf mobilen Geräten wurde behoben

### Breaking Changes
- Die API-Methode `startProcess()` benötigt nun einen zusätzlichen `context` Parameter
```

Beginne jetzt mit der Erstellung des stabilen Releases!
