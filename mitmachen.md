---
layout: ../layouts/Layout.astro
title: Mitmach-Spass
---
Wer zum Inhalt dieser Seite betragen oder Fehler korrigiert haben möchte hat zwei Möglichkeiten.

Für Langweiler: 
Schreibt mich in den bekannten WhatsApp-Gruppen oder Discord-Servern an.

Für coole Leute: 
Nutzt GitHub. :D
Erstellt euch da einfach einen kostenfreien Account und lernt damit umzugehen.
Mit git bzw. GitHub umgehen zu können, gehört mit zu den Grundfähigkeiten eines jeden Informatikers. Ich empfehle also stark sich damit früher oder später mal auseinanderzusetzen.
Eine gute Anleitung findet ihr z.B. [hier](https://docs.github.com/de/get-started/quickstart/hello-world) oder einfach über eine Google-Suche.

Das Repo auf dem die Dokumente liegen, die den Inhalt dieser Website speisen, findet ihr [hier](https://github.com/KonradMiosga/studynotes).

Wir ihr merge-requests mit euren Änderungen an mich stellen könnt, erklärt euch ChatGPT hier kurz. ;)


1. **Fork des Repositories:**
   - Gehe auf die GitHub-Seite des Repositories, zu dem du einen Beitrag leisten möchtest.
   - Klicke oben rechts auf den "Fork"-Button. Das erstellt eine Kopie des Repositories in deinem eigenen GitHub-Account.

2. **Klonen des Repositories:**
   - Klon die Forked-Version des Repositories auf deinen lokalen Computer. Verwende dazu den Befehl `git clone` in der Git-Bash oder einem anderen Terminal:
     ```
     git clone https://github.com/dein-benutzername/name-des-geforkten-repos.git
     ```

3. **Branch erstellen:**
   - Wechsle in das Verzeichnis des geklonten Repositories:
     ```
     cd name-des-geforkten-repos
     ```
   - Erstelle einen neuen Branch für deine Änderungen:
     ```
     git checkout -b dein-branch-name
     ```

4. **Änderungen durchführen:**
   - Mache die gewünschten Änderungen an deinem Code.

5. **Commit und Push:**
   - Füge die geänderten Dateien zum Staging-Bereich hinzu:
     ```
     git add .
     ```
   - Committe die Änderungen mit einer aussagekräftigen Nachricht:
     ```
     git commit -m "Beschreibung der vorgenommenen Änderungen"
     ```
   - Pushe die Änderungen in deinen Fork auf GitHub:
     ```
     git push origin dein-branch-name
     ```

6. **Erstelle einen Pull Request:**
   - Gehe auf die GitHub-Seite deines geforkten Repositories.
   - Klicke auf den "New pull request"-Button.
   - Wähle den Branch aus, den du gerade erstellt hast, um deine Änderungen zu vergleichen.
   - Überprüfe deine Änderungen und füge eine aussagekräftige Überschrift und Beschreibung für den Pull Request hinzu.
   - Klicke auf "Create pull request" und dann auf "Create pull request" erneut.


***Disclaimer:*** Ich lerne aktuell selbst noch mit git umzugehen, also sollte sich hier durch einen blöden Fehler mal alles in Rauch auflösen, ist das nicht schlimm. Bekommt man alles behoben.