# FamilienHub

Mobile-first Familienorganizer als PWA mit Firebase Authentication und Realtime Database.

## Dateien
- `index.html` – App
- `manifest.webmanifest` – PWA-Metadaten
- `sw.js` – Service Worker / App-Shell-Cache
- `logo.svg` und `icons/` – Logo und App-Icons
- `firebase-database-rules.json` – derzeit verwendete Datenbankregeln (vor Veröffentlichung prüfen!)

## GitHub Pages
1. Neues GitHub-Repository erstellen.
2. Alle Dateien und den Ordner `icons/` unverändert hochladen.
3. In **Settings → Pages** als Quelle den Branch `main` und Ordner `/ (root)` auswählen.
4. Die veröffentlichte HTTPS-Adresse öffnen.
5. Firebase Console → Authentication → Authorized domains: die GitHub-Pages-Domain ergänzen, falls sie noch fehlt.
6. Auf Android in Chrome über das Menü **App installieren** bzw. **Zum Startbildschirm hinzufügen** auswählen.

## Lokal testen
Nicht per `file://` öffnen. Im Projektordner einen lokalen Webserver starten, z. B.:
`python -m http.server 8000`
Dann `http://localhost:8000` öffnen.

## Firebase-Hinweis – vor echter Nutzung wichtig
Die App enthält Firebase-Konfigurationsdaten. Das ist bei Firebase-Web-Apps normal; der Schutz muss über Authentication und Datenbankregeln erfolgen.
Die bisherige Regeldatei erlaubt jedem angemeldeten Firebase-Konto Zugriff auf `families/main`. Das ist **keine sichere Familienfreigabe**. Vor einer echten Veröffentlichung muss eine Mitglieder-Allowlist bzw. eine Prüfung der Familienmitgliedschaft in den Realtime-Database-Regeln umgesetzt werden. Außerdem muss die Anmeldung auf die tatsächlich vorgesehenen Konten beschränkt werden.
Der Service Worker speichert nur die App-Oberfläche. Firebase-Daten werden weiterhin online geladen und synchronisiert; vollständiger Offline-Datenbetrieb ist nicht implementiert.
