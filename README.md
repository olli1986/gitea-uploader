# ZIP → Gitea Upload

Lädt eine ZIP-Datei direkt aus dem Browser in ein Gitea-Repository hoch -
mit Ordnerstruktur, in einem oder mehreren Commits. Läuft vollständig
client-seitig; es wird ausschließlich mit dem selbst angegebenen
Gitea-Server kommuniziert.

## Nutzung

1. Gitea-Server-URL, Benutzername und Passwort oder Zugangstoken eingeben,
   "Verbinden & Repos laden" klicken.
2. Bestehendes Repo aus der Liste wählen **oder** einen neuen Namen
   eingeben und "Repo erstellen" klicken.
3. ZIP-Datei auswählen.
4. Commit-Nachricht anpassen (optional) und "Jetzt hochladen" klicken.

Vorhandene Dateien mit gleichem Pfad werden aktualisiert statt doppelt
angelegt. Über die Checkbox "Dateien im Repo löschen, die nicht mehr in
der ZIP enthalten sind" kann der Repo-Stand komplett an die ZIP angepasst
werden (mit Bedacht nutzen).

## Voraussetzung auf dem Gitea-Server

Damit der Browser die Gitea-API von einer anderen Domain aus aufrufen
darf, muss CORS für diese Domain aktiviert sein (Abschnitt `[cors]` in
`app.ini`).

## Lizenz

MIT, siehe [LICENSE](./LICENSE).
