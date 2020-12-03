# DHGE - Praktische Informatik - Matrikel 19 - Semester 3

Dieses Repository ist ein Projekt von Studierenden des Studiengangs "Praktische Informatik" der Dualen Hochschule Gera-Eisenach. Hier werden alle Mitschriften der einzelnen Modulen gesammelt. Die Skripte liegen im `markdown`-Format vor. Zur besseren Handhabung (und weil Github nur begrenzte `markdown`-Features bereitstellt) werden diese zusätzlich automatisch in [PDFs](https://github.com/importPI19fromDHGE/dhge-pi19-sem3/releases) umgewandelt und zur Verfügung gestellt.

## Contributing

Alle Kommilitonen sind dazu eingeladen, ihre eigenen Beiträge zu diesem Projekt zu leisten und ihre Ideen einzubringen. Wenn du einen Beitrag leisten willst, kannst du wie folgt vorgehen:

1. Wenn du hier neu bist, erstelle auf jeden Fall ersteinmal [ein Issue](./issues). Dann können wir uns gerne über deine Idee austauschen.
2. Forke dieses Repository
3. `git clone <fork>` deine Fork und erstelle mit `git checkout -b <branchname>` eine neue Branch
4. Implementiere deine Idee. Bei Fragen kannst du dich gerne über das Issue an uns wenden.
5. Erstelle eine Pull Request, markiere dabei die Personen aus dem Issue und warte auf Feedback.

## Module

- [DBS - Datenbanken](./DBS)
- [RES - Betriebssystemverwaltung](./RES)
- [PRO - IT-Trends](./PRO)
- [SWE - Systemanalyse](./SWE)
- [NET - Rechnernetze](./NET)

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
