Systemanalyse
=============

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Inhaltsverzeichnis**

- [Einführung / Überblick](#einf%C3%BChrung--%C3%BCberblick)
  - [User Story Format](#user-story-format)
  - [Was gehört alles zur Systemanalyse?](#was-geh%C3%B6rt-alles-zur-systemanalyse)
- [Regeln für Software-Entwicklung](#regeln-f%C3%BCr-software-entwicklung)
  - [(1) Klartext](#1-klartext)
    - [Wasserfallmodell](#wasserfallmodell)
    - [Agil](#agil)
  - [(2) Gründliche Vertragsgestaltung](#2-gr%C3%BCndliche-vertragsgestaltung)
    - [Wasserfallmodell](#wasserfallmodell-1)
    - [Agil](#agil-1)
  - [(3) Wandelnde Anforderungen: Wie gehe ich damit um?](#3-wandelnde-anforderungen-wie-gehe-ich-damit-um)
    - [Change Request Prozess:](#change-request-prozess)
- [Systementwicklung im Software-Engineering](#systementwicklung-im-software-engineering)
  - [Vorgehensmodelle](#vorgehensmodelle)
    - [Phasenmodell](#phasenmodell)
    - [Iteriertes Phasenmodell](#iteriertes-phasenmodell)
    - [Evolutionäre SW-Entwicklung](#evolution%C3%A4re-sw-entwicklung)
    - [Spiralen Modell](#spiralen-modell)
    - [V-Modell](#v-modell)
    - [Eine Ausprägung des V-Modells: "V-Modell XT"](#eine-auspr%C3%A4gung-des-v-modells-v-modell-xt)
    - [Extreme Programming (XP)](#extreme-programming-xp)
- [SCRUM](#scrum)
  - [Empirische Prozess Kontrolle](#empirische-prozess-kontrolle)
  - [SCRUM-Prozess](#scrum-prozess)
  - [User-Story](#user-story)
  - [Rollen im SCRUM-Prozess](#rollen-im-scrum-prozess)
    - [Product Owner](#product-owner)
    - [Entwickler Team](#entwickler-team)
    - [SCRUM-Master](#scrum-master)
    - [Vorgehen in SCRUM](#vorgehen-in-scrum)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Einführung / Überblick

- Wir bekommen ein Problem vom Nutzer → Lösung durch Programmierung
  - (1) Woher kommt die Problembeschreibung?
  - (2) Beschreibt sie wirklich das Problem des Nutzers?
  - (3) Was will der Nutzer denn **wirklich** damit machen?

## User Story Format

> Als ...
>
> möchte ich ...
>
> um ... zu

- selber so formulieren und einfordern
- bestenfalls bekommt man die Problembeschreibung direkt so
- Struktur des Programms ist dem Nutzer quasi egal
- der Nutzer erwartet eine Korrektheit der Lösung => TESTEN
- neue Anforderungen → und dann?
- **mehrere Entwickler:** wie wird die Aufgabe vernünftig geteilt?

## Was gehört alles zur Systemanalyse?

- Anforderungen / Anforderungsanalyse
- Strukturierung der Entwicklung
- Entwurf + Entwicklung
- Betrieb der Lösung
- Wartung der Lösung
- Qualitätssicherung (Testen)

# Regeln für Software-Entwicklung

## (1) Klartext

### Wasserfallmodell

- lineares Modell
- Phasen
- Lastenheft (Was möchte der Kunde bekommen?)
- Pflichtenheft (Was hat der Entwickler verstanden, was macht er?)

### Agil

- iteratives Modell
- feste Struktur & klare Regeln → jedoch adaptierbar
- Backlog → Aufgabensammlung
- Refinement Prozess! → **Kommunikation ist wichtig**

## (2) Gründliche Vertragsgestaltung

### Wasserfallmodell

- 1/2 Jahr rechtsichere Fomulierung des Lastenhefts
- gleiche Begriffe zu Beginn des Lastenhefts abklären
- 3\. Person ließt, versteht und korrigiert → unterschreibt

### Agil

- Backlog + Refinement

## (3) Wandelnde Anforderungen: Wie gehe ich damit um?

Zum Beispiel: keine Zusatzleistungen bzw. E-Mail/mündlich
=> am Ende: was zählt?

### Change Request Prozess:

Request → Impact, Analysis → Approve / Deny → Implementation → Business

**14 Tage Cycle:** Planning, Review, Retro

**MMM:** Mensch, Maschine, Methode  
Zuerst schauen: "Habe ich die richtigen Mitarbeiter?"  
Danach schauen: "Habe ich die richtige Hardware/Software?"  
Zuletzt die Methode hinterfragen
# Systementwicklung im Software-Engineering

> orientiert sich an der Auto-Produktion

- Autoproduktion:

  - kalkulierbare Kosten + Risiken (Planung und Produktion sind getrennt)
  - vorhersagbares Ergebnis (Industrialisierung)
  - Qualität (ständiges Messen)

- Software Produktion

  - Kosten sind **nicht** zuverlässig vorhersagbar
  - viele Fehlschläge in der Branche
  - schlecht quantifizierbar

-> **Systematisierung** & **Krisenerkenntnisse** werden notwendig

**Grundlagen:**

- Softwaretechnik: praktisches Erstellen on Software
- Informatik: Methoden & Theorie

-> führen zur:

**Softwareentwicklung**

- Phasen
  - zeitlich befristete Abschnitte
- Vorgehensmodelle
  - Leitfaden bzw. Standards
  - definieren Phasen

## Vorgehensmodelle

### Phasenmodell

**5 Phasen** -> Stufenmodell

```
Analyse
└─ Design
  └─ Programmierung
    └─ Integration / Test
      └─ Einsatz / Wartung
```

**Analyse-Phase**

- Funktionsumfang
- User Interface
- Leistungsverhalten
- Termine

Lastenhaft (vom Auftraggeber) als Grundlage -> Pflichtenheft wird (vom Auftragnehmer) erstellt

> Mit der Erstellung des Pflichtenhefts beginnt die **Design-Phase**

- die innere Struktur der Software wird festgelegt -> Komponentenzerlegung benennen (Teile und Herrsche Prinzip)

> Achtung: Fehlerfortpflanzung!

**Programmierung**

- Komponenten werden anhand des Entwurfs implementiert
- Programmieren im Kleinen (alternative Benennungen / Kodierungen)

-> Module (einzeln getestete Quelltexte)
  - nicht selbständig lauffähig

> auch hier kann wieder eine Fehlerfortpflanzung stattfinden!

**Integration / Test**

- nacheinander Einzelkomponenten hinzugefügt
- weitere Tests (Integrations-Tests) (Abnahme-Tests)
- Installation, dann ist das Gesamtsystem vorhanden und ein sog. Systemtest kann durchgeführt werden
  - Systemtest: Konsistenz bezüglich der Produkt-Definition wird überprüft

**Einsatz / Wartung**

- dauert bis zum Abschalten der Software
- Fehlerkorrektur
- Anpassungen an andere System-Umgebungen
- Änderungen und Erweiterungen der Funktionalitäten

MVPs fehlen

> Einzelphasen sind für sich betrachtet nichts schlechtes!
> aber Rückkopplungen?

**Vor-und Nachteile des Phasen-/Wasserfallmodells**

| Vorteile                              | Nachteile                                           |
| ------------------------------------- | --------------------------------------------------- |
| Gesamtkosten + Aufwand zu Beginn klar | wenig Flexibilität bezüglich Änderungsmöglichkeiten |
| Phasenpipelining möglich              | keine Rückkopplungen                                |
| Einzelabschnitte                      | Testen nur am Ende                                  |
| Einzelabschnitte sind wenig komplex   | für komplexe Aufgaben / große Teams ungeeignet      |
|                                       | kein experimentelles Vorgehen                       |
|                                       | Kunde ist nicht wirklich involviert                 |
|                                       | Fail Early wird nicht unterstützt                   |

> Viele Vorteile können auch Nachteile sein (und vice-versa)
> je nachdem welche Ziele verfolgt werden und in welchem Stil man arbeiten möchte

### Iteriertes Phasenmodell

```
Analyse
└─ Design
  └─ Programmierung
    └─ Integration / Test
      └─ Einsatz / Wartung
```

Hier wird immer wieder in eine Phase "zurück gesprungen", falls etwas nicht passt.

> -> Protop zur Akzeptanz-Analyse ist möglich!

**PDCA-Prinzip:** Planning -> Doing -> Checking -> Acting (und wieder von vorn)

> Das PDCA-Prinzip wird später genauer behandelt

**Unterschied zwischen Prototyp und Pretotype**

**Prototyp:**
- erstes Vorbild
- praktische Erfahrungen
- klären von Anforderungen
- zeigt ausgewählte Eigenschaften
- darf bzw. **muss** quick & dirty sein

**Gefahr:**
- wird nicht wieder weggeworfen
- wird als Doku-Ersatz missbraucht
- Aufwand ist relativ hoch

-> **Pretotyp:** "Fake it till you make it"
> Durch einen Pretotyp wird die Fail-Early Idee unterstützt

### Evolutionäre SW-Entwicklung

**evolutionär:**

- Bewährtes weiterentwickeln
- unnötige Features abschalten

-> Weiterentwicklung des Prototypen

-> Problem:
- ständige Änderungen im Quellcode
- evolutionäre Dokumentation

| Vorteile                               | Nachteile              |
| -------------------------------------- | ---------------------- |
| entspricht der natürlichen Entwicklung | fehlender Prozess      |
| kann Resourcen-sparend sein            | unendliche Entwicklung |
|                                        | Anarchie               |

> Eine unendliche Entwicklung kann natürlich auch von Vorteil sein (bspw. bei SAAS)

### Spiralen Modell

| (1) | **ZIELE**, Alternativen, Rahmenbedingungen | (2) | Evaluierung der Alternativen, **RISIKEN** abschätzen, reduzieren |
|-----|--------------------------------------------|-----|------------------------------------------------------------------|
| (4) | **PLAN** für nächsten Zyklus               | (3) | **REALISIERUNG** + Überprüfung                                   |

**USP:** Risikobetrachtung

- Weiterentwicklung des Wasserfallmodells
- zyklische Wiederholung der Phasen -> Annäherung an Gesamt-Ziel
- Ziele ändern sich auch während des Projektfortschritts -> Spiralen-Modell versucht darauf zu reagieren

**Genereller Ablauf:**

- **Zyklus 1:** (1) Planung -> (2) Risiko, Prototyp 1 -> (3) Anforderungen -> (4) Entwicklungsplan
- **Zyklus 2:** (1) Ziele, Alternativen, Rahmenbedingungen -> (2) Risiko, Prototyp 2 -> (3) Grob-Entwurf -> (4) Testplan
- **Zyklus 3:** (1) Ziele, Alternativen, Rahmenbedingungen -> (2) Risiko, Prototyp 3 (betriebsfähig) -> (3) Fein-Entwurf, Code, Integrieren, Testen -> ...

| Vorteile                             | Nachteile                                |
| ------------------------------------ | ---------------------------------------- |
| frühe Korrektur-Möglichkeit          | Weglassen von Elementen nicht vorgesehen |
| Risiko wird (zwangsweise) betrachtet | spätes echtes Produkt                    |
| frühe Fehlersichtbarkeit ist Möglich | unflexibel                               |
| klarer Ablauf                        | zeitlich anspruchsvoll                   |

### V-Modell

> bisher Vorgehensmodelle zur Verbesserung von Zeit, Kosten, Leistung
>
> Flächeninhalt von Dreieck (Zeit, Kosten, Leistung) ist konstant
>
> -> Zeit + Kosten + Leistung können nicht gleichzeitig verbessert werden

Analyse -> High-Level-Design -> Low-Level-Design -> Implementierung -> Unit Tests -> Integrations-Tests -> Systemtests -> Akzeptanz-Tests
<!-- Hier wäre eine visuelle Darstellung ganz gut -->

| Vorteile                                              | Nachteile                                                                                                         |
| ----------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------- |
| klarer Ablauf (nächster Schritt bei Fehler wird klar) | Fehler in der Anaylse-Phase erst sehr spät sichtbar (früher mehr Kommunikation mit dem Kunden und MVP als Lösung) |
| klare Test-Struktur vorgegeben                        |                                                                                                                   |
| Iterationen bis alle Tests der Phase OK sind          |                                                                                                                   |

### Eine Ausprägung des V-Modells: "V-Modell XT"

- Ursprung: militärscher Bereich
- **Ziele:**
  - (1) Kosten transparent machen -> Kosten-Limitierung wird möglich
  - (2) Mindeststandard an Qualitäts-Maßnahmen zu garantieren
  - (3) Vergleichbarkeit von Angeboten Dritter
- **V Modell-93:** Richtschnur für IT-Vorhaben in BRD
- **V Modell-93:** Objekt-Orientierung
- **V Modell XT:** "Extreme Tailoring"
  - an Bedürfnisse anpassbar
  - Auftraggeber mit eingebunden
  - stärkere Modularisierung
  - mehr in Richtung AGIL

2015: 900 A4 Seiten PDF-Doku => 500 Seiten

**3 Säulen:** Meta-Modell, freie Inhalte, Werkzeuge

**Meta-Modell**
- Rollen
- Produkte
- Beziehungen (Aktivitäten)

feste Inhalte + optionale Bestandteile

Produkt-orientierte Arbeitsweise + Tailoring

Auftrag-Geber / Auftrag-Nehmer im Sprachgebrauch + Schnittstellen (Synchronisations-Punkte)

**Werkzeuge**
- V-Modell XT-Editor (für Anpassungen)
- V-Modell XT-Projekt-Assistenten (Tailoring)
- XML-Technologie baiserend

|                     |                                                                                |
| ------------------- | ------------------------------------------------------------------------------ |
| produktorierentiert | nicht *wie*, sondern *was* "hergestellt" wird                                  |
| Produkte            | Software-Code, Modelle, Dokumentationen, Zwischenergebnisse (auch als SW-Code) |

für alle Produkte gibt es sog. Entscheidungspunkte (Milestones)
- inklusive Aussagen zur Qualitätskontrolle
- DoD

> DoR: "Definition of Ready"  
> DoD: "Definition of Done"

Tailoring -> Projekt für Softwaresysteme oder Projekt für Beschaffung  
(unterscheiden sich: mithilfe des Projekt-Assistenten können die relevanten Teile bestimmt werden)

-> 4 Typen von Projekten werden unterschieden

Auftraggeber Projekt (AG): Vergabe von Entwicklungsaufträgen  
Auftragnehmer Projekt (AW): Entwicklung  
AG/AW: ohne Vertragsverhältnis (z.B. Fach + Developer Abteilung sitzen zusammen)  
Organisationsspezifische Projekt

es gibt Produkte außerhalb des eigenen Projekts (sog. externe Produkte)  
-> Fertigstellung und Übergabe legen Kommunikationspfade fest

**Kommunikationspfade:**
Wer, Was, Wann

| Vorteile                                              | Nachteile                                                    |
| ----------------------------------------------------- | ------------------------------------------------------------ |
| gute Strukturvorgabe                                  | sehr komplex                                                 |
| Kosten sind transparent falls keine Änderungen kommen | Reaktion auf Änderungen nicht vorgesehen                     |
| sehr generisch gehalten                               | sehr generisch gehalten                                      |
| viele Anpassungsmöglichkeiten (aber ad libitum) ->    | es gibt keinen Prozess, der nach Verbesserungen sucht        |
|                                                       | vage Anforderungen führen nicht zu einem V-Modell XT Projekt |

### Extreme Programming (XP)
- leichtgewichtiges Vorgehensmodell
- für kleine / mittlere Teams geeignet
- bei vagen Anforderungen gut geeignet
- schnelle Änderungen der Anforderungen

> XP setzt bewährte Techniken im extremen Maße ein
1. Paar-Programmierung  
   kontinuirliche Review
2. Testen  
   kontinuirliches Testen
3. Refactoring  
   kontinuirliches Design / Redesign
4. Feedback an Kunden  
   kurze Release Zyklen

- Story (einfache Lösung)-> neue Aufgabe, ist das Problem zu Komplex müssen die Stories neu definiert werden
- Paar Bildung für Aufgaben -> Testentwurf -> Test nicht erfolgreich, wieder zurück zu Programmieren in Paaren
- Ist der Code zu kompliziert -> Umstrukturierung -> resultiert in vereinfachtem Code
- Es wird überprüft ob CI (Continuous Integration) Tests erfolgreich sind (wenn nicht -> zurück zum Pair Programming)
- Tests erfolgreich -> Abnahme Tests, wenn erfolgreich -> Abnahme
- Wenn Abnahme Tests nicht erfolgreich sind -> zurück zur neuen Aufgabe
- bei Problemen können auch Paare neu eingeteilt werden

<!-- Hier würde sich eine Grafik anbieten -->

> - durch Stories und Tests getrieben  
> - Programmierung steht im Mittelpunkt  
> - viele Release Zyklen

**Zu 1. (Paar-Programmierung)**  
__Beispiel 1999 Utah:__  
13 Einzelprogrammierer  
14 Paar-Programmierer  
4 Aufgaben in 6 Wochen  
am Ende: Test der Programme  
-> Paare hatten bessere Qualität und waren schneller fertig.  
Paare hatten mehr Vertrauen in ihre Programme, hatten mehr Spaß und waren effizienter

> ABER: Die Chemie in den Paaren muss stimmen!

Weitere Beispiele: Windows 2000, Crysler Payroll-System

**Zu 2. (Testen)**
- Testfälle erstellen **bevor** Komponente implementiert wird
- alle Tests laufen automatisch ab
- Fehlerfall => zuerst neuen Test entwerfen, dann Fehler beheben
- Testbarkeit => Entkopplung der Subsysteme

**Zu 3. (Refactoring)**
- "Alte Zöpfe ruhig abschneiden!"
- XP = so einfach wie möglich
- Design ist richtig <-> alle Tests sind OK, keine Redundanzen, Anzahl an Klassen / Methoden ist minimal
- systematisches Redesign
  1. Extract Methods: Code in Methoden auslagern
  2. Move Methods: Methoden wandern von Klasse zu Klasse
  3. Magic-Numbers (verhindern): symbolische Konstanten   
     Beispiel: `if (filesOpen > MAXFILES)` anstatt `if (filesOpen > 3)`
  4. Conditionals in Polymorphismus überführen

**Zu 4. (Feedback an Kunden / kurze Release Zyklen)**
- ganz nah am Kunden zu sein ist wichtig

**Vor-und Nachteile**

Allgemeine Kriterien:
- Kosten / Kosten
- Qualität der Ergebnisse
- Flexibilität
- gegenseitiges Lernen
- Overhead (Betreuung, Komplexität)
- Tests
- Kommunikationsprobleme sichtbar

| Vorteile                                                      | Nachteile                           |
| ------------------------------------------------------------- | ----------------------------------- |
| geringere Anschaffungskosten                                  | Zeit-aufwändig                      |
| Code Qualität                                                 | Personal-aufwändig                  |
| Flexibilität (bezüglich neuer Nutzerwünsche, umstrukturieren) | Update Häufigkeit / Kundenakzeptanz |
| Teams <--                                                     | Corona                              |

# SCRUM

## Empirische Prozess Kontrolle

**PDCA Prinzip:**  
Plan -> Do -> Check -> Act -> (zurück zu Plan)

> - kurze Planungszeit, schnell in das Doing übergehen und nach kurzer Zeit prüfen  
> - soll zu einer besseren Lösung führen

- transparenter Prozess
- Doing + Überprüfung + Anpassung
- häufige Wiederholung

## SCRUM-Prozess
- (1) Produkt-Vision, gemeinsame Idee muss zunächst existieren
- -> ein Workshop führt zu (2) einem Produkt-Backlog, gefüllt mit Epics
> ein Epic ist ein höheres Anforderungsniveau -> keine Details -> nicht sofort umsetzbar  
> Der Backlog enthält <= 150 Epics (wenn mehr -> zwei Produkte (Empfehlung))  
> in der Regel besteht ein Epic aus 1-8 User-Stories
- Der Product Owner ist für die "Vision" und die Reihenfolge der Epics verantwortlich
- Jeder soll/darf Epics in das Backlog "füttern" dürfen

## User-Story
> Als ... möchte ich ... um ...

- Erklärung eines Features aus Sicht einer Person, die dieses Feature verwenden will
- Wert für den Kunden
- Ziel
- Jeder User-Story werden eine Priorität und sog. Story-Points zugeordnet
> Story-Points sind eine Aufwandsschätzung, die jedoch **nicht** die geschätzen Arbeitsstunden darstellen
- desweiteren enthält die User-Story eine Risikoabschätzung
- hinterher wird an der User-Story der tatsächliche Aufwand dokumentiert

Tests auf der "Rückseite":  
Angenommen ... <Vork.> wenn ... <Aktion> dann ... <Ergebnis>  
> Realisierbar mit: JIRA, ..., Empfehlung für den Anfang: taktile Variante (Papier)

## Rollen im SCRUM-Prozess
### Product Owner
- muss eine "Brücke" zwischen Business und Development herstellen
- muss ROI (Return of Investment) gewährleisten
- ist die Schnittstelle zum Kunden -> muss die Kundenbedürfnisse verstehen und einordnen
- **Value:** muss Kriterien für den Value definieren und ihn erhöhen -> Was? Warum?
- ist für Sprint Reviews verantwortlich
- muss Backlog Prioritäten setzen

**Aus praktischer Erfahrung ist der PO:**
- ein Full-Time Job  
- eine Authoritätsperson  
- genau eine Person

### Entwickler Team
- besteht idealerweise aus 7+-2 Mitarbeiter
- selbstorganisierend
- Mitarbeiter ist typischerweise "I-shaped" -> hat auf einem Gebiet extrem tiefes Wissen  
  das Ziel ist jedoch ein "T-shaped" Mitarbeiter -> hat ein breites Wissen, mit einem Spezialbereich
- sind Macher
- sind nach außen geschützt

### SCRUM-Master
- Kümmerer (kümmert sich um Probleme seiner Mitarbeiter)
- Diener + Führer in einer Person
- Prozessbeobachter
- dokumentiert u.A. den Fortschritt der Entwicklung
- hilft dem Team, Probleme zu lösen
- idealerweise ist der SCRUM-Master ein fachfremder Mitarbeiter

### Vorgehen in SCRUM
1. Vision -> Produktbacklog  
   im Produktbacklog ist die oberste Aufgabe die wichtigste

2. Sprint-Planning  
   Das **Team** erstellt ein Sprint-Backlog aus dem Produkt-Backlog
   - ein Sprint-Ziel muss definiert werden

3. Bearbeitung des Sprints (meist 14 Tage)
   - Daily Meeting (jeder im Team erzählt ganz kurz, woran er gerade arbeitet)
   - am Ende des Sprints: Sprint Review (bezieht sich konkret auf den Inhalt des Sprints)
   - Retrospektive (bezieht sich auf den Prozess des Sprints, realisierbar durch KSSP)
   - zurück zu 2.

> Die 4 festen Events sind nicht abwählbar (vs. Aussage: beim SCRUM kann vieles an Bedürfnisse vom Team angepasst werden)

**Daily SCRUM Event**
- Koordination des Teams bezüglich des Sprint-Ziels
- Entwickler Team
- am Kanboard
- geführt wird es vom SCRUM-Master (!)
- Timebox! 15 Minuten und nicht länger!
- 3 Fragen:
  - Was habe ich getan?
  - Was werde ich tun?
  - Was hat mich behindert
- Product Owner darf als Gast dabei sein

> Im Burn-Down-Chart ist die Reduzierung der Tasks anfangs oft sehr langsam, da noch kein/wenig Task-Grooming/Task-Refinement betrieben wurde.