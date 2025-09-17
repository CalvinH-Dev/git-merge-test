# Git Merge Conflict Test Project

Ein einfaches HTML/CSS Projekt zum Testen von Git Merge Konflikten und Git Best Practices.

## Aufgabe

1. **Teste die HTML-Seite**: Öffne `index.html` im Browser
2. **Setze `resources/test.txt` auf ignore**: Verwende `.gitignore`
3. **Teste Git Merge Konflikte** mit verschiedenen Branches
4. **Lerne lokale Git Updates rückgängig zu machen**

## Schnellstart

```bash
# Projekt klonen und öffnen
git clone <repository-url>
cd git-merge-test

# HTML-Seite im Browser öffnen
open index.html  # macOS
start index.html # Windows
```

## Projektstruktur

```
git-merge-test/
├── index.html          # Hauptseite mit Git Commands
├── style.css           # Moderne CSS Styles
├── README.md           # Diese Datei
├── .gitignore          # Git ignore Regeln
└── resources/
    ├── README.md       # Aufgaben Beschreibung
    └── test.txt        # Test-Datei (soll ignoriert werden)
```

## Git Commands - Schritt für Schritt

### Grundlegende Commands (in der richtigen Reihenfolge):

1. **Status prüfen**
   ```bash
   git status
   ```

2. **Änderungen hinzufügen**
   ```bash
   git add .                    # Alle Dateien
   git add dateiname.txt        # Einzelne Datei
   ```

3. **Commit erstellen**
   ```bash
   git commit -m "Beschreibung der Änderungen"
   ```

4. **Branch erstellen und wechseln**
   ```bash
   git branch feature-branch    # Neuen Branch erstellen
   git checkout feature-branch  # Zu Branch wechseln
   # oder kombiniert:
   git checkout -b feature-branch
   ```

5. **Änderungen pushen**
   ```bash
   git push origin branch-name
   ```

## Merge Konflikte erstellen und lösen

### Konflikte absichtlich erstellen:

1. **Erstelle zwei Branches mit unterschiedlichen Änderungen an derselben Datei**
   ```bash
   # Main Branch - ändere Zeile 12 in index.html
   git checkout main
   git add index.html
   git commit -m "Änderung in main branch"

   # Feature Branch - ändere dieselbe Zeile 12 anders
   git checkout -b feature-conflict
   # Ändere dieselbe Zeile unterschiedlich
   git add index.html
   git commit -m "Andere Änderung in feature branch"
   ```

2. **Merge versuchen (wird Konflikt erzeugen)**
   ```bash
   git checkout main
   git merge feature-conflict
   # CONFLICT!
   ```

### Konflikte lösen:

1. **Konfliktreiche Dateien anzeigen**
   ```bash
   git status
   ```

2. **Datei öffnen und Konflikte manuell lösen**
   - Suche nach `<<<<<<<`, `=======`, `>>>>>>>`
   - Entscheide welche Änderungen behalten werden sollen
   - Entferne die Konflikt-Marker

3. **Lösung bestätigen**
   ```bash
   git add dateiname
   git commit  # Automatische Merge-Commit Message
   ```

## Lokale Git Updates rückgängig machen

### Uncommitted Änderungen rückgängig machen:

```bash
# Einzelne Datei zurücksetzen
git checkout -- dateiname.txt

# Alle Änderungen zurücksetzen
git reset --hard HEAD

# Staging rückgängig machen
git reset HEAD dateiname.txt
```

### Commits rückgängig machen:

```bash
# Letzten Commit rückgängig (behält Änderungen)
git reset --soft HEAD~1

# Letzten Commit komplett entfernen
git reset --hard HEAD~1

# Mehrere Commits rückgängig
git reset --hard HEAD~3  # Letzten 3 Commits
```

### Specific Commit rückgängig machen:

```bash
# Commit ID finden
git log --oneline

# Commit rückgängig machen (erstellt neuen Commit)
git revert <commit-hash>
```

## .gitignore Setup

Erstelle eine `.gitignore` Datei mit folgendem Inhalt:

```gitignore
# Test-Dateien ignorieren
resources/test.txt

# System-Dateien
.DS_Store
Thumbs.db

# Editor-Dateien
.vscode/
.idea/

# Temporäre Dateien
*.tmp
*.log
```

## Praktische Übungen

1. **Button-Test**: Klicke den Button auf der HTML-Seite
2. **Style-Änderung**: Ändere die Button-Farbe in `style.css`
3. **Konflikt-Test**: Erstelle einen Merge-Konflikt
4. **Reset-Test**: Mache Änderungen rückgängig
5. **Ignore-Test**: Prüfe ob `resources/test.txt` ignoriert wird

## Troubleshooting

**Problem**: Merge-Konflikt zu komplex
**Lösung**: `git merge --abort` um Merge abzubrechen

**Problem**: Versehentlich wichtigen Commit gelöscht
**Lösung**: `git reflog` um Commit zu finden und wiederherzustellen

**Problem**: Push wird abgelehnt
**Lösung**: Erst `git pull` dann `git push`

## Best Practices

- Kleine, häufige Commits
- Aussagekräftige Commit-Messages
- Vor Merge immer `git status` prüfen
- Regelmäßig `git pull` für Updates
- Nie direkt auf main branch arbeiten
- Nie Commits mit sensiblen Daten