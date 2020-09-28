Datenbanken
===========

# Grundlagen

## Begriffe

- **Datenbank:** Menge von Daten, die redundanzfrei unter Steuerung eines DBMS gespeichert, verwaltet und manipuliert wird
	- Modell der Informationen und Informationsstrukturen als Ausschnitt der realen Umwelt
- **Datenbank-Management-System (DBMS):** Programme die für den direkten Zugriff auf die Datenbank zugreifen und Operationen über die Daten durchführen (externe Programme greifen indirekt über DBMS zu)
- **Modell:** Abbild eines Ausschnitts der objektiven Realität (Ergebnis eines zielgerichteten Modellbildungsprozesses)
- **Datenmodell:** Modellierungsvorschrift die aus bestimmten Strukturtypen,
festen Integrationsvorschriften (Zuordnung zu Objekt- und Beziehungstypen) und Operationen
- **Schema:** formalisierte Darstellung des Modells (grafisch oder normalsprachlich) nach bestimmten Vorschriften
	- Schema-Mapping: Abbilden von Objekten eines höheren Schemas auf ein tieferes Schema

### Vorteile von Datenbanken

- Redundanzminderung
- zentrale Verwaltung (-> höhere Datensicherheit)
- Datenintegrität und Konsistenz
- Trennung von Programmen und Datenhandhabung (Datenunabhängigkeit)
	- physische Datenunabhängigkeit: Anwenderprogramme sind von der physischen Speicherung der Daten unabhängig
	- logische Datenunabhängigkeit: logische Sicht eines Programmes bleibt in der Gesamtsicht der Daten unverändert

### Aufgaben von DBMS

- Definition der eigentlichen Daten, Zugriffshilfen und Benutzersichten
- Datenmanipulation: Retrieval, Update
- Datenverwaltung: Laden und Entladen der DB, Modifizieren von Speicherstrukturen, Reorganisation
- Datensicherheit: Zugriffskontrolle, Sicherung der Integrität, Synchronisation von Mehrfachzugriffen

## Architekturen von DBMS

### Drei-Ebenen-Konzept

**Externe Ebene**

- Beschreibung der externen Sichtweise auf die Daten (unabhängig von der internen Struktur)

**Konzeptuelle Ebene**

- Informationsangebot: logische Gesamtstruktur, Eigenschaften und Beziehungen der Daten
- neutral gegenüber externen Sicht auf Daten (logische Datenunabhängigkeit)
- Standard: relationales Modell

**Interne Ebene**

- geeigneten physischen Datenstrukturen in Abhängigkeit von Realitätsmodell der konzeptionellen Ebene und hardwarespezifischen Eigenschaften (physische Datenunabhängigkeit)

### Weitere Komponenten eines DBMS

|                     | Datensystem    |                        |
|---------------------|----------------|------------------------|
| Metadatenverwaltung | Zugriffssystem | Transaktionsverwaltung |
|                     | Speichersystem |                        |

### DBMS im Schichtenmodell

- Schichtenmodell = Kommunikation direkt benachbarter Schichten über Schnittstellen
- **Datensystem:** Übersetzung und Optimierung von Anfragen externer Programme (-> Satzzugriffe)
- **Zugriffsverwaltung:** Verwaltung physischer Sätze und Zugriffspfade (-> Seitenzugriffe)
- **Speichersystem:** Puffer- und Externspeicherverwaltung (-> Daten)
- Weitere Verfeinerung des Schichtenmodells möglich

## Datenzugriffe

Ablauf zur Verarbeitung von Anfragen:

- Externes Programm stellt Anforderung (SQL) an das DBMS
- Prüfen der Anforderung (mit Beschreibungsinformationen) und Vorbereitung der Ausführung (Ausführungsplan, -optimierung)
- Anforderung der benötigten Datenblöcke
- Pufferverwaltung liest Blöcke aus dem Datenbankpuffer/vom Datenträger ein und stellt sie zur Verfügung
- Aufbereitung der Daten und Übertragung in den Speicherbereich des externen Programmes
- Meldung über Ausführung der Anforderung und Bereitstellung der Daten
