# ZIP → Gitea Upload

**Live nutzen:** [https://software.obraasch.de/gitea-uploader/index.html](https://software.obraasch.de/gitea-uploader/index.html)

Lädt eine ZIP-Datei direkt aus dem Browser in ein Gitea-Repository hoch -
mit Ordnerstruktur, in einem oder mehreren Commits. Läuft vollständig
client-seitig; es wird ausschließlich mit dem selbst angegebenen
Gitea-Server kommuniziert.

## Nutzung

1. Gitea-Server-URL, Benutzername und Passwort oder Zugangstoken eingeben,
   "Verbinden & Repos laden" klicken.
2. Konto/Organisation wählen, dann bestehendes Repo aus der Liste wählen
   **oder** einen neuen Namen eingeben und "Repo erstellen" klicken.
3. ZIP-Datei auswählen. Danach lässt sich jede enthaltene Datei einzeln abhaken - abgewählte Dateien werden
   beim Hochladen übersprungen (auch dann nicht gelöscht, wenn "Dateien löschen, die nicht mehr in der ZIP
   enthalten sind" aktiv ist).
4. Commit-Nachricht anpassen (optional) und "Jetzt hochladen" klicken.
5. Optional: Unter "Release erstellen" Tag, Titel und Beschreibung eintragen, die gewählte ZIP
   und/oder weitere Dateien als Anhang auswählen und "Release erstellen" klicken. Das geht auch
   unabhängig vom Hochladen, sobald ein Repo gewählt ist.

Vorhandene Dateien mit gleichem Pfad werden aktualisiert statt doppelt
angelegt. Über die Checkbox "Dateien im Repo löschen, die nicht mehr in
der ZIP enthalten sind" kann der Repo-Stand komplett an die ZIP angepasst
werden (mit Bedacht nutzen).

Über das Zahnrad-Symbol oben rechts lassen sich Zugangsdaten im Browser
speichern (nur lokal, nichts wird übertragen) sowie als Datei exportieren
und auf einem anderen Gerät wieder importieren.

## Voraussetzung auf dem Gitea-Server: CORS

Damit der Browser die Gitea-API von einer anderen Domain aus aufrufen darf, muss CORS auf dem Gitea-Server
aktiviert sein. In `app.ini` (bei per Helper-Script installiertem Gitea: `/etc/gitea/app.ini`) folgenden
Abschnitt ergänzen (Position in der Datei ist egal, einfach ans Ende anfügen):

```ini
[cors]
ENABLED = true
ALLOW_DOMAIN = https://software.obraasch.de
ALLOW_CREDENTIALS = true
```

Danach den Gitea-Dienst neu starten (`systemctl restart gitea` bei nativer Installation, sonst der
entsprechende Container-Neustart), damit die Änderung greift.

## Lizenz

MIT, siehe [LICENSE](./LICENSE).
