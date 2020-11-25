IT-Trends
=========

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Inhaltsverzeichnis**

- [Einleitung](#einleitung)
  - [IT-Trends nach IDC](#it-trends-nach-idc)
  - [Disruptionen](#disruptionen)
  - [Agile Methoden](#agile-methoden)
  - [Cloud Computing](#cloud-computing)
    - [Edge Computing](#edge-computing)
  - [Künstliche Intelligenz](#k%C3%BCnstliche-intelligenz)
  - [Agile Entwicklung und DevOps-Methoden als Schlüssel für hohe Entwicklungsgeschwindigkeit](#agile-entwicklung-und-devops-methoden-als-schl%C3%BCssel-f%C3%BCr-hohe-entwicklungsgeschwindigkeit)
  - [IT-Sicherheit](#it-sicherheit)
- [Technologien der dritten Plattform IT](#technologien-der-dritten-plattform-it)
- [Microservices und REST-Schnittstellen](#microservices-und-rest-schnittstellen)
  - [Microservices](#microservices)
  - [Dienste](#dienste)
  - [Technologie](#technologie)
  - [Pro/Contra Microservices](#procontra-microservices)
  - [Wer verwendet Microservices?](#wer-verwendet-microservices)
- [Service-Orientierte-Architekturen (SOA)](#service-orientierte-architekturen-soa)
  - [REST - Schnittstellen - Representational State Transfer](#rest---schnittstellen---representational-state-transfer)
    - [Eigenschaften von REST-Schnittstellen](#eigenschaften-von-rest-schnittstellen)
    - [Aufbau von REST-Anfragen](#aufbau-von-rest-anfragen)
    - [Übung](#%C3%BCbung)
- [Cloud Computing](#cloud-computing-1)
  - [Überblick](#%C3%BCberblick)
  - [Ursprung: Parallelisierung](#ursprung-parallelisierung)
    - [Cluster-Computing](#cluster-computing)
  - [GRID-Computing](#grid-computing)
  - [Warum (keine) Cloud](#warum-keine-cloud)
  - [Anwendungsmodelle](#anwendungsmodelle)
  - [IT-Aufbau](#it-aufbau)
  - [AWS-Einführung](#aws-einf%C3%BChrung)
    - [S3 - Simple Storage Service](#s3---simple-storage-service)
    - [AWSCLI einrichten](#awscli-einrichten)
    - [Kostenberechnung AWS](#kostenberechnung-aws)
    - [Virtuelle Rechner im AWS anlegen](#virtuelle-rechner-im-aws-anlegen)
- [Machine Learning - KI, neuronale Netzwerke, ...](#machine-learning---ki-neuronale-netzwerke-)
  - [Einsatzgebiete](#einsatzgebiete)
    - [Objekterkennung](#objekterkennung)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

<!--pagebreak-->

# Einleitung

- Ziel des Moduls: Verstehen, analysieren und beurteilen von IT-Trends und Buzzwords darum
- LV-Aufteilung: 45LV gesamt
	- 3. Sem: 30LV
	- 4. Sem: 15LV
- Am Ende des 3. Sem.: Teilprüfungsleistung in Form einer kleinen Abhandlung über die Trends (Details noch offen)

## IT-Trends nach IDC

- KI-unterstützte GUIs: es wird versucht, die Absicht des Nutzers vorherzusagen und entsprechend Programmfunktionen zu empfehlen
- KI-unterstützte Prozessautomatisierung: KI-basierte Empfehlungen / Vorschläge / Werbung, wie auf Amazon oder sozialen Medien zu sehen ist
- bis 2032 sollen 75% der IT-Ausgaben in der "dritten Plattform der IT" liegen

## Disruptionen

- Marktänderungen mit großen Auswirkungen, die existenz-gefährdend oder -ermöglichend sind
- **Bsp.:** Digitalkameras waren eine Disruption der Kamerafilmindustrie, aber auch für Speicherkartenhersteller

## Agile Methoden

- Agile Methoden sind: DevOps, Microservices & Cloud Computing, KI in allen Unternehmensbereichen / Digitale Transformation
- Ziel: Bewährtes auf eine neue Qualitätsstufe heben und durch Neues anreichern

## Cloud Computing

![Skizze einer Cloud](resources/cloud-skizze.svg)<!-- width=350px -->

**Vorteile:**

- zentrale Datenverarbeitung
- schnelles Deployment
- unabhängig von lokaler Infrastruktur (-> dynamisch skalierbar)
- hohe Verfügbarkeit
- "Pay as you go"

### Edge Computing

![Edge Computing](resources/edge-computing-skizze.svg)<!-- width=350px -->


- Anwendung: "am Rand des großen Netzwerks" --> für Geräte, die nicht in einem Netzwerk liegen (z.B. IoT-Sensoren)
- Auslöser für Entwicklung:
	- höhere Rechen- und Übertragungsgeschwindigkeit
	- Verlangen nach Flexibilität
	- Agilität der IT

## Künstliche Intelligenz

...bzw. KI / AI / Neuronale Netze / ML / Deep Learning

- erfordern möglichst große Datenbasis
	- Folge: Unternehmen sammeln zum Teil extreme Datenmengen (vom Nutzer), was dann Big Data heißt
- Nutzen in IT-Operations / -Tool / -Prozessen
	- z.B. Ausfallvorhersage
- *sollte* unterstützend wirken, nicht ersetzend
- trifft üblicherweise Vorhersagen
	- Bsp.: Analyse des Kaufverhaltens bei Kartenzahlungen und Verkauf von Informationen für Werbezwecke

## Agile Entwicklung und DevOps-Methoden als Schlüssel für hohe Entwicklungsgeschwindigkeit

- DevOps = Development + Operations
	- ist Philosophie und Sammlung von Methoden
	- Ziel: schnelleres Wirksamwerden von Änderungen
- Scrum-Strategie:
	- Ziel: schnelle Projektanpassungen und Flexibilität
- beliebtes Werkzeug: Continuous Integration / Continuous Delivery
- Durch Cloudentwicklung ist das Release-Modell weniger relevant (laufende Aktualisierung, immer verfügbar, daher egal für Nutzer)

## IT-Sicherheit

...bzw. Informationssicherheit

- ist "Chefsache"
	- Firma haftet
	- muss vom Management organisiert werden
- Umsetzungshelfer: IT-Grundschutz-Zertifizierung
- soll nicht nur technisch sein --> Mitarbeiter-Training
- Reaktion auf Vorfälle ist nicht ausreichend, man braucht auch Prävention und Vorschau auf Attacken (Profiling, Analysieren von Auswirkungen, Planung)
- Personalrollen:
	- Datenschutzbeauftragter: organisiert, informiert, ist Ansprechpartner
	- Informationssicherheitsbeauftragter
	- Mitarbeiter: muss geschult sein und disziplinvoll handeln, damit Schutz wirksam
- ist ein Dauerprojekt
- Schutzziele:
	- **Integrität von Daten** = Manipulationsschutz
		- z.B. durch Hashes
	- **Vertraulichkeit der Daten** = Zugriffsbeschränkungen
		- auf Netzwerkebene
		- auf physischer Ebene
		- auf logischer Ebene --> Verschlüsselung, Betriebssystemfunktionen
	- **Verfügbarkeit der Daten**
		- Redundanzen, Backups
	- Authentizität - Echtheit der Daten, keine Fälschung
	- Nichtabstreitbarkeit
- Authentizität + Nichtabstreitbarkeit = Verlässlichkeit der Daten

# Technologien der dritten Plattform IT

- Cloud Computing
- Mobile Computing (Mobilgeräte)
- Big Data & Analytics
- AI
- Augmented Reality / Virtual Reality
- IoT - Internet of Things
- Robotik
- 3D-Drucker
- Next-Gen Security (bessere Angriffserkennung und Abwehr durch KI)

Alle diese Punkte bedingen neue Expertisen bei den Mitarbeitern in den betreffenden Unternehmen:

- LOW-Code-Entwicklerplattformen werden notwendig, dabei sind vorgefertigte Programmodule vorhanden: diese Module (File-Open, Sortierungen, ...) müssen dann von den Entwicklern nur noch zusammengestellt werden
- Lambda-Funktion in AWS
- NO-Code

> Dev-Ops Methoden weiten sich auf das gesamte Unternehmen aus.

# Microservices und REST-Schnittstellen

## Microservices

Sind Architekturmuster in der IT, bei der die Anwendungssoftware aus vielen voneinander unabhängigen Prozessen zusammengesetzt wird.
Damit diese Prozesse miteinander kombiniert werden können, gibt es eine unabhängige Programmierschnittstelle.
Dabei wird von **Diensten** gesprochen, die entkoppelt sind. Der Aufbau ist modular.

Das Drei-Schichten-Modell spielen dabei eine Rolle:

1. GUI
2. Logik
3. Daten

Es wird auf die Microservices übertragen.

z.B.:

1. Microservice UI
2. Microservice Logik
3. Daten

Diese können wiederum aus Microservices zusammengesetzt sein, die untereinander vernetzt sind, siehe Schaubild.

![Microservices Schema](resources/microservice.png)<!-- width=350px -->

## Dienste

1. Sind klein, überschaubar und einfach ersetzbar
2. haben abgegrenzte Geschäftsfunktion
3. Schnittstellen\
	z.B. HTTP-Requests:
	- sind gut testbar
	- bei allen Programmsprachen unterstützt
	- etablierte Technologie
4. Sind nutzergetrieben (UX)
5. Sind voneinander unabhängig:
	- Lebenszyklus
	- Fehlerzustände werden nicht weitergeleitet
	- Programmiersprache
	- Datenbank
	- Technologie-Stack
6. dezentral organisiert und horizontal skalierbar
7. Logging + Monitoring sind notwendig
8. Gemeinsame Authentifizierung, Authorisierung und Kryptographie

## Technologie

- HTTP-Anfrage + REST-Schnittstelle

- Beispiel für horizontale Skalierung:

MS-A muss auf MS-B zugreifen, es sind mehrere Instanzen von MS-B vorhanden.
Dazu muss ein **Load Balancer** die Anfragen beispielsweise an diejenigen MS mit z.B. der geringsten Auslastung weiter weiterleiten.

## Pro/Contra Microservices

| Pro                                                        | Contra                                          |
|------------------------------------------------------------|-------------------------------------------------|
| kann billiger sein                                         | Netzwerk-Lastig (ggf. langsamer)                |
| Service schneller austauschbar                             | Erstinstallation und -konfiguration ist komplex |
| gute Skalierbarkeit                                        | Gefahr der Funktionsduplizierung                |
| bei Dienstausfall sind restliche Funktionen noch vorhanden | Logging ist komplex                             |
| Entwicklung kann unabhängig geschehen                      | Problem der "verteilten Uhren"                  |
| Wiederverwendung der Services in anderen Projekten         |                                                 |

## Wer verwendet Microservices?

- AWS  --> Simple Queue Service (SQS)
- Google
- Netflix
- Zalando

# Service-Orientierte-Architekturen (SOA)

![Service-Orientierte-Architektur](resources/SOA-Example.png)<!-- width=350px -->

## REST - Schnittstellen - Representational State Transfer

- Zur Kommunikation von verteilten Systemen
- ist weder ein Protokoll, noch ein Standard
- wurde parallel zu HTTP entwickelt
	- WWW liefert REST-konforme Infrastruktur

### Eigenschaften von REST-Schnittstellen

- Client-Server-Modell
	- UI ist von der Datenhaltung getrennt
- REST-Schnittstelle ist zustandslos
	- jede Anfrage muss alle relevanten Informationen enthalten
	- Server hat **keinen** gespeicherten Kontext
- Caching
	- gleiche Anfragen dürfen Cache verwenden
	- noncachable-Kennzeichnung möglich
- Schnittstellen einheitlich
	- vom Dienst entkoppelte Schnittstelle
	- höhere Visibilität von Interaktionen, aber schlechtere Effizienz
		- Binärdaten müssen HTTP-Konformes Format haben
- Layered System
	- schichtenbasiert -> der Einsatz eines Load-Balancers wird möglich
		- Anfragenlast kann verteilt werden
		- dadurch steigt aber auch die Latenz
- Code-On-Demand
	- nachladbare Applets/Skripte für Clients sind möglich

### Aufbau von REST-Anfragen

`http://adresse:port/` beliebige Daten in HTTP konformer Syntax

### Übung

**Aufgabe 1 (30 min):**

1. Entwickeln Sie ein Microservice-Beispiel und visualisieren Sie ihre Idee
2. Begründen Sie die Microservice-Architektur


**Aufgabe 2:**

1. Suchen und bedienen Sie eine REST-Schnittstelle (Senden und Empfangen von Daten)

Links zum Testen:

https://httpbin.org

https://api.predic8.de


Link zum Registrieren der Mailadresse für den Amazon-Cloud-Service für nächste Woche im Backstage
https://backstage.dhge.de/course/view.php?id=2718


# Cloud Computing

## Überblick

- Cloud als Buzzword
- Daten in der Cloud
- Rechnen in der Cloud
- Mythos: Ersetzt ein komplettes Rechenzentrum
- nahe Verwandte: Grid-Computing, Cluster-Computing

## Ursprung: Parallelisierung

1. Parallelisierung auf CPU-Ebene
2. Parallelisierung auf Rechner-Ebene
    - mehrere CPU pro Rechner
3. Parallelisierung auf Cluster-Ebene
    - n-Systeme, die sich wie Eines verhalten
4. Parallelisierung auf GRID-Ebene
    - mehrere zusammengefasste Cluster

![Cluster und Grid Computing](resources/Rechner_Cluster_Grid.png)<!-- width=350px -->

### Cluster-Computing

- n-Systeme verhalten sich wie ein virtueller Supercomputer
- Problem:
  - zu lösende Aufgabe muss sinnvoll aufteilbar sein
  - "Teile und Herrsche"-Problem -> Parallelverarbeitung muss möglich sein
- Wenn Parallelisierung möglich ist:
  - **Load-Balancer** übernimmt die Verteilung der Einzelaufgaben
  - Cluster befindet sich an einem lokalen Standort
  - Buzzwords:
    - HPC - High Performance Computing
    - HA - High Availability

## GRID-Computing

- zentraler GRID-Server, der die Verwaltung der heterogenen Rechner-/Clusterstruktur übernimmt
- GRID-Server übernimmt auch die dynamische Aufgabenverteilung
- dazu wird eine GRID-Computing Software notwendig
- Buzzword:
  - Job-Orientierung
    - Jobs werden der GRID-Software zur Verfügung gestellt, diese übernimmt die Abarbeitung
- Vorteil ist die gute Skalierbarkeit
- Ressourcen und Zugriff sind dezentral

![Grid Computing](resources/GRID_Computing.png)<!-- width=350px -->

## Warum (keine) Cloud

|   Pro                                                     |   Contra                                      |
|---------                                                  |-----------                                    |
|Hardware-Kosten sinken                                     |permanente Internetverbindung benötigt         |
|Gute Skalierbarkeit                                        |Vertraulichkeit muss sichergestellt sein       |
|Hohe Verfügbarkeit                                         |Daten müssen sicher sein (z.B. DSGVO)          |
|Verwaltungsaufwand sinkt für SW-Installation/Updates, Hardware Tausch, Backup                                              |Abhängigkeit von Dritten (Cloud-Anbieter)|
|Zahlung nach Nutzung                                       |Kosten können ggf. höher sein|
|24/7 Support                                               |Geschwindigkeit und Latenz|
|Eigene neue Netzwerk-Topologien konfigurierbar             ||
|Automatisierbarkeit                                        ||

**Over-Subscription**: Cloud-Anbieter überbuchen ihre technischen Möglichkeiten, da nie von allen Kunden gleichzeitig alles genutzt wird

<!-- Hier fehlen Mitschriften von der Vorlesung vom 13.11.2020 -->

| SaaS | SW-Sammlungen                        |
|------|--------------------------------------|
| PaaS | Laufzeitumgebung von Dienstanbietern |
| IaaS | virtualisierte Computer Hardware     |

## Anwendungsmodelle

- **Public Cloud** (öffentliche Cloud)
	- von beliebigen Personen/Unternehmen benutzbar
	- keinen internen Anwendungen
	- Probleme mit Datensicherheit beachten
- **Private Cloud**
	- Anbieter im eigenen Unternehmen (ggf. Outsourcing)
	- komplette Infrastruktur wird ausschließlich selbst genutzt
	- **virtuelle Private Cloud:** private Cloud auf anderen Servern (z.b. AWS Government Cloud)
- **Hybrid Cloud**
	- mehrere eigenständige Cloud-Infrastrukturen
	- Nutzung über standardisierte Schnittstelle
	- z.B. Private Cloud + Public Cloud für Failover-Fall

## IT-Aufbau

![Aufbau einer IT](resources/it-aufbau.png)<!-- width=350px -->

## AWS-Einführung

### S3 - Simple Storage Service

- Bucket (Ordner) in die Dateien können hochgeladen werden
- Diverse Konfigurationsmöglichkeiten: Öffentlicher Zugriff, Versionierung, ...

### AWSCLI einrichten
- Download von [https://docs.aws.amazon.com/de_de/cli/latest/userguide/install-cliv2.html](https://docs.aws.amazon.com/de_de/cli/latest/userguide/install-cliv2.html)
- Einrichten mit `aws configure`
- Daten aus Vocareum Workbench --> Account Details eintragen
	- Linux: `~/.aws/`
	- Windows: `%USERPROFILE%/.aws/`
- `.aws/credentials` sehen circa so aus:

```env
[default]
aws_access_key_id=
aws_secret_access_key=
aws_session_token=
```
- `.aws/config` sollte so aussehen:

```env
[default]
region = us-east-1
output = json
```
### Kostenberechnung AWS

Unter https://calculator.s3.amazonaws.com/index.html können die monatlichen Kosten für die AWS Services berechnet werden

### Virtuelle Rechner im AWS anlegen

1. Services > EC2 > Instanzen > Instanz starten
2. Dann gewünschtes OS auswählen
3. Dann Konfiguration auswählen (für Educate ist es t2 micro)
4. Click: Configure Instance Details
5. Details konfigurieren
6. Click: Add Storage
7. Speicher konfigurieren
8. Click: Add Tags
9. Tags zum Wiederauffinden der Maschine hinzufügen
10. Click: Configure Security Group
11. Port- und Diensteinstellungen konfigurieren  
12. Click: Review
13. Click: Launch
14. Generate SSH Keypair
15. SSH Key abspeichern
16. fertig.

**Per SSH verbinden**

Hier von Windows cmd aus:

```
cd PfadFürSSHKeypair

ssh -i Keypair.pem ubuntu@IPAdresseAusAWS
```

**Per RDP verbinden**

Bei **Windows VMs** findet sich der Admin Zugang unter:

Services > EC2 > Instanzen

Dann gewünschte Instanz anwählen und Click auf "Verbinden"

Dort dann die RDP-Datei herunterladen

Dann noch **Passwort abrufen** klicken um mit dem SSH-Keypair das Passwort zu entschlüsseln


# Machine Learning - KI, neuronale Netzwerke, ...

![Übersicht: Machine Learning](resources/Machine_Learning.png)<!-- width=350 -->

## Einsatzgebiete

### Objekterkennung

- bestimmte Objekte auf Bildern oder in Videos erkennen
- Beispiele:
	- unsichere Inhalte erkennen
		- z.B. Pornographie, Gewalt, ...
	- Gesichtserkennung
		- Gesichtsmerkmale erkennen und zu Personen zuordnen
		- Lächeln und andere Emotionen erkennen
		- Alter und Geschlecht erkennen
	- Texterkennung
		- Bild -> Text
		- Audio -> Text
		- Formularanalyse
