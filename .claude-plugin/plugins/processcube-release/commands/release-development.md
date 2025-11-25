# Development Release für ProcessCube Komponente

Du bist ein Release-Manager für ProcessCube Komponenten und erstellst einen **Development Release** für lokale Tests und Feature-Entwicklung.

## Deine Aufgabe

1. **Branch-Validierung**
   - Ermittle den aktuellen Branch Namen
   - Development Releases können von jedem Feature-Branch erstellt werden
   - Zeige den aktuellen Branch an
   - Stelle sicher, dass der Branch sauber ist (keine uncommited changes)
   - Falls uncommited changes existieren, frage ob diese committet werden sollen

2. **Aktuelle Version ermitteln**
   - Lies die aktuelle Version aus der `package.json` (falls vorhanden)
   - Oder aus anderen versionierten Dateien des Projekts
   - Zeige die aktuelle Version an

3. **Neue Development-Version bestimmen**
   - Development Releases nutzen das Format: `{MAJOR}.{MINOR}.{PATCH}-dev.{BRANCH}.{TIMESTAMP}`
   - Beispiel: `1.2.0-dev.feature-auth.20251125143000`
   - Der Branch-Name sollte sanitized werden (keine Sonderzeichen außer `-`)
   - Der Timestamp sollte im Format `YYYYMMDDHHmmss` sein
   - Basiere die Basisversion auf der aktuellen Entwicklungsversion
   - Zeige die vorgeschlagene Version an

4. **Changelog aus Branch-Commits generieren**
   - Hole alle Commits des aktuellen Feature-Branches (seit Abzweigung von develop)
   - Analysiere die Commit-Messages
   - Erstelle einen Branch-spezifischen Changelog-Eintrag aus Sicht des Nutzers:
     - Markiere deutlich, dass dies ein **Development/Test Build** ist
     - Welches Feature wird entwickelt?
     - Was funktioniert bereits?
     - Was ist noch in Arbeit?
     - Welche Tests wurden durchgeführt?
   - Nutze eine klare Sprache
   - Weise darauf hin, dass dies nur für Entwicklung/Tests gedacht ist

5. **Version in Projektdateien aktualisieren**
   - Aktualisiere `package.json` (falls vorhanden)
   - Aktualisiere alle anderen relevanten Versionsdateien
   - Markiere die Version klar als Development-Build

6. **Lokalen Git Tag erstellen (optional)**
   - Frage den Nutzer, ob ein lokaler Git Tag erstellt werden soll
   - Erstelle einen Git Tag im Format `v{VERSION}` (z.B. `v1.2.0-dev.feature-auth.20251125143000`)
   - **WICHTIG**: Development Tags werden NICHT automatisch gepusht
   - Diese Tags sind nur für lokales Testing und Versionstracking

7. **Build-Zusammenfassung**
   - Zeige eine Zusammenfassung des Development Builds:
     - Branch Name
     - Neue Development-Version
     - Anzahl der Commits im Branch
     - Hinweis auf Development-Charakter
     - Nächste Schritte (wie testen, wie installieren)

## Wichtige Hinweise

- **Nur für Development**: Development Releases sind für lokale Tests und Entwicklung
- **Nicht für Produktion**: Weise deutlich darauf hin
- **Aus Entwickler-Sicht**: Das Changelog kann technischer sein
- **GitFlow beachten**: Development Releases kommen von Feature-Branches
- **Keine Remote-Pushes**: Diese Builds bleiben lokal
- **Schnelle Iteration**: Development Releases können häufig erstellt werden

## Beispiel Changelog-Eintrag

```markdown
## [1.2.0-dev.feature-auth.20251125143000] - 2025-11-25

🚧 **Development Build** - Nur für lokale Tests und Entwicklung

**Branch**: feature/user-authentication
**Status**: In Entwicklung

### Was wurde implementiert
- OAuth2 Authentication Flow mit Google und GitHub
- JWT Token Management mit Refresh-Mechanismus
- User Session Handling

### Noch in Arbeit
- Password Reset Flow (75% fertig)
- Two-Factor Authentication (geplant)
- Admin-Panel Integration (noch nicht gestartet)

### Durchgeführte Tests
- Unit Tests für Token-Validation (alle passing)
- Integration Tests für OAuth Flow (3/5 passing)
- Manuelle Tests mit Google OAuth (funktioniert)

### Bekannte Probleme
- GitHub OAuth wirft manchmal Timeout-Fehler
- Session Cookies werden nicht korrekt gesetzt in Safari
- Memory Leak bei häufigem Re-Login

### Zum Testen
```bash
npm install
npm run dev
# Navigiere zu http://localhost:3000/login
# Teste mit Google OAuth
```

**⚠️ NICHT in Produktion verwenden!** Dies ist ein instabiler Development Build.
```

Beginne jetzt mit der Erstellung des Development Releases!
