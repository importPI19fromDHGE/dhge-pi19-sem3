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

# SQL

## Datenbanken

**Datenbank erstellen**
```sql
CREATE DATABASE bibliothek
ON PRIMARY ( name = 'bibliothek', filename= N'c:\DB\bibliothek.mdf', size = 20MB, filegrowth= 5%)
LOG ON ( name = 'bibliothek_log', filename= N'c:\DB\bibliothek.ldf', size = 5MB, filegrowth= 1MB, maxsize= 50MB);
```

**Datenbank auswählen**
```sql
USE bibliothek;
go
```

**Datenbank löschen**
```sql
DROP DATABASE bibliothek;
```

## Datentypen

| Datentyp                        | Beschreibung                                          |
|---------------------------------|-------------------------------------------------------|
| `smallint, integer, bigint`     | Ganze Zahlen                                          |
| `numeric, decimal, number(n,m)` | Festkommazahlen                                       |
| `float, double`                 | Gleitkommazahlen                                      |
| `char(n)`                       | Zeichenkette der Länge n (`nchar` für Unicode)        |
| `varchar(max)`                  | Zeichenkette variabler Länge (`nvarchar` für Unicode) |
| `date, time, datetime`          | Datums- und Zeitangaben                               |
| `bit`                           | Einzelner Bit (Wahrheitswert)                         |

## Tabellen

### Tabellen erstellen

```sql
CREATE TABLE Autor (
	id bigint PRIMARY KEY IDENTITY(0,1),
	name nvarchar(100) NOT NULL,
	vorname nvarchar(100) NOT NULL,
	geb_jahr smallint,
);

CREATE TABLE Buch (
	id bigint PRIMARY KEY IDENTITY(0,1),
	isbn varchar(30) UNIQUE NOT NULL,
	titel nvarchar(100) NOT NULL,
	preis numeric(6,2),
	leihbar bit DEFAULT 1,
	erschienen_am date,
);

CREATE TABLE Buch2Autor(
	autor_id bigint NOT NULL FOREIGN KEY REFERENCES Autor(id),
	buch_id bigint NOT NULL FOREIGN KEY REFERENCES Buch(id),
	CONSTRAINT pk_buch2autor PRIMARY KEY (buch_id, autor_id)
);
```

### Eigenschaften für Tabellenspalten

| Attribut        | Beschreibung                                                                                 |
|-----------------|----------------------------------------------------------------------------------------------|
| `PRIMARY KEY`   | Primärschlüssel                                                                              |
| `IDENTITY(n,m)` | Wert dieser Spalte wird automatisch gesetzt (aufsteigend beginnend bei n mit Schrittweite m) |
| `NOT NULL`      | Wert dieser Spalte darf nicht leer sein                                                      |
| `UNIQUE`        | Wert dieser Spalte muss innerhalb der Spalte einzigartig sein                                |
| `DEFAULT 0`     | Standartwert für die Spalte                                                                  |
