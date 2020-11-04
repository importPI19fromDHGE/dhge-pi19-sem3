Systemanalyse
=============

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Inhaltsverzeichnis**

- [Systemanalyse](#systemanalyse)
- [Einführung / Überblick](#einführung--überblick)
  - [User Story Format](#user-story-format)
  - [Was gehört alles zur Systemanalyse?](#was-gehört-alles-zur-systemanalyse)
- [Regeln für Software-Entwicklung](#regeln-für-software-entwicklung)
  - [(1) Klartext](#1-klartext)
    - [Wasserfallmodell](#wasserfallmodell)
    - [Agil](#agil)
  - [(2) Gründliche Vertragsgestaltung](#2-gründliche-vertragsgestaltung)
    - [Wasserfallmodell](#wasserfallmodell-1)
    - [Agil](#agil-1)
  - [(3) Wandelnde Anforderungen: Wie gehe ich damit um?](#3-wandelnde-anforderungen-wie-gehe-ich-damit-um)
    - [Change Request Prozess:](#change-request-prozess)
- [Systementwicklung im Software-Engineering](#systementwicklung-im-software-engineering)
  - [Vorgehensmodelle](#vorgehensmodelle)
    - [Phasenmodell](#phasenmodell)
    - [Iteriertes Phasenmodell](#iteriertes-phasenmodell)
    - [Evolutionäre SW-Entwicklung](#evolutionäre-sw-entwicklung)
    - [Spiralen Modell](#spiralen-modell)
    - [V Modell](#v-modell)
    - [Eine Ausprägung des V-Modells: "V-Modell XT"](#eine-ausprägung-des-v-modells-v-modell-xt)

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

- Analyse
  - Design
    - Programmierung
      - Integration / Test
        - Einsatz / Wartung

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

- Analyse
  - Design
    - Programmierung
      - Integration / Tests
        - Einsatz / Wartung

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
| **(1) ZIELE, Alternativen, Rahmenbedingungen** | **(2) Evaluierung der Alternativen, RISIKEN abschätzen, reduzieren** |
| ---------------------------------------------- | -------------------------------------------------------------------- |
| **(4) PLAN für nächsten Zyklus**               | **(3) REALISIERUNG + Überprüfung**                                   |

**USP:** Risikobetrachtung

(Weiterentwicklung des Wasserfallmodells)

- zyklische Wiederholung der Phasen -> Annäherung an Gesamt-Ziel

Ziele ändern sich auch während des Projektfortschritts -> Spiralen-Modell versucht darauf zu reagieren

**Genereller Ablauf:**

**Zyklus 1:**

(1) Planung -> (2) Risiko, Prototyp 1 -> (3) Anforderungen -> (4) Entwicklungsplan


**Zyklus 2:**

(1) Ziele, Alternativen, Rahmenbedingungen -> (2) Risiko, Prototyp 2 -> (3) Grob-Entwurf -> (4) Testplan

**Zyklus 3:**

(1) Ziele, Alternativen, Rahmenbedingen -> (2) Risiko, Prototyp 3 (betriebsfähig) -> (3) Fein-Entwurf, Code, Integrieren, Testen -> (4) 

| Vorteile                             | Nachteile                                |
| ------------------------------------ | ---------------------------------------- |
| frühe Korrektur-Möglichkeit          | Weglassen von Elementen nicht vorgesehen |
| Risiko wird (zwangsweise) betrachtet | spätes echtes Produkt                    |
| frühe Fehlersichtbarkeit ist Möglich | unflexibel                               |
| klarer Ablauf                        | zeitlich anspruchsvoll                   |

### V Modell

> bisher Vorgehensmodelle zur Verbesserung von Zeit, Kosten, Leistung

> Flächeninhalt von Dreieck (Zeit, Kosten, Leistung) ist konstant

> -> Zeit + Kosten + Leistung können nicht gleichzeitig verbessert werden

Analyse -> High-Level-Design -> Low-Level-Design -> Implementierung -> Unit Tests -> Integrations-Tests -> Systemtests -> Akzeptanz-Tests
<!-- Hier wäre eine visuelle Darstellung ganz gut -->

| Vorteile                                              | Nachteile                                                                                                         |
| ----------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------- |
| klarer Ablauf (nächster Schritt bei Fehler wird klar) | Fehler in der Anaylse-Phase erst sehr spät sichtbar (früher mehr Kommunikation mit dem Kunden und MVP als Lösung) |
| klare Test-Struktur vorgegeben                        |                                                                                                                   |
| Iterationen bis alle Tests der Phase OK sind          |                                                                                                                   |

### Eine Ausprägung des V-Modells: "V-Modell XT"

- kommt aus dem militärschen Bereich 

- **Ziel:**

  - (1)  Kosten transparent machen -> Kosten-Limitierung wird möglich
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

**3 Säulen:** Meta-modell, freie Inhalte, Werkzeuge

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