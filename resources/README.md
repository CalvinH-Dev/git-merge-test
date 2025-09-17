# Resources Folder

## Aufgabe

**Hauptziel**: Lerne wie man Dateien in Git ignoriert!

### Was zu tun ist:

1. **Schaue dir die Datei `test.txt` an**
   - Diese Datei enthält Test-Daten
   - Sie soll NICHT in Git getrackt werden

2. **Erstelle eine `.gitignore` Datei**
   - Im Hauptverzeichnis des Projekts
   - Füge die Zeile `resources/test.txt` hinzu

3. **Teste die .gitignore**
   ```bash
   # Prüfe ob die Datei ignoriert wird
   git status

   # Die test.txt sollte NICHT in der Liste stehen
   ```

4. **Ändere die test.txt Datei**
   - Füge eigenen Text hinzu
   - Führe wieder `git status` aus
   - Die Änderungen sollten ignoriert werden

## Lernziele

- Verstehen wie `.gitignore` funktioniert
- Lernen welche Dateien man typischerweise ignoriert
- Praktische Anwendung von Git ignore patterns

## Erfolgskriterium

Wenn `git status` die `test.txt` Datei nicht mehr anzeigt, hast du es richtig gemacht!