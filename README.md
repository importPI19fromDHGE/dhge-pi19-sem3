# DHGE - Praktische Informatik - Matrikel 19 - Semester 3

Dieses Repository ist ein Projekt von Studierenden des Studiengangs "Praktische Informatik" der Dualen Hochschule Gera-Eisenach. Hier werden alle Mitschriften der einzelnen Modulen gesammelt. Die Skripte liegen im `markdown`-Format vor. Zur besseren Handhabung (und weil Github nur begrenzte `markdown`-Features bereitstellt) werden diese zusätzlich automatisch in [PDFs](https://github.com/importPI19fromDHGE/dhge-pi19-sem3/releases) umgewandelt und zur Verfügung gestellt.

## Contributing andere Jahrgänge

Studierende anderer Jahrgänge sind dazu eingeladen, dieses Projekt als Grundlage für ihr eigenes, matrikelspezifsiches Repository zu nutzen.
Du kannst folgendermaßen vorgehen:

- Lerne in jedem Fall Git und Github kennen, frage deine Kommilitonen, frage das [Internet](https://rogerdudler.github.io/git-guide/index.de.html), frage uns diesbezüglich.
- Lerne außerdem hilfreiche Software kennen: Github Desktop, Visual Studio Code / andere Editoren, Git Bash, [git-fork](https://git-fork.com/), GitKraken etc.
- Beantrage ggf. [Github Student Developer Pack](https://education.github.com/students) (optional, aber nice to have)
- **Such dir engagierte Leute** und
- Informiere dich bei deinen Kommilitonen, ob schon jemand ein Repo / eine Orga angelegt hat. Falls wir (PI19) das mitkriegen folgt hier ein Link:
  - https://github.com/importPI20fromDHGE
  - Ansprechpartner: J. Müller, PIB20
- Es gibt schon ein Repo oder eine Orga? Dort weiterlesen.
- Es gibt noch kein Repo? Übernimm Verantwortung:
1. Lege eine Organisation mit passendem Namen und Einstellungen an. (Wie wäre es mit importPI20fromDHGE?)
2. Forke dieses Repository mit der Organisation als Besitzer, ändere ggf. den Namen.
2. Nimm alle Sicherheitseinstellungen vor, stell das Repo auf Public, **lade deine Kommilitonen zur Organsiation ein**, *verwalte Rechte*.
4. Klone (`git clone`) das neue Repo lokal auf deinem Computer.
5. Passe ggf. das Top-Level README.md an.

Und dann kann es losgehen!

## Contributing PI 19

Alle Kommilitonen PI 19 sind dazu eingeladen, ihre eigenen Beiträge zu diesem Projekt zu leisten und ihre Ideen einzubringen. Wenn du einen Beitrag leisten willst, kannst du wie folgt vorgehen:

1. Wenn du hier neu bist, erstelle auf jeden Fall ersteinmal [ein Issue](https://github.com/importPI19fromDHGE/dhge-pi19-sem4/issues/new). Dann können wir uns gerne über deine Idee austauschen.
2. `git clone` diese Repo und erstelle mit `git checkout -b <branchname>` eine neue Branch
3. Implementiere deine Idee. Bei Fragen kannst du dich gerne über das Issue an uns wenden.
4. Erstelle eine Pull Request, markiere dabei via @mention die Personen aus dem Issue und warte auf Feedback.

## Module

- [DBS - Datenbanken](./DBS-DORENDORF)
- [RES - Betriebssystemverwaltung](./RES-GUENTHER)
- [PRO - IT-Trends](./PRO-KASCHE)
- [SWE - Systemanalyse](./SWE-KASCHE)
- [NET - Rechnernetze](./NET-FELDMANN)

## Markdown-Erweiterungen

Alle Skripte in diesem Repository sind im `markdown`-Format verfasst. Für dieses existieren [viele verschiedene Standards](https://de.wikipedia.org/wiki/Markdown#Weiterentwicklungen,_Variationen_und_Erg%C3%A4nzungen). Auf Github selbst ist der Funktionsumfang von `markdown` im Vergleich zu anderen Standards deutlich eingeschränkt. Es ist beispielsweise nicht möglich die Größe von Bilder zu definieren, Metadaten für Dokumente anzugeben oder Mathematische Formel darzustellen. Aus diesem Grund wird [`pandoc`](https://pandoc.org/) verwendet, um `markdown`-Dateien mit vielen Funktionserweiterungen in PDFs umzuwandeln. Damit eine Kompatibilität zum Github-`markdown` haben wir eigene Erweiterungen definiert, die im Folgenden beschrieben werden:

### Bildgröße

```md
![Bildbeschreibung](img/a.png)<!--width=200px-->
![Bildbeschreibung](img/b.png)<!--height=200px-->
```

### Pagebreaks usw.

```md
<!--pagebreak-->
<!--newpage-->
<!--clearpage-->
```

### Mathematische Formel

Github unterstützt keine mathematischen Formeln. Als Workaround gibt es eine [Erweiterung für Chrome](https://github.com/orsharir/github-mathjax). Ansonsten können Formeln in ihrer vollen Pracht nur in den PDFs betrachtet werden.
