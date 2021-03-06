Datenbanken-Praktikum
=====================

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Inhaltsverzeichnis**

- [Datenbanken-Praktikum](#datenbanken-praktikum)
- [Formen von Kundenanforderungen](#formen-von-kundenanforderungen)
- [Schematische Darstellung](#schematische-darstellung)
  - [Entity Relationship Diagramm (ERD)](#entity-relationship-diagramm-erd)
  - [Tabellenschema](#tabellenschema)
- [Constraints und Kardinalitäten](#constraints-und-kardinalitäten)
- [Vorgehensweise zur Modellierung einer Datenbank](#vorgehensweise-zur-modellierung-einer-datenbank)
- [Relationship-Matrix](#relationship-matrix)
- [SQL](#sql)
  - [Datenbanken](#datenbanken)
  - [Datentypen](#datentypen)
  - [Tabellen](#tabellen)
    - [Tabellen erstellen](#tabellen-erstellen)
    - [Eigenschaften für Tabellenspalten](#eigenschaften-für-tabellenspalten)
    - [verändern von Tabellen](#verändern-von-tabellen)
    - [Constraints](#constraints)
  - [Daten einfügen](#daten-einfügen)
  - [Daten lesen](#daten-lesen)
  - [Aggregatsfunktionen](#aggregatsfunktionen)
  - [Unterabfragen](#unterabfragen)
  - [Unions](#unions)
  - [Gruppieren](#gruppieren)
  - [Joins](#joins)
  - [Daten verändern](#daten-verändern)
  - [Daten löschen](#daten-löschen)
    - [Truncate](#truncate)
    - [Tabelle löschen](#tabelle-löschen)
    - [Spalte löschen](#spalte-löschen)
  - [Views](#views)
  - [Transaktionen](#transaktionen)
  - [Indices](#indices)
  - [Trigger](#trigger)
    - [DML-Trigger](#dml-trigger)
      - [`AFTER`-Trigger](#after-trigger)
      - [Instead-of-Trigger](#instead-of-trigger)
    - [`DDL`-Trigger](#ddl-trigger)
  - [Stored Procedures](#stored-procedures)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

<!--newpage-->

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

![Bestandteile eines ERD](assets/ERD_Bestandteile.png)<!-- width=400px -->

Beispiel-ERD:

![Beispiel-ERD](assets/unternehmenERD.png)<!-- width=400px -->

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

![Arten von Constraints](assets/constraints.png)<!-- width=400px -->

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
ON PRIMARY ( name = 'bibliothek' /*logischer Name*/, filename= N'c:\DB\bibliothek.mdf'  /*UTF-8 kodierter Pfad (N-Prefix)*/, size = 20MB, filegrowth= 5%)
LOG ON ( name = 'bibliothek_log', filename= N'c:\DB\bibliothek.ldf', size = 5MB, filegrowth= 1MB, maxsize= 50MB); /* Achtung: Keine Änderungen nach erreichen des Limits mehr möglich*/
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

| Datentyp                        | Beschreibung                                                             |
|---------------------------------|--------------------------------------------------------------------------|
| `smallint, integer, bigint`     | Ganze Zahlen                                                             |
| `numeric, decimal, number(n,m)` | Festkommazahlen                                                          |
| `real, float`                   | Gleitkommazahlen                                                         |
| `char(n)`                       | Zeichenkette der Länge n Bytes (`nchar` für Unicode)                     |
| `varchar(n)`                    | Zeichenkette mit variabler Speicherreservierung (`nvarchar` für Unicode) |
| `date, time, datetime`          | Datums- und Zeitangaben                                                  |
| `bit`                           | Einzelner Bit (Wahrheitswert)                                            |

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

create table Verlag (
	id bigint PRIMARY KEY,
	name nvarchar(50) NOT NULL,
	plz char(6),
	ort nvarchar(50) NOT NULL,
	strasse nvarchar(100),
	webseite nvarchar(200)
	);

create table nutzer(
	id bigint PRIMARY KEY IDENTITY(1,1),
	name nvarchar(50) NOT NULL,
	vorname nvarchar(50) NOT NULL,
	plz char(6),
	ort nvarchar(100) NOT NULL,
	strasse nvarchar(100)
);

create table ausleihe(
	id bigint PRIMARY KEY IDENTITY(1,1),
	exemplar_id bigint FOREIGN KEY REFERENCES exemplar(id) NOT NULL,
	nutzer_id bigint FOREIGN KEY REFERENCES nutzer(id) NOT NULL,
	leih_dat date DEFAULT(convert(date,getdate())) /*holt sich im Default die Systemzeit (als datetime) und wandelt es zu date um*/
);
```

- Einfügen von Fremdschlüsseln beim CREATEn ist Implementierungs-spezifisch. MSSQL: ``buch_id bigint FOREIGN KEY REFERENCES Buch(id) NOT NULL``
- Vorsicht: es gibt Syntax-Unterschiede zwischen CREATE und ALTER

```sql
create table Exemplar (
	id bigint PRIMARY KEY, /*Spalte ID vom Typ BigInt, Primärschlüssel*/
	buch_id bigint FOREIGN KEY REFERENCES Buch(id) NOT NULL,
	anschaffung date,
	standort nvarchar(40) NOT NULL, /*variabler Speicherplatz, aber maximal 100 Zeichen. Darf nicht leer sein*/
	leihbar bit
	);

create table Buch2Verlag (
	buch_id bigint FOREIGN KEY REFERENCES Buch(id) NOT NULL,
	verlag_id bigint FOREIGN KEY REFERENCES Verlag(id) NOT NULL,
	CONSTRAINT pk_buch2verlag PRIMARY KEY (buch_id, verlag_id)
	/*erstellt einen Constraint vom Primärschlüssel-Typ --> buch_id und verlag_id sind PKs*/
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
| `DEFAULT(n)`    | Standardwert für die Spalte                                                                  |
| `FOREIGN KEY`   | Fremdschlüssel                                                                               |
| `ON DELETE`     | Aktion beim Löschen der Zeile                                                                |
| `ON UPDATE`     | Aktion beim Aktualisieren der Zeile (verändern der Daten)                                    |

### verändern von Tabellen

[Microsoft Dokumentation](https://docs.microsoft.com/de-de/sql/t-sql/statements/alter-table-table-constraint-transact-sql?view=sql-server-ver15)

```sql
ALTER TABLE buch ALTER COLUMN preis numeric(6,2);
/*ändert in der Tabelle Buch die Spalte preis*/

ALTER TABLE buch ADD Auflage smallint DEFAULT 1;
/*fügt in der Tabelle buch die Spalte Auflage hinzu*/

ALTER TABLE tabellenName ADD
CONSTRAINT constraintName PRIMARY KEY (col1, col2);
/*fügt eine Constraint nachträglich hinzu*/

ALTER TABLE tabellenName DROP CONSTRAINT constraintName;
/*löscht Constraint*/

ALTER TABLE	Buch2Verlag  ADD
CONSTRAINT ck_buch2verlag_plz CHECK /*Check Constraint prüft, ob Daten in best. Form vorliegen*/
(plz LIKE '[a-z][0-9][0-9][0-9][0-9][0-9]');

ALTER TABLE buch ADD Constraint ck_buch_seiten CHECK (seiten BETWEEN 1 AND 5000);
```

Wenn eine Spalte gelöscht wird / aktualisiert wird, kann man über ein Constraint eine Aktion ausführen:

```sql
ALTER TABLE tabellenName ADD
CONSTRAINT constraintName PRIMARY KEY (col1, col2)
ON DELETE CASCADE
ON UPDATE CASCADE;
```

| Aktion          | Zweck                               |
| :-------------- | :---------------------------------- |
| ``CASCADE``     | kaskadierendes Löschen / Update     |
| ``SET NULL``    |              setze Zelle auf `NULL` |
| ``SET DEFAULT`` | setze Zelle auf den Default-Wert    |
| ``NO ACTION``   | ...                                 |

### Constraints

- FOREIGN KEY und CHECK Constraints erlauben eine vorl. Deaktivierung
  - Deaktivierung: ``ALTER TABLE Ausleihe NOCHECK CONSTRAINT FK_AusleihNutzer;``
  - Reaktivierung: ``ALTER TABLE Ausleihe   CHECK CONSTRAINT FK_AusleihNutzer;``

## Daten einfügen

- Syntax: ``INSERT INTO tabellenname(zu,befüllende,spalten) VALUES (daten,hier,eintragen)``
  - die Spaltenliste und ``VALUES`` muss nicht angegeben werden, wenn alle Spalten in der richtigen Reihenfolge eingetragen werden

## Daten lesen

- Syntax: ``SELECT spalte1, spalte2 FROM tabelle``
- alle Spalten: ``SELECT * FROM tabelle``
- Angabe von Bedingungen: Schlüsselwort ``WHERE``: ``SELECT * FROM Buch WHERE Seiten = 128``
  - Vergleichsoperatoren: ``=``, ``<``, ``>``, ``<=``, ``>=``, ``!=``, ``<>``, ``!>``, ``!<``
  - Angabe von Bereichen mit ``BETWEEN``: ``SELECT * FROM buch WHERE Seiten BETWEEN 100 AND 500``
  - logische Verknüpfungen möglich: ``SELECT * FROM Buch WHERE Seiten = 128 AND verlag_id = 7``
  - logische Operatoren: ``NOT``, ``AND``, ``OR`` in genau dieser Rangreihenfolge
  - Klammerung möglich
- Select von Daten aus mehreren Tabellen: ``SELECT Titel, ISBN, Seiten FROM Buch, Verlag WHERE Verlag.id = Buch.Verlag_id AND Verlag.Name = 'Eichborn Verlag'``
  - wenn es zu Namenskonflikten kommt, kann man auch die Spalten mit dem ``tabelle.spalte``-Syntax angeben
  - Arbeit mit Wildcards mit ``like``: ``WHERE Verlag.Name like '%Eichborn'``
  - akzeptierte Wildcards:
    - ``%`` - beliebig viele Zeichen
    - ``_`` - genau ein Zeichen
    - ``[aeiou]%`` - beginnt mit Vokal
    - ``[^aeiou]%`` - beginnt mit Konsonant
    - ``[a-k]%`` - beginnt mit A bis K
- Sortieren mit ``ORDER BY``: ``SELECT * FROM abteilung ORDER BY abteilung.bezeichnung``
  - für umgekehrte Sortierung: anfügen des Schlüsselwortes ``DESC``
- Aliase:
  - ohne Sonderzeichen ``AS``: ``SELECT Mitarbeiter.vorname AS MA_Vorname``
  - bei Sonderzeichen in eckigen Klammern: ``SELECT Mitarbeiter.vorname [MA Vorname]``
  - Schlüsselwort ``AS`` optional
  - kann auch im ``FROM`` stehen
- Nach ``WHERE`` kann das Schlüsselwort ``IN`` folgen, um bspw. Auswahllisten abzufragen: ``SELECT * FROM Autor WHERE Autor.Name IN ('Goethe', 'Schiller', 'Lessing')``
  - nicht kombinierbar mit ``LIKE``
- Limitieren von Ergebniszeilen mit Schlüsselwort ``TOP``: ``SELECT TOP (10) Titel, Seiten FROM buch ORDER BY Seiten``
- bei der Verwendung von ``ORDER BY`` und ``TOP`` in Kombination kann das Schlüsselwort ``WITH TIES`` verwendet werden, damit "Ties" mit angezeigt werden: ``SELECT TOP (5) WITH TIES Titel, Seiten FROM buch ORDER BY Seiten`` --> zeigt ggf. mehr als 5 an
- Beim Selektieren können Zeilen übersprungen werden:

```sql
-- diese Variante ist für kleinere Resultsets geeignet
SELECT * FROM autor ORDER BY name
OFFSET 6 ROWS
FETCH NEXT 5 ROWS ONLY;
```

- Schlüsselwort ``DISTINCT`` gibt nur einzigartige Zeilen aus, keine doppelten

## Aggregatsfunktionen

- [Microsoft Dokumentation](https://docs.microsoft.com/de-de/sql/t-sql/functions/aggregate-functions-transact-sql?view=sql-server-ver15)
- Funktionen, die auf Ergebnisse angewendet werden
- oft in Verbindung mit ``SELECT`` oder ``GROUP BY``
- Bsp.: Nutzer zählen mit count(): ``SELECT COUNT(*) FROM nutzer``

```sql
-- zeigt alle Nutzer ohne Email-Adresse an
SELECT COUNT(*) FROM nutzer
WHERE email IS NULL
OR email = '';

-- zeigt das Buch mit größter Seitenzahl an:
SELECT MAX(seiten) FROM buch
```

| Funktion                | Zweck                                                              |
| :---------------------- | :----------------------------------------------------------------- |
| MAX()                   | Maximum                                                            |
| MIN()                   | Minimum                                                            |
| SUM()                   | Summe                                                              |
| AVG()                   | Mittelwert                                                         |
| COUNT()                 | zählt Ergebniszeilen                                               |
| COUNT_BIG()             | wie Count, gibt bigint zurück                                      |
| GROUPING()              | wird Spaltenabfrage in ``GROUP BY`` aggregiert?                    |
| GROUPING_ID()           | berechnet Ebene der Gruppierung                                    |
| STRING_AGG()            | Concat. Strings mit Trennzeichen                                   |
| CHECKSUM_AGG()          | Prüfsumme                                                          |
| STDEV()                 | Standardabweichung                                                 |
| STDEVP()                | Standardabweichung für die Population                              |
| VAR()                   | stat. Varianz                                                      |
| VARP()                  | Varianz für die Population                                         |
| APPROX_COUNT_DISTINCT() | ungefähre Anzahl von eindeutigen Nicht-Null-Werten in einer Gruppe |

## Unterabfragen

- "Select im Select"
- Bsp.: alle Bücher selektieren, die überdurchschnittlich viele Seiten haben:

```sql
SELECT buch.titel, buch.seiten FROM buch
WHERE seiten > (SELECT AVG(seiten) FROM buch)
ORDER BY seiten;
```

## Unions

- ein Result Set aus mehreren Abfragen
- funktioniert nur für ähnliche - sprich zusammenführbare - Spalten

```sql
SELECT name, vorname FROM nutzer UNION
SELECT name, vorname FROM autor;
```

## Gruppieren

**sehr klausurrelevant, so der Hinweis von Herr Grimm**

- mit Schlüsselwort ``GROUP BY``
- Bsp.: wie oft kommen Namen vor?

```sql
SELECT name, COUNT(*) anzahl FROM nutzer GROUP BY name ORDER BY anzahl DESC;
```

- mit ``HAVING`` kann weiter eingeschränkt werden: nur Nutzer ausgeben, die mind. 2 Mal vorkommen

```sql
SELECT name, COUNT(*) anzahl FROM nutzer GROUP BY name HAVING COUNT(*) > 1 ORDER BY anzahl DESC;
```

```sql
-- alle Bücher, die mehr als 1 Autor haben
SELECT titel, COUNT(*) [Anzahl Autoren] FROM buch, autor, Buch2Autor
WHERE buch2autor.Autor_id = autor.id AND Buch2Autor.Buch_id = buch.id
GROUP BY titel HAVING COUNT(*) > 1;

-- alle Autoren, die mehr als 1 Buch geschrieben haben
SELECT name, vorname, COUNT(*) [Anzahl Bücher] FROM buch, autor, Buch2Autor
WHERE buch2autor.Autor_id = autor.id AND Buch2Autor.Buch_id = buch.id
GROUP BY autor.name, autor.Vorname HAVING COUNT(*) > 1;
```

## Joins

- Vereinigung von Abfragen

![Übersicht von Joins](./assets/joins.png)<!-- width=500px -->

```sql
SELECT titel, name FROM buch, verlag WHERE buch.verlag_id = verlag.id;

-- macht dasselbe wie

SELECT titel, name FROM buch
INNER JOIN verlag ON buch.Verlag_id = verlag.id;
```

```sql
-- alle Nutzer mit ggf. ausgeliehenen Büchern
SELECT name, vorname, titel FROM nutzer
LEFT JOIN ausleihe ON nutzer.id = ausleihe.nutzer_id
LEFT JOIN exemplar ON ausleihe.exemplar_id = exemplar.id
LEFT JOIN buch ON exemplar.buch_id = buch.id;

-- Verlage in der gleichen Stadt
SELECT DISTINCT v1.name, v1.ort, v1.plz FROM verlag v1
JOIN verlag v2 ON v1.ort = v2.ort
WHERE v1.id != v2.id
ORDER BY v1.ort;
```

- Joins mit ``WHERE a.id = b.id`` werden implizite Joins genannt

## Daten verändern

- mit Schlüsselwort `UPDATE`
- angeben, welche Spalte welchen Wert erhält
- `UPDATE tabelle SET spalte = xyz WHERE bedingung`
  - WHERE optional, aber dann wird `UPDATE` für jede Zeile ausgeführt
- Rechnen ist mit folgenden Operatoren unterstützt: `| & ^ + - * / %`
  - alle Operatoren unterstützen auch die Form `+=` etc.
- Werte können aus anderen Spalten übernommen werden

```sql
-- André Grimm --> André Kaudelwerk
UPDATE nutzer SET name = 'Kaudelwerk' WHERE id =
(SELECT id FROM nutzer WHERE name = 'Grimm' AND vorname = 'André');

-- Rechnen ist erlaubt: alle Bücher +10 Seiten
UPDATE buch SET seiten = seiten + 10;

-- Werte aus anderen Tabellen übernehmen: Klappentext mit Name des Verlag ersetzen
UPDATE Buch SET Buch.Klappentext = Verlag.Name
FROM Buch JOIN Verlag ON Verlag.id = Buch.Verlag_id
```

## Daten löschen

- mit Schlüsselwort `DELETE`
- `DELETE FROM tabelle WHERE bedingung`
- Good Practice: Primärschlüssel als Bedingung wählen
- Indices werden bei `DELETE` nicht zurückgesetzt (Fragmentierung)
- Alle Daten aus einer Tabelle löschen und Indices zurücksetzen: `TRUNCATE TABLE tabelle`
- Löschen der gesamten Struktur einer Tabelle `DROP TABLE tabelle`
- Löschen eines Constraints `ALTER TABLE tabelle DROP CONSTRAINT contraint`
- Löschen der gesamten Datenbank `DROP DATABASE datenbank`

```sql
-- Buch mit ID 27 löschen
DELETE FROM Buch WHERE id = 27;
-- Alle Bücher löschen, Indices zurücksetzen
TRUNCATE TABLE Buch;
-- Tabelle Buch mit allen Strukturen löschen
DROP TABLE Buch;
```

### Truncate

Wenn auch Indices gelöscht werden sollen: Nutzung von ``TRUNCATE`` geeignet:

```sql
TRUNCATE TABLE thema;
```

- effizienter
- **keine Protokollierung --> kein Rückgängig-machen**

### Tabelle löschen

```sql
DROP TABLE tabelle;
```

- löscht auch Indices usw.

### Spalte löschen

```sql
ALTER TABLE tabelle DROP COLOUMN spalte;
```

## Views

- vgl. "Alias für eine Abfrage"
- nach der Erstellung wie normale Tabellen verwendbar
- zusätzliche Attribute:
	- `ENCRYPTION` Unterliegende Datenbankstruktur der Basistabellen nicht preisgeben (siehe unten)
	- `SCHEMABINDING` View fest an das Schema der Basistabelle binden
  	- Tabellenstrukturänderungen sind dann nur möglich, wenn sie nicht die View betreffen
	- `VIEW_METADATA` Bei Abfrage des Views über die API werden die View-Metadaten statt den Basistabellen-Daten gesendet

```sql
-- Erleichterter Zugriff auf Buch und Exemplar Informationen
CREATE VIEW vBuchExemplar (ExemplarNr, Buchtitel, ISBN, RegalNr)
WITH ENCRYPTION, SCHEMABINDING, VIEW_METADATA
AS SELECT Exemplar.ExemplarNr, Buch.Titel, Buch.ISBN, Exemplar.RegalNr
FROM Exemplar
JOIN Buch ON Exemplar.Buch_id = Buch.id;
-- View wie normale Tabelle verwenden
SELECT * FROM vBuchExemplar;
-- View löschen
DROP VIEW vBuchExemplar;
```

- speichert Abfrageergebnisse und generiert bei Bedarf an der geforderten Stelle eine temporäre Tabelle
- Nutzen:
  - Änderung von Berechtigungen
  - Speichern rechenintensiver Abfragen zur Verbesserung der Effizienz
  - Generierung von Views zur Bereitstellung von Abwärtskompatibilität

- anzeigen, wie View erstellt wurde: ``SELECT * FROM sys.syscomments``
  - Debug-Informationen wie Kommentar und genaue ``CREATE VIEW``-Query
  - kann mit ``ENCRYPTION``-Attribut umgangen werden

Beispiel: View mit Name, Vorname von Autor, dessen Nationalität und Anzahl der Bücher in der DB:

```sql
CREATE VIEW vAutorNat AS
SELECT autor.name, autor.vorname, nationalitaet.bezeichnung, count(*) [Anzahl Bücher]
FROM nationalitaet
JOIN autor ON nationalitaet.id = autor.nationalität_id
JOIN buch2autor ON autor.id = buch2autor.autor_id
GROUP BY autor.name, autor.vorname, nationalitaet.bezeichnung;

SELECT * FROM vAutorNat ORDER BY [Anzahl Bücher] DESC;
```

## Transaktionen

- Änderungen werden in ein Overlay geschrieben, d.h. in temporäre Tabellen

Aufbau:

```sql
BEGIN TRANSACTION
[...]
UPDATE nutzer SET ort =  'Gera'
SELECT vorname, name, ort FROM nutzer;

-- Rolle rückwärts:
ROLLBACK

SELECT vorname, name, ort FROM nutzer;
```

- anstelle des ``ROLLBACK`` kann auch ``COMMIT`` ausgeführt werden, damit die Änderungen übernommen werden
- wird auch manuell gesteuert, d.h. außerhalb eines Skriptes

## Indices

- der Primärschlüssel ist automatisch der clustered Index
- für jeden unique Key wird automatisch ein nonclustered Index erstellt

**ungruppierte (nonclustered) Indices**

- Index für eine Spalte
- neue Tabelle mit zwei Spalten wird erstellt
- 1. Spalte speichert Inhalt aus eigentlicher Tabelle, aber sortiert
- 2. Spalte speicher Position davon
- Vorteil: schnelles Suchen
- Nachteil: mehr Speicherbedarf

**gruppierte (clustered) Indices**

- bildet ganze Tabelle ab -> nur 1 pro Tabelle erlaubt
- sortiert abhängig von best. Spalte
- Vorteil: kein zusätzl. Speicherbedarf
- Nachteil: beim Ändern von Daten muss Index ggf. neu erstellt werden
- braucht temporär mehr RAM (bis zu 20%)

```sql
-- nonclustered Index erstellen:
CREATE INDEX ix_Buchtitel ON Buch(titel DESC);
-- clustered Index erstellen:
CREATE CLUSTERED INDEX ix_Buchtitel ON Buch(Titel);
```

## Trigger

- "Auslöser" -> reagieren auf definiertes Ereignis
- vgl. Prozedur ohne Parameter
- Arten:
	- `DML`: Data Manipulation Language (reagieren auf `INSERT`, `UPDATE`, `DELETE`)
		- sichern Datenkonsistenz, prüfen Daten <!--eignet sich auch zum pfuschen ;)-->
	- `DDL`: Data Definition Language (reagieren auf `ALTER`, ``CREATE``, ``DROP``)
- mehrere Trigger für ein Ereignis und ein Trigger für mehrere Ereignisse möglich
- wenn möglich, sollte man für bessere Effizienz Constraints anstelle von Triggern verwenden
- Löschen von Triggern mit ``DROP TRIGGER triggername;``

### DML-Trigger

####  `AFTER`-Trigger <!--höhö-->

- lösen aus, nachdem Ereignis aufgetreten ist

```sql
CREATE TRIGGER tr_BuchInsert ON buch
AFTER INSERT AS-- UPDATE, DELETE
DECLARE @title nvarchar(100);
SELECT @title = titel FROM inserted;  -- deleted
PRINT 'Buch hinzugefügt: ' + @title;
```

Wenn man ein Buch einfügt, erhält man:

```txt
Buch hinzugefügt: Buchtitel

(1 row affected)

Completion time: 2020-11-25T14:37:17.3255273+01:00
```

- Ereignisse werden in temporären Tabellen - bspw. `inserted` oder `deleted` gespeichert
- Hinweis: ein UPDATE löst einen `DELETE` und einen `INSERT` aus
- Deaktivieren mit `DISABLE TRIGGER triggername`
- Reaktivieren mit `ENABLE TRIGGER triggername`

Trigger zur Prüfung des Nutzeralters:

```sql
-- Trigger für Nutzer: Fehlermeldung, wenn Alter > 130

CREATE TRIGGER tr_NutzerAlter ON nutzer
AFTER INSERT AS
DECLARE @age int;
DECLARE @id bigint;
SELECT @id = id from inserted; -- von temp. Tabelle
SELECT @age = (CONVERT(int, getdate()) - CONVERT(int, gebdat)) / 365 FROM inserted;

IF @age > 130
BEGIN
  DELETE FROM nutzer WHERE ID = @id;
  RAISERROR('Das Alter ist zu hoch!', 15, 1);
  /*
    nach Nachricht folgt Schweregrad und Status -> frei wählbar:
    Schweregrad von 0 bis 18; 19 bis 25 sind für Administratoren reserviert.
    Status von 0 bis 255
  */
END;
```

- Übung: Erstellen Sie einen Trigger, der beim Einfügen einess Buches überprüft, ob es einen Verlag mit der angegebenen Verlags-ID gibt. Wenn nicht, wird der Eintrag wieder gelöscht und eine Fehlermeldung ausgegeben.

```sql
CREATE TRIGGER tr_verlagPrüfen ON buch
AFTER INSERT AS

DECLARE @vid bigint;
DECLARE @id bigint;

SELECT @id = id FROM inserted;
SELECT @vid = verlag_id FROM inserted;

IF (SELECT name FROM verlag WHERE id = @vid) IS NULL
BEGIN
  DELETE FROM buch WHERE id = @id; -- ID würde trotzdem eins hochgezählt werden
  RAISERROR('Der angegebene Verlag existiert nicht!', 15, 1);
END;
```

#### Instead-of-Trigger

- werden anstelle des Ereignisses ausgeführt
- ``INSERT`` / ``UPDATE`` / ``DELETE`` werden dennoch in ``inserted`` bzw. ``deleted`` geschrieben
- Übung von oben umgebaut:
- wenn ``INSERT INTO`` mehrere Basistabellen einer View betrifft, schlägt dieser fehl und kann mit ``INSTEAD OF`` Trigger gelöst werden

```sql
CREATE TRIGGER tr_verlagPrüfen ON buch
INSTEAD OF INSERT AS

DECLARE @vid bigint;

SELECT @vid = verlag_id FROM inserted;

IF (SELECT name FROM verlag WHERE id = @vid) IS NULL
BEGIN
	RAISERROR('Der angegebene Verlag existiert nicht!', 15, 1);
ELSE
	INSERT INTO buch (titel, isbn, klappentext, seiten, verlag_id) SELECT titel, isbn, klappentext, seiten, verlag_id FROM inserted; -- * würde hier auch die ID übernehmen, was nicht geht
END;
```

- Übung: Erstellen Sie einen Trigger für die Tabelle `Ausleihe`, der sicherstellt, dass nur Einträge mit gültiger Nutzer-ID und Exemplar-ID zulässt und dass das Exemplar leihbar ist

```sql
CREATE TRIGGER tr_ausleihePrüfen ON ausleihe
INSTEAD OF INSERT AS

DECLARE @nid bigint;
DECLARE @eid bigint;

SELECT @nid = nutzer_id FROM inserted;
SELECT @eid = exemplar_id FROM inserted;

IF ((SELECT id FROM nutzer WHERE id = @nid) IS NULL)
	OR ((SELECT id FROM exemplar WHERE id = @eid) IS NULL)
	OR ((SELECT leihbar FROM exemplar WHERE id = @eid) = 0)
	RAISERROR('Ausleihe fehlgeschlagen! Prüfen Sie Nutzer-ID, Exemplar-ID und Leih-Status!', 15, 1);
ELSE
	INSERT INTO ausleihe (exemplar_id, Nutzer_id, LeihDat, MahnDat, RueckDat, Kosten)
	SELECT exemplar_id, Nutzer_id, LeihDat, MahnDat, RueckDat, Kosten FROM inserted;
```

### `DDL`-Trigger

- beziehen sich einerseits auf **Datenbankbereich** (Tabellen, Sichten, Prozeduren,...) und auf **Server-Bereich** (*Datenbanken*, Logins,...)
- viele Ereignisse, siehe [Docs](https://docs.microsoft.com/de-de/sql/relational-databases/triggers/ddl-events?view=sql-server-ver15)
- da sehr viele: Zusammenfassung in [DDL-Ereignisgruppen](https://docs.microsoft.com/de-de/sql/relational-databases/triggers/ddl-event-groups?view=sql-server-ver15)

Beispiel: auf Server-Ebene

```sql
-- Server-Trigger für das Erstellen einer Datenbank
CREATE TRIGGER tr_createDB
ON ALL SERVER FOR CREATE_DATABASE
AS PRINT 'Eine neue Datenbank erblickt das Licht der Welt. Sag "Hello World!" :-)';

-- Datenbank-Trigger für das löschen einer Tabelle
CREATE TRIGGER tr_drop_table
ON DATABASE FOR DROP_TABLE AS
PRINT 'Eine Datenbank tritt die letzte Reise an und wird erlöst!';
```

Beispiel: auf Datenbank-Ebene

```sql
CREATE TRIGGER tr_createTable
ON DATABASE FOR CREATE_TABLE
AS
SET NOCOUNT ON; -- unterdrückt automatisch generierte Debug Meldungen
DECLARE @Table SYSNAME = eventdata().value('(/EVENT_INSTANCE/ObjetName)[1]', 'sysname');
PRINT 'Die Tabelle' + @Table + 'wurde erstellt';
```

## Stored Procedures

- "gespeicherte Funktionen"
- ähnlich wie Trigger, aber werden durch Nutzer ausgelöst
- Parameter sind möglich
- **Vorteil**: sparen Zeit und verringern Fehlerquellen für komplexe Anfragen
- schneller als normale Anfragen <!--"sin angeblich auch schneller... Weeß ick nich"-->
- werden immer im Rechte-Kontext des Nutzers ausgeführt
- Erstellen:

```sql
CREATE PROC pAutorNatio -- bzw PROCEDURE ausschreiben
@name nvarchar(100), @vorname nvarchar(100) -- Parameter
AS
SET NOCOUNT ON;
SELECT nationalitaet.bezeichnung FROM nationalitaet JOIN autor ON nationalitaet.id = autor.nationalität_id
WHERE autor.name LIKE '%' + @name + '%';
```

```sql
-- Prozedur, die auf Basis eines (unvollständigen) Buchtitels alle passenden Bücher inkl. Autor und Verlag zurückgibt
CREATE OR ALTER PROCEDURE pBuch @titel nvarchar(50) AS
SET NOCOUNT ON; -- deaktiviert Ausgaben des DBMS
SELECT Buch.Titel Buchtitel, Buch.ISBN, Autor.Name Autor, Verlag.Name Verlag FROM Buch
JOIN Verlag ON Verlag.id = Buch.Verlag_id
JOIN Buch2Autor ON Buch.id = Buch2Autor.Buch_id
JOIN Autor ON Autor.id = Buch2Autor.Autor_id
WHERE Buch.Titel LIKE '%' + @titel + '%';
```

Aufruf:

```sql
EXECUTE pAutorNatio 'schiller', '';
EXEC pBuch 'Der';
```

- Best Practice: Filtern von SQL-Schlüsselwörtern, sodass keine bösartigen Parameter ausgeführt werden können
