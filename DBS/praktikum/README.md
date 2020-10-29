Datenbanken-Praktikum
=====================

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Inhaltsverzeichnis**

- [Formen von Kundenanforderungen](#formen-von-kundenanforderungen)
- [Schematische Darstellung](#schematische-darstellung)
  - [Entity Relationship Diagramm (ERD)](#entity-relationship-diagramm-erd)
  - [Tabellenschema](#tabellenschema)
- [Constraints und Kardinalitäten](#constraints-und-kardinalit%C3%A4ten)
- [Vorgehensweise zur Modellierung einer Datenbank](#vorgehensweise-zur-modellierung-einer-datenbank)
- [Relationship-Matrix](#relationship-matrix)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Formen von Kundenanforderungen

- Kundenanforderung kann in folgenden Formen kommen:
  - ausformuliert schriftlich
    - hier ist das Datenbankmodell vorgegeben und man muss es nur noch bauen
  - in Stichpunkten
    - hier könnten Details fehlen, wodurch zusätzliche Kommunikation erforderlich sein kann
  - im Gespräch
    - Entwickler hat hier die Aufgabe, durch gezielte Fragen die wirklichen Anforderungen an das Datenbankmodell zu bestimmen
    - es kann sein, dass der Kunde selbst nicht wirklich weiß, was er haben will

# Schematische Darstellung

Folgende Darstellungen von Datenbankschemata sind am weitesten verbreitet:

Herr Grimm schlägt folgende Tools zur Modellierung vor, falls man noch eins sucht:

```txt
ERD-Tool online:
https://erdplus.com/standalone
https://app.creately.com/diagram/vHwWnnJJu2t/edit
https://cloud.smartdraw.com/ -> Google-Konto
https://app.diagrams.net/

Tabellenschema:
https://lucid.app

MS SQLServer Management Tool (SSMS):
direkter Download -> https://aka.ms/ssmsfullsetup
direkter Download deutsch -> https://go.microsoft.com/fwlink/?linkid=2146265&clcid=0x407
Info-Seite -> https://docs.microsoft.com/de-de/sql/ssms/download-sql-server-management-studio-ssms?view=sql-server-ver15
```

## Entity Relationship Diagramm (ERD)

Die Bestandteile:

![Bestandteile eines ERD](resources/ERD_Bestandteile.svg)

Beispiel-ERD:

![Beispiel-ERD](resources/unternehmenERD.png)

## Tabellenschema

- grafisch
  - ähnlich zum ERD sind Spalten, Beziehungen, etc. dargestellt
- ausformuliert
  - Modell im Fließtext beschrieben
  - Entwickler muss Modell also _herauslesen_

# Constraints und Kardinalitäten

- Constraints legen fest, ob eine Beziehung obligatorisch oder optional ist
- Kardinalitäten legen fest, ob eine Beziehung jeweils ein Attribut oder mehrere verbindet

| Formulierung               | Bedeutung                     |
| :------------------------- | :---------------------------- |
| genau eins                 | obligatorische Beziehung, ?:1 |
| mindestens eins            | obligatorische Beziehung, ?:n |
| höchstens eins             | optionale Beziehung, ?:1      |
| keins oder eins oder viele | optionale Beziehung, ?:n      |

![Arten von Constraints](resources/constraints.png)

- im Zweifelsfall das flexiblere verwenden, für den Fall, dass sich in der Zukunft die Anforderungen ändern

# Vorgehensweise zur Modellierung einer Datenbank

Es wird folgende Reihenfolge vorgeschlagen:

- Entitäten und Attribute modellieren
- Primärschlüssel wählen
- Beziehungen modellieren
- Kardinalitäten festlegen
- Modell überprüfen

# Relationship-Matrix

- Eine Tabelle, in der Attribute und Beziehungen eingetragen werden
- hilft, einen Überblick über sein Modell zu behalten
- wird zeilenweise gelesen
- gegenüberliegende Relationen sollten sinnvoll gespiegelt werden

|                  | Abteilung | Abteilungsleiter | Mitarbeiter    | Projekt     |
| :--------------: | :-------: | :--------------: | :------------: | :---------: |
| Abteilung        | xxxxxxxxx | geführt von      | ist zugeordnet |             |
| Abteilungsleiter | leitet    | xxxxxxxxxxxxxxxx | ist            |             |
| Mitarbeiter      | gehört zu | ist              | xxxxxxxxxxxxxx | arbeitet an |
| Projekt          |           |                  | ist zugeordnet | xxxxxxxxxxx |
