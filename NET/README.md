

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Inhaltsverzeichnis**

- [Rechnernetzkonzepte und -architekturen](#rechnernetzkonzepte-und--architekturen)
- [1. Einleitung / Übersicht](#1-einleitung--%C3%BCbersicht)
  - [1.1 Veranstaltungsziele](#11-veranstaltungsziele)
  - [1.2 Inhaltlicher Teil](#12-inhaltlicher-teil)
    - [1.2.1 Kommunikationsszenario](#121-kommunikationsszenario)
    - [1.2.2 Standardisierung](#122-standardisierung)
    - [Internet Engineering Taskforce](#internet-engineering-taskforce)
      - [Arbeitsgruppen  / IETF-Areas](#arbeitsgruppen---ietf-areas)
    - [1.2.3 Begrifflichkeiten](#123-begrifflichkeiten)
    - [1.2.4 ISO / OSI Referenzmodell  <!-- hochgradig Prüfungsrelevant-->](#124-iso--osi-referenzmodell-----hochgradig-pr%C3%BCfungsrelevant--)
      - [7 Anwendungsschicht](#7-anwendungsschicht)
      - [6 Darstellungsschicht](#6-darstellungsschicht)
      - [5 Sitzungsschicht](#5-sitzungsschicht)
      - [4 Transportschicht](#4-transportschicht)
      - [3 Vermittlungsschicht](#3-vermittlungsschicht)
      - [2 Sicherungsschicht](#2-sicherungsschicht)
      - [1 Bitübertragungsschicht](#1-bit%C3%BCbertragungsschicht)
    - [1.2.5 TCP / IP-Modell](#125-tcp--ip-modell)
    - [1.2.6 Protokoll-Header](#126-protokoll-header)
    - [1.2.7. Kopplungselemente](#127-kopplungselemente)
      - [**Switches**](#switches)
      - [**Router**](#router)
      - [**Weitere Kopplungselemente**](#weitere-kopplungselemente)
    - [1.2.8 Topologien](#128-topologien)
    - [Tooling - Wireshark](#tooling---wireshark)
- [2. Netzzugangsschicht](#2-netzzugangsschicht)
  - [2.1 Übersicht zu Ethernet](#21-%C3%BCbersicht-zu-ethernet)
  - [2.2 Aufbau eines Ethernet Frames](#22-aufbau-eines-ethernet-frames)
  - [2.3 Namen von Netzwerkschnittstellen unter Linux](#23-namen-von-netzwerkschnittstellen-unter-linux)
  - [2.4 Switches](#24-switches)
    - [2.4.1 Architekturtypen](#241-architekturtypen)
    - [2.4.2 Kenngrößen](#242-kenngr%C3%B6%C3%9Fen)
    - [2.4.3 Spanning-Tree-Protocol <!--wahrscheinliche Prüfungsaufgabe-->](#243-spanning-tree-protocol---wahrscheinliche-pr%C3%BCfungsaufgabe--)
      - [2.4.3.1 STP - Port Fast/Fast Link](#2431-stp---port-fastfast-link)
      - [2.4.3.2 Rapid Spanning Tree Protocol](#2432-rapid-spanning-tree-protocol)
    - [2.4.4 Virtuelles LAN](#244-virtuelles-lan)
      - [2.4.4.1 Tag-basierte VLANs](#2441-tag-basierte-vlans)
      - [2.4.4.2 Inter-VLAN-Routing](#2442-inter-vlan-routing)
      - [2.4.4.3 STP und VLAN](#2443-stp-und-vlan)
    - [2.4.5 Transparent Interconnection of lots of links (TRILL)](#245-transparent-interconnection-of-lots-of-links-trill)
    - [2.4.6 Stacking](#246-stacking)
- [3. Vermittlungsschicht: Internet Protocol](#3-vermittlungsschicht-internet-protocol)
  - [3.1 IPv4](#31-ipv4)
    - [3.1.1 IPv4-Header](#311-ipv4-header)
    - [3.1.2 Fragmentierung](#312-fragmentierung)
    - [3.1.3 IPv4-Adressierung](#313-ipv4-adressierung)
  - [3.2 Address Resolution Protocol (ARP)](#32-address-resolution-protocol-arp)
    - [3.2.1 Einordnung](#321-einordnung)
    - [3.2.2 Protokolldetails](#322-protokolldetails)
  - [3.3 ICMP](#33-icmp)
  - [3.4 Praxisübung](#34-praxis%C3%BCbung)
  - [3.5 Nachteile IPv4](#35-nachteile-ipv4)
  - [3.6 IPv6](#36-ipv6)
    - [3.6.1 Header](#361-header)
    - [3.6.2 Extension-Header](#362-extension-header)
    - [3.6.3 IPv6-Fragmentierung](#363-ipv6-fragmentierung)
    - [3.6.4 Ipv6-Adressen - Notation](#364-ipv6-adressen---notation)
    - [3.6.5 Adresstypen (Folie 3/15)](#365-adresstypen-folie-315)
    - [3.5.6 Generelle Adresstruktur (Folie 3/16)](#356-generelle-adresstruktur-folie-316)
    - [3.5.7 Erzeugung einer link-local Adresse (Folie 3/17)](#357-erzeugung-einer-link-local-adresse-folie-317)
    - [3.5.8 IPv6-Multicasts (Folie 3/18)](#358-ipv6-multicasts-folie-318)
    - [3.5.9 Stateless Adress Autoconfiguration SLAAC (Folien 3/22,23)](#359-stateless-adress-autoconfiguration-slaac-folien-32223)
  - [3.6 Migration IPv4 -> IPv6 (Folie 3/24)](#36-migration-ipv4---ipv6-folie-324)
    - [3.6.1 Dual-Stack Lite (DS-Lite) (Folie 3/25)](#361-dual-stack-lite-ds-lite-folie-325)
  - [3.7 Exkurs: Raw Sockets](#37-exkurs-raw-sockets)
  - [3.8 Exkurs: IPv6 im Linux-Kernel 5.9 (Folien 3/27,28)](#38-exkurs-ipv6-im-linux-kernel-59-folien-32728)
  - [Praxisbeispiel radvd - SLAAC in Namespaces:](#praxisbeispiel-radvd---slaac-in-namespaces)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Rechnernetzkonzepte und -architekturen

*16.11.2020*

# 1. Einleitung / Übersicht
## 1.1 Veranstaltungsziele
Wissensvermittlung zu:
- Übersichtswissen über Rechnernetze
- Komponenten und Protokolle im Internet
- Planung von Netzwerken
- Konfiguration von Netzwerken

Prüfungsleistung:
- wenn möglich schriftliche Prüfung
- letzte Einheit ist für Prüfungsvorbereitung vorgesehen

Hilfsmittel bei Prüfung:
- wahrscheinlich 1 DIN A4 - Zettel handschriftlicher eigener Notizen


## 1.2 Inhaltlicher Teil
### 1.2.1 Kommunikationsszenario

<img src="./resources/NIC.png" alt="NIC_Abbildung" width=500>

Bei Abruf einer Website durch Host A von Server A sind vielfältige Technologien zur Realisierung des Szenarios erforderlich.

**Physische Verbindung**
Auf welchem Weg gelangen die Daten von Host zu Server und zurück?

**Weiterleitung von Daten über das Internet**
- Protokolle, Header, ...

Wie müssen diese Daten gestaltet sein, damit sie verwendet werden können?

**Weiterleitung der Daten ans richtige Zielsystem**
Wie läuft das Routing ab?


### 1.2.2 Standardisierung

- ISO
- ITU
- IEEE
    - Fokus auf den "unteren" Schichten, nah an Physik
    - Ethernet, Netzwerkkarten, ...
- IETF
    - Standardisierung der Protokolle
    - HTTP, UDP, TCP, Mailprotokolle
    - ist kein Berufsverband, sondern Freiwilligenorganisation

### Internet Engineering Taskforce

- Publikationsformat der IETF sind RfC's (Request for Comments)
- RFC haben eindeutige, fortlaufend vergebene Nummern
- so ist UDP z.B. durch RFC 768 spezifiziert
- recht praxisnahe Beschreibung der Standards

#### Arbeitsgruppen  / IETF-Areas

- IETF-Arbeitsgruppen sind einem von 7 Bereichen (Areas) zugeordnet
    - Applications and Real-Time
    - Internet
    - Security
    - Operations and Management
    - Routing
    - General
    - Transport


### 1.2.3 Begrifflichkeiten

**Übertragungsmodi**

|verbindungsorientiert| verbindunglos|
|----|-----|
|Information über Existenz einer Beziehung liegt vor|Information über Existenz einer Beziehung liegt **nicht** vor|
|Beziehung zwischen Sender und Empfänger| Kommunikation kann ohne Verbindungsaufbau begonnen werden|
|z.B. TCP| z.B. UDP|


|leitungsvermittelt| paketvermittelt|
|----|----|
|Feste Durchschaltung zwischen Sender und Empfänger| Gemeinsame Nutzung von Leitungen|
|Ermöglicht Zusicherung von Eigenschaften (Quality of Service- Parameter)|Daten werden in Pakete aufgeteilt, die (direkt oder indirekt) Informationen für die Zuordnung zu einem Empfänger beinhalten|
|zu beachten: es müssen dann soviele Leitungen vorhanden sein, wie genutzt werden sollen|zu beachten: Überlastsituationen können auftreten|


Im Großen und Ganzen ist "das Internet" paketvermittelt, Leitungsvermittlung kann in Spezialfällen vorhanden sein


### 1.2.4 ISO / OSI Referenzmodell  <!-- hochgradig Prüfungsrelevant-->

<img src="./resources/ISO_OSI_Layer.png" alt="ISO/OSI Layer" width=500>

#### 7 Anwendungsschicht
- Durch anwendungsspezifische Protokolle verwendet

#### 6 Darstellungsschicht
- Umwandlung von Daten in unabhängiges Format

#### 5 Sitzungsschicht
-
#### 4 Transportschicht
- fügt Zusatzinformationen in die Pakete ein, um die Verwendung auf Empfängerseite zu definieren


#### 3 Vermittlungsschicht
- Weiterleitung über lokale Netze hinaus / zwischen verschiedenen Netzen
- unabhängig vom Typ der verwendeten Netze

#### 2 Sicherungsschicht
- einzelne Bitfolgen werden als Frames erfasst
- Redundanzinformationen werden hinzugefügt um Fehlererkennung und -korrekturen (auch auf Empfängerseite) zu ermöglichen (z.B. Paritätsbits)
-  Beispielverfahren: CRC (Cyclic Redundancy Check)


#### 1 Bitübertragungsschicht
- einzelne Bits in physikalische Signale umwandeln und umgekehrt
- Modulation und Demodulation

### 1.2.5 TCP / IP-Modell

 Integriert das Referenzmodell, verwendet dazu 4 Schichten.
 Siehe dazu Folie 14.

### 1.2.6 Protokoll-Header

Siehe Folie 15

### 1.2.7. Kopplungselemente

![Switches und Router](resources/L2-net.png)

#### **Switches**
- verbinden Netzsegmente (Broadcast-Domains) und leiten Pakete zwischen diesen weiter
- sind Layer 2 - Kopplungselemente
- Netzwerkkarten im gleichen Netzsegment können sich gegenseitig direkt addressieren (per MAC-Adresse)
- speichern intern eine Zuordnung zwischen Ausgangsports und MAC-Adressen
- Alternative Namen: Bridge, L2-Switch

#### **Router**

- leiten Pakete zwischen unterschiedlichen Netzen weiter
- bei Weiterleitungsentscheidung wird IP-Adresse ausgewertet (Lookup in Routing-Tabelle)
- Alternativ auch: Layer-3-Switch

#### **Weitere Kopplungselemente**

- Hub, Repeater, Application-Layer-Gateway

**Kleiner Einschub, nicht komplett:**
```sh
ip addr show

ip neigh
# zeigt Nachbarn in ARP-Tabelle an
# IPv4, IPv6 und MAC-Adresse

ip r

ip route
```

### 1.2.8 Topologien

Unterscheidung zwischen physikalischer und logischer Topologie.
Physikalisch dabei die tatsächlich vorhandenen (physischen) Netzwerkkomponenten und ihrer Verbindungen.
Logisch dabei die Kommunikationsbeziehungen und der Struktur des Datenflusses.

Grafische Aufarbeitung versch. Topologien auf Folie 17

Zu beachten: Gibt es SPF (single point of failure) im Netz? Wenn ja: Ausfallsicherheit gering

**hier fehlen noch Dinge**

### Tooling - Wireshark

- nützliches Tool zur Darstellung von Kommunikationsvorgängen in Netzwerken
- es ist eine Filterfunktionalität vorhanden um gezielt nach IP-Adressen, Protokollen, Ports,... zu suchen
- dabei verwendete Bibliothek: **LIBPCAP**

Auch verwendetes Tool: Scapy

# 2. Netzzugangsschicht

## 2.1 Übersicht zu Ethernet

- Ursprünglich für LAN-Kommunikation vorgesehen
- Klassisch: Steuerung des Zugriffs auf den Kanal über CSMA/CD-Algorithmus (bei Punkt-zu-Punkt obsolet)
- Seit den 1980iger Jahren verschiedene Varianten etabliert, die sich bzgl.
Übertragungsraten, Kabeltypen und Leitungskodierung unterscheiden
	- Datenraten von 10 Mbit/s bis 400 Gbit/s, ...
	- Leitungskodierung u.a.: Manchester-Code, 4B5B-Code, 8b10b-Code, ...
	- Kabeltypen u.a.: Koaxialkabel, Twisted-Pair-Kabel, Multimode
Lichtwellenleiter, Singlemode Lichtwellenleiter, ...
- Alternative: z.B. Infiniband

## 2.2 Aufbau eines Ethernet Frames

![Ethernet Frame](resources/eth-frame.png)

- Präambel: Synchronisation zwischen Kommunikationspartnern
- SFD: Start of Frame Delimiter (fest Bitfolge zur Identifikation des Frame-Anfangs)
- Quell-/Zieladresse: global eindeutige 6-Byte-Adresse
- Nutzdaten: maximal 1500 Bytes Nutzdaten (Header höherer Schichten + Daten)
- Typ-Feld: Typ-Feld der nächsthöheren Netzwerkschicht (z.B. `0x0800` für IPv4) - alternativ Längenfeld
- Padding: Gewährleistet Minimalgröße von 64 Byte
- CRC-Checksum: 32-Bit-Prüfsumme über das Frame (von Zieladresse bis Padding-Feld)

## 2.3 Namen von Netzwerkschnittstellen unter Linux

- Alt: `ethX` bzw. `wlanX` (an MAC gebunden -> Probleme bei Tausch)
- Neu: Consistent Network Device Naming (z.B. `enp0s25`)
	- Ethernetinterface (en), das an PCI-Bus (p) an Slot 25 hängt

## 2.4 Switches

- Multiport Kopplungselemente, das Frames nur an den Port weiterleitet über den der Empfänger erreichbar ist
- Speicherung von Adressen in Source-Address-Table (SAT)
- **Cut-Through Switches:** Nach Analyse der MAC-Adresse sofortiges Durschalten zum entsprechenden Port (Weiterleitung ohne Zwischenspeicherung = geringe Latenz, kein Einfluss auf Datenrate)
- **Store-and-Forward Switches:** Frame wird am Eingangsport und Ausgangsport gepuffert (größere Latenz, Möglichkeit zur Zwischenverarbeitung der Daten)

### 2.4.1 Architekturtypen

- **Shared Memory:** CPU kopiert Daten nach Extraktion der Zieladresse in den korrekten Ausgangspuffer
- **Bus-System:** Empfangener Port leitet Frame über gemeinsamen Bus an richtigen Ausgangsport
- **Switching-Matrix:** Physische Durchschaltung von Ein- und Ausgabeleitungen

### 2.4.2 Kenngrößen

- Datenrate der verschiedenen Ports
- Datenrate des Backplanes (der internen Busse)
- Port-Typen
- Maximale Größe des SAT
- Managementinterface (CLI/WEB UI/ SNMP)
- Unterstützte RFCs und IEEE-Standards
- Bandbreitenmanagement
- Preis

### 2.4.3 Spanning-Tree-Protocol <!--wahrscheinliche Prüfungsaufgabe-->

- STP etabliert sich innerhalb des Netzes einen Spannbaum durch das Blockieren von Ports, die Zyklen erzeugen würden
- Blockierter Port: Eingehender und ausgehender Traffic wird verworfen, Kanal ansonsten voll funktionsfähig
- STP reagiert automatisch auf Link-Fehler und berechnet einen neuen Spannbaum unter Berücksichtigung ausgefallener Verbindungen (-> Aktivierung blockierter Ports im neuen Spannbaum)

**Ablauf**

1. Root-Bridge bestimmen: alle Bridges senden Priorität und MAC an alle (höchste Priorität / geringste MAC wird Root)
2. Bestimmung zur kürzesten Pfade zur Root-Bridge (Pfadlänge wird an jedem Switch unter Berücksichtigung der Datenrate automatisch inkrementiert)
3. Deaktivieren aller Ports, die nicht Root sind

**Begriffe**

- Root-Port: Switch Port, der am nächsten zur Root-Bridge liegt
- Designated Port: Alle Ports, die kein Root-Port und nicht blockiert sind  
- Non-Designated Port: Ports in blockiertem Zustand um Zyklen zu verhindern  

#### 2.4.3.1 STP - Port Fast/Fast Link

- STP weist Konvergenzprobleme auf: Netzwerk erst nach etwa 30 Sekunden funktionstüchtig (Probleme beispielsweise mit PXE Boot)
- Switches bieten Speziellen Modus für Ports an denen Endsysteme angeschlossen sind (Port geht sofort bei Aktivierung in Forwarding State)
- Herstellerspezifische Terminologie: PortFast (Cisco), Fast Link (NetGear)

#### 2.4.3.2 Rapid Spanning Tree Protocol

- Proaktiver Ansatz bei dem effizient auf Alternativpfade gewechselt werden kann

### 2.4.4 Virtuelles LAN

- Physisches Netzwerkdesign steht häufig mit logischem Netzwerkdesign in Konflikt
- logische Einteilung des Netzes auf Ebene der Switche (Aufteilung in Broadcast-Domänen; erhöhte Sicherheit)

**Varianten**

- Portbasierte VLANs: jeder Port kann Mitglied exakt eines VLANs sein
- Tag-basierte VLANs: Frames werden mit ID eines VLANs getaggt, wodurch über einen Port mehrere VLANs realisiert werden können
- dynamische/inhaltsbasierende VLANs: Zuordnung zu VLANs anhand verwendeter Protokolle (weniger verbreitet)

#### 2.4.4.1 Tag-basierte VLANs

- Erweiterung der Ethernet-Frames um einen Tag zur Identifikation des VLANs zu dem das Frame gehört

**Aufbau** (4 Bytes)

![](resources/vlan-tag.png)

- **Tag Protocol Identifier:** fixer Hex-Wert
- **Priority Code Point:** Prioritätsinformationen
- **Drop Eligible Indicator:** Identifiziert Frames, die bei Überlast verworfen werden können
- **VLAN Identifier:** ID des zugehörigen VLANs ($2^{12}-2$ = max. 4096 VLANs)

#### 2.4.4.2 Inter-VLAN-Routing

**Ansatz 1**

- Routing zwischen VLANs ohne zusätzliche Softwareunterstützung durch in unterschiedlichen VLANs befindliche Physikalische Schnittstellen eines Routers möglich
- Problem: hoher Aufwand für Hardware (für jedes VLAN physische Schnittstelle plus Verkabelung)


- **Ansatz 2:** Einsatz von virtuellen Interfaces zur Vermeidung des hohen Aufwandes für separate Schnittstellen
<!-- Gerne Prüfungsfrage: Voraussetzungen/Konfigurationsschritte -->

#### 2.4.4.3 STP und VLAN

> STP weiß nix von VLANs

- klassischer Ansatz nutzt die verfügbaren physischen Verbindungen nicht optimal aus
- Lösung: Multiple Spanning Tree Protocol (jedes VLAN hat eigenen ST + ein Internal Spanning Tree für alle VLANs)

### 2.4.5 Transparent Interconnection of lots of links (TRILL)

- Ethernet-Frames werden in einen TRILL-Header gekapselt
- Routing dieser Frames auf deren Basis auf L2 (nächster Hop wird durch umgebenen L2-Header angegeben)
- Nutzung von Intermediate System to System zur Ermittlung von Pfaden zwischen Rbridges
- TRILL-Header besitzt HOP-Count-Feld um Routing-Schleifen zu vermeiden
- Entfernung des THRILL-Headers vor Auslieferung an das Zielsystem

### 2.4.6 Stacking

- Stackfähige Switsches können miteinander zu einer Gruppe verbunden werden (einzelnes logisches Gerät, ansprechen über einzelne IP)
- Vorteile: Skalierbarkeit (Anzahl der Ports einfach ), vereinfachte Netzwerkschnittstelle (Konfiguration von nur einem logischem Gerät), Vergrößerter Durchsatz (Stacking über Port mit hoher Datenrate)
- Nachteil: Platzbedarf, höherer Stromverbrauch mehrerer Geräte, Kopplung als neue Fehlerquelle



# 3. Vermittlungsschicht: Internet Protocol

- Schicht 3; von Übertragungsmedium unabhängig
- Overlay über L2, bildet davon unabhängiges Netz
- Ermöglicht Adressierung von "Knoten"
- zwei Versionen verbreitet: IPv4 und IPv6
- IP-Paket wird trotz Hops nicht verändert (Ausnahme: NAT)
- Bezeichnung Hostadresse eigentlich falsch -> Schnittstellenadresse 
- eine IP-Adresse ist nicht einem Host zugewiesen, sondern einem NIC
  - Workaround: Loopback-Interface, zur Adressierung von Localhost
- *casts:
  - Unicast: Senden an exakt einen NIC
  - Broadcast: Senden an alle NICs
  - Multicast: Senden an Teilmenge
  - Anycast: Senden an alle NICs, aber nur einer antwortet

## 3.1 IPv4

### 3.1.1 IPv4-Header

![Aufbau des IPv4-Headers](resources/ip-paket-aufbau.png)

- Version: 4 Bits, Protokollversion
- Internet Header Length (IHL): 4 Bits, Länge des Headers in 32 Bit Wörtern, Standardwert 5 --> 5 * 32 Bit = 20 Byte
- Differenciated Service Code Point (DSCP): 6 Bit, Prioritätsklassen
- Explicit Congestion Notification (ECN): 2 Bit, Meldung von Überlast, von Layer 4 gesteuert, wird damit rückläufig zu Sender kommuniziert "Bitte sende langsamer"
- Total Length: 16 Bit, Gesamtlänge des Datagramms / Fragments in Bytes
- Identification: 16 Bit, ID des Datagramms
- Flags: 3 Bit:
  - Bit 0: reserviert (RFC3514)
  - Bit 1: Don't Fragmen (DF)
  - Bit 2: More Fragments (MF)
- Fragment Offset: 13 Bit, Offset in 8 Byte Blöcken, die Daten innerhalb des urspr. Paket hatten
- Time to Live (TTL): 8 Bit, Lebenszeit des Pakets, in Praxis maximale Anzahl der Hops
- Protocol: 8 Bit, im Datenbereich verwendetes Protokoll, Bsp. in Linux: ``/etc/protocols``
- Header Checksum: Prüfsumme für (nur) IP-Header
- Options: Zusatzdaten für bspw. Routing oder Zeitstempel
  - Bsp Source Routing: Sender gibt exakte Route an; ermöglicht Angriffsfläche für DoS-Attacken

### 3.1.2 Fragmentierung

![Bild von Fragmentierung](resources/ip-fragmentierung.png)

- 1:1 Übersetzung von IP-Paket und ETH-Frame
- Maximum Transmission Unit (MTU): Maximalgröße des ETH-Payloads
  - ETH-Payload enthält auch IP-Header,... --> nicht tatsächliche Nutzdatengröße
  - größer: weniger Overhead, anfälliger für Fehler, höherer Speicherbedarf in Netzwerkkomponenten
  - kleiner: weniger Latenz, mehr Overhead
- wenn IP-Paket größer als MTU: muss fragmentiert werden
  - Ergebnis sind n vollwertige IP-Pakete inkl. Header
  - alle Pakete gleiche Identification Nummer  (zum Rekonstuieren des urspr. Paket)
  - Flags:
    - MF-Flag = 1 bei allen außer dem letzten Paket
    - Fragment Offset: zählt Byteposition hoch
- Wo wird fragmentiert?
  - bei IPv4 kann bei jedem Hop auf der Route fragmentiert werden, Performanceverlust 
  - bei IPv6 wird beim Sender fragmentiert
- Pass-MTU: bezeichnet geringste MTU aller Hops auf der Route 

```
# MTU anzeigen lassen 

ip addr show
```

### 3.1.3 IPv4-Adressierung

- Struktur: 0 bis n Bits Netzadresse, 32-n Bit Hostadresse (NIC-Adresse)
- Notation: ``adresse/n`` --> Classless Inter Domain Routing Notation (CIDR)
- Netzanteil ermöglicht Ausbildung einer hierarch. Struktur, skalierbar
- Einteilung von IPv4-Adressen in öff. Adressen (innerhalb des Intenets eindeutig, durch zentrale Instanz vergeben) und private Adressen (innerh. eines lokalen Netzes eindeutig)
- insbesondere durch IPv4-Adress-Knappheit werden öff. Adressen durch Network Address Translation (NAT) auf mehrere Hosts abgebildet
- Routing:

![Bild eines Routers](resources/routing-bsp.png)

## 3.2 Address Resolution Protocol (ARP)

### 3.2.1 Einordnung

![Ablauf von ARP](resources/ip-arp-ablauf.png)

- ARP ermittelt zu IP-Adressen und weiteren Adressfamilien die zugehörigen Hardwareadressen
- Request-Reply-Protokoll
- ermittelte Zuordnung für best. Zeitraum in ARP-Tabelle gespeichert
- wenn Ziel-NIC außerhalb des eigenen Netzwerks: Ermittlung der MAC-Adresse des **Gateways**, nichts dahinter
  - siehe folgendes Bild:

![Bild ARP Beispiel](resources/ip-arp-bsp.png)

```
# Für Anzeige von ARP-Anfragen (Beispiel)

tcp dump -i any -p arp
```

### 3.2.2 Protokolldetails

//TODO: Bild Folie 7

//TODO: ausfüllen

## 3.3 ICMP

- Internet Control Message Protocol dient der Kommunikation von Fehlern und Abfrage von Statusinformation in (fast immer) IP-basierten Netzwerken
- ausgewählte Typen:
  - 0: Echo Reply: Antwort auf Echo Request
  - 3: Destination Unreachable: Ziel nicht erreichbar mit folgenden Codes:
    - 0 - Net unreachable
    - 3 - Port unreachable
    - 4 - Fragmentation needed and Don't Fragmen (DF) was set
  - 5: Redirect: siehe unten
  - 9: Router Advertisement: dient automatischen Discovery von Routern
  - 11: Time Exceeded: TTL-Feld aus IP-Datagramms abgelaufen
  - 13: Timestamp: TODO
- Aufbau:
  - 8 Bit Typ (s.o.)
  - 8 Bit Code (s.o.)
  - 16 Bit Prüfsumme
  - weitere Inhalte abhängig von Typ / Code

Möglichkeiten: 
- mehr Funktionen als "nur" Ping
- Fehlermeldungen können im Netzwerk propagiert werden 
- Zeitstempel können zur Lastermittlung genutzt werden

Beispiel: ICMP-Redirect

- wird von einem Gateway versendet, wenn es feststellt, dass ein Router im gleichen Netz liegt, sodass direkt mit diesem kommuniziert werden kann
- bietet Angriffsfläche: kann verwendet werden, um kompromittierten Router in den Pfad zu zwingen
- per Default in vielen Systemen deaktiviert

## 3.4 Praxisübung

Exkurs Namespaces: 

- Namespaces bieten Möglichkeit, separate Netzwerk-Stacks lokal zu schaffen 
- Zu Beginn leere und frei konfigurierbare Stacks 
- es können komplette lokale Netzwerke innerhalb eines Kernels geschaffen werden 
- wird zum Beispiel für Docker genutzt
  - dort aber auch noch separate Namespaces für PIDs, IP-Tables, Filesystem
  

Verknüpfung von 3 Network Namespaces:

![Bild der Aufgabenstellung](resources/uebungsaufgabe.png)

- 3 Namespaces erstellen:

```bash
sudo ip netns add ns1
sudo ip netns add ns2
sudo ip netns add ns3

sudo ip netns list # zur Prüfung
```

- virtuelle Ethernet-Interfaces erstellen:

```bash
sudo ip link add veth1 netns ns1 type veth peer name veth2 netns ns2 # erstellt veth1 in ns1 und veth2 in ns2
sudo ip link add veth3 netns ns2 type veth peer name veth4 netns ns3
```

- Namespace betreten und Interface aktivieren:

```bash
sudo ip netns exec ns1 /bin/bash
ip link set veth1 up
```

- diesen Schritt für alle Interfaces wiederholen
- allen VEth-Interfaces die gewünschten Adressen vergeben: (für alle Interfaces wiederholen)

```bash
sudo ip netns exec ns1 /bin/bash
sudo ip addr add 192.168.42.5/24 dev veth1
```

- Routen zwischen den Namespaces anlegen:

```bash
sudo ip netns exec ns1 /bin/bash
ip route add 192.168.23.0/24 via 192.168.42.254
```

- diesen Schritt für alle Namespaces / gewünschten Routen wiederholen
- Kernel anweisen, für das Router-Namespace das Routing zu aktivieren:

```bash
sudo ip netns exec ns2 /bin/bash
echo 1 > /proc/sys/net/ipv4/ip_forward
```

- mit bspw. Ping überprüfen, ob Verbindung funktioniert

## 3.5 Nachteile IPv4

- Ausgeschöpfter Adressraum 
  - theoretisch nur 4 Mrd. Adressen 
  - diese auch noch ungünstig vergeben (/8 Netz für IBM)
  - Einsatz von NAT (Network Adress Translation) kann Verwendung einiger Dienste erschweren (Ende-zu-Ende Prinzip wird gebrochen)

- Ineffizientes Routing
  - variable Länge der Header von IPv4-Paketen 
  - Header können mit Optionen auf bis zu 60 Bytes ausgeweitet werden 
  - Router prüfen, ob Paket die MTU überschreitet und fragmentieren ggf. 

- Keine automatische Konfiguration 
  - IP-Adresse muss manuell oder über DHCP (Dynamic Host Configuration Protocol) vergeben werden 
  - Zusätzliche Infrastruktur für automatische Konfiguration erforderlich

## 3.6 IPv6

### 3.6.1 Header

![IPv6-Header](resources/IPv6_Header.png)


Hop Limit: 
- ehemals TTL
- zur Vermeidung von Zyklen
- bei jedem Hop dekrementieren um 1

### 3.6.2 Extension-Header

- in Zusammenhang mit Next-Header-Feld verwendet 
- (Folie 3/12)

### 3.6.3 IPv6-Fragmentierung 

- Grundprinzip ähnlich zu IPv4
- wenn auf Pfad MTU nicht ausreicht wird fragmentiert 
- Unterschied zu IPv4: 
- durch Sender fragmentiert, dadurch Effizienzsteigerung
- Absender wird über Fragmentierungsbedarf informiert (per ICMPv6-Nachricht "Packet too big")
- Praxis: 
- limitierende MTU meist an den Rändern, also beim Sender

### 3.6.4 Ipv6-Adressen - Notation


- `x:x:x:x:x:x:x:x`
- x = 4 hexadezimale Zahlen, je 16 Bit 

- längere 0-Folgen können einmalig abgekürzt werden: 
- `ff01:0:0:0:0:2342:78fa` -> `ff01::2342:78fa`

- Empfehlungen aus RFC: 
- führende Nullen des Blocks weglassen
- Zwei Doppelpunkte
- sollen maximale Anzahl von 0-Blöcken repräsentieren 
- nicht zur Abkürzung eines einzelnen Blocks verwenden 
- bei mehreren möglichen Kürzungen: möglichst weit links kürzen 
- bei Angabe von Portnummern: IPv6-Adresse in eckige Klammern
- `[ff01:0:0:0:0:2342:78fa]:80` oder `[ff01::2342:78fa]:80`

### 3.6.5 Adresstypen (Folie 3/15)

![IPv6-Header](resources/Adresstypen.png)

- Anycast:
- wird zum Beispiel bei DNS-Rootservern verwendet 

- Multicast: 
- um z.B. alle Router im Netz anzusprechen

### 3.5.6 Generelle Adresstruktur (Folie 3/16)

- Trennung zwischen Präfix und Interface Identifier
- Notation analog zu CIDR 
- `/64` am Ende gibt die Länge des Präfix an


![IPv6-Adresstruktur](resources/IPv6_Adresstruktur.png)

### 3.5.7 Erzeugung einer link-local Adresse (Folie 3/17)

- aus MAC-Adresse oder per Privacy Extension abgeleitet 

### 3.5.8 IPv6-Multicasts (Folie 3/18)

- es gibt mehrere Multicast-Gruppen an denen teilgenommen werden kann 
- es existieren zudem festgelegte "well-known" Multicast-Adressen 
- `ff02::1` -> alle Knoten am Link 
- zum Beispiel für ARP-äquivalente Anfragen 
- `ff02:2` -> alle Router am Link 
- `ff02::16` -> alle MLDv2-fähigen Router

### 3.5.9 Stateless Adress Autoconfiguration SLAAC (Folien 3/22,23)

**Prüfungsrelevant!**

![SLAAC Phase 1](resources/SLAAC_1.png)
![SLAAC Phase 2](resources/SLAAC_2.png)

## 3.6 Migration IPv4 -> IPv6 (Folie 3/24)

- momentane Koexistenz von v4 und v6 erfordert Mechanismen zur Realisierung des Übergangs und für Interoperabilität

- Mechanismen: 
- Dual-Stack: 
- beide Adressversionen für Interfaces
- Knoten können über beide Protokolle unabhängig voneinander kommunizieren 
- Tunnelmechanismen:
- Kapselung von Paketen von v4 in v6 oder umgekehrt
- Varianten: 4in6, 6in4, 6over4, ... 
- Translationsmechanismen: 
- Transformation der jeweiligen Header zur anderen Version 
- Beispiel: NAT64 zur Übersetzung von v4 zu v6 

### 3.6.1 Dual-Stack Lite (DS-Lite) (Folie 3/25)

- Kombination aus Tunnelmechanismen und Translation 
- Vorteile: 
- Providerinfrastruktur lann auf IPv6 umgestellt werden 
- IPv4-Adressen beim Provider werden eingespart 

![Dual-Stack Lite](resources/DS_Lite.png)   

## 3.7 Exkurs: Raw Sockets 

- Ermöglichen die Instanziierung von IP-Headern und Implementierung von Protokollen im User-Space 
- IP-Headerelemente wie auch gekapselte Datagramme können im Programm befüllt werden
- Durch Raw Sockets können z.B. implementiert werden:
- Netzwerksicherheitswerkzeuge wie Portscanner
- ICMP-basierte Anwendungen
- Routing-Protokolle

![Raw-Sockets](resources/Raw_Sockets.png)   

- Tooling: **Scapy** und **nmap**

- Frage: Wie kann unter Verwendung von Raw-Sockets ein einfaches TRACEROUTE gebaut werden? 

- Antwort: Mit Hilfe des TTL kann dies ermöglicht werden 
- erst TTL 1 (ICMP des ersten Routers)
- dann TTL 2 (ICMP des zweiten Routers)
- ...

- Problem: nicht alle Router haben diese ICMP-Antworten aktiviert, weitere Anpassung nötig 

## 3.8 Exkurs: IPv6 im Linux-Kernel 5.9 (Folien 3/27,28)

[//]: # (Hat hier jemand was?) 


## Praxisbeispiel radvd - SLAAC in Namespaces: 



- Namespaces erstellen:

```bash
sudo ip netns add ns1
sudo ip netns add ns2

sudo ip netns list # zur Prüfung
```

- virtuelle Ethernet-Interfaces erstellen:

```bash
sudo ip link add veth1 netns ns1 type veth peer name veth2 netns ns2 # erstellt veth1 in ns1 und veth2 in ns2
```

- radvd installieren und .conf anlegen

```bash

apt-get install radvd

touch /etc/radvd.conf

```

- .config bearbeiten

```bash
interface veth1
{
prefix 2001:db8:1:0::/64
{
AdvOnLink on;
AdvAutonomous on;
AdvRouterAddr off;
};
};
```

Quelle Beispielkonfig: https://github.com/reubenhwk/radvd/blob/master/radvd.conf.example

- radvd erneut starten und Status erfassen
```bash
sudo systemctl start radvd
sudo systemctl status radvd
```

- Namespace betreten und Interface aktivieren:

```bash
sudo ip netns exec ns1 /bin/bash
ip link set veth1 up
```

- diesen Schritt für zweites Interface wiederholen

- radvd in Namespace1 aktivieren 

**tbc: Anfang nächster Einheit**

```bash


```



<!--

# 4. Transportschicht: User Datagram Protocol und Transmission Control Protocol
# 5. Routing
# 6. Anwendungsschicht
# 7. Software-defined Networking
# 8. Netztechnologien
-->