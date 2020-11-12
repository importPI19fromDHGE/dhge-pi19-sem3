Betriebssystemverwaltung
========================

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Inhaltsverzeichnis**

- [mögliche Prüfungsfragen](#m%C3%B6gliche-pr%C3%BCfungsfragen)
- [Vorteile Virtualisierung](#vorteile-virtualisierung)
- [Grundlagen Linux](#grundlagen-linux)
  - [Terminal](#terminal)
  - [VBox Guest Additions installieren](#vbox-guest-additions-installieren)
  - [VMs mit Snapshots vor Schäden schützen](#vms-mit-snapshots-vor-sch%C3%A4den-sch%C3%BCtzen)
- [Grundlagen Windows](#grundlagen-windows)
  - [Features hinzufügen / entfernen](#features-hinzuf%C3%BCgen--entfernen)
  - [Verwaltungsaufgaben](#verwaltungsaufgaben)
  - [Netzlaufwerk verbinden](#netzlaufwerk-verbinden)
    - [via Explorer](#via-explorer)
    - [via CMD](#via-cmd)
    - [Automatisieren: Skript](#automatisieren-skript)
  - [Leere Datei anlegen](#leere-datei-anlegen)
  - [Netzwerkconfig ausgeben](#netzwerkconfig-ausgeben)
  - [ICMPv4 (Ping) eingehend in der Firewall zulassen](#icmpv4-ping-eingehend-in-der-firewall-zulassen)
    - [Grafik](#grafik)
    - [CMD: vorhandene Regel aktivieren](#cmd-vorhandene-regel-aktivieren)
    - [CMD: neue Regel erstellen](#cmd-neue-regel-erstellen)
  - [Ping of Death](#ping-of-death)
    - [Windows](#windows)
    - [Linux](#linux)
  - [Windows-Netzwerkeinstellungen via Skript ändern](#windows-netzwerkeinstellungen-via-skript-%C3%A4ndern)
  - [Vorträge](#vortr%C3%A4ge)
    - [Themen](#themen)
    - [Was soll rein?](#was-soll-rein)
  - [Linux: Nutzerverwaltung](#linux-nutzerverwaltung)
    - [Nutzer im Terminal ändern](#nutzer-im-terminal-%C3%A4ndern)
    - [alle Nutzer anzeigen](#alle-nutzer-anzeigen)
  - [Linux: Skripte](#linux-skripte)
    - [SMB-Share einbinden](#smb-share-einbinden)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

<!---
created by Maximilian Kerst, 05.10.2020

Disclaimer von Max: was ich hier reinschreibe, ist zT sehr oberflächlich, da wir hier erstmal Basics behandeln.
Falls jemand damit ein Problem hat, kann er gerne Details hinzufügen :-)
-->

# mögliche Prüfungsfragen

<!---unvollständig!!! (LG Max)-->

- Wie bezieht man Windows ISOs?
- Wie ermittelt man die Windows-Version / RAM-Menge / CPU-Kerne?
- Zweck der Virtual Box Gasterweiterung
- Nutzen von Hashing
- Befehle und Parameter, ein Befehl kann zum Parameter werden (man pages)
- Wie man Windows optionalfeatures (de)aktiviert?
- Welche Filesysteme sind Ihnen bekannt?
- Zweck von FTP
- Was ist DD?
- Die Zeichen ">>" bzw. ">" im Skript bzw. tee -a 
- Unterschied Datensicherung und Datenspiegelung
- Unterschied Datenrate und Bandbreite
- Welchen Zweck erfüllt `rsync`?
- Was ist ein Backup? Wie kann man ein Backup erstellen?
- Welche Informationen benötigt man um sich bei einem SSH-Server einzuloggen?
- Wie verwendet man Schleifen in Bash-Skripten?

# Vorteile Virtualisierung

- System anhalten, Snapshots, etc
- Experimente ohne Schäden
- viele VMs pro Host
- unterschiedliche Betriebssysteme komfortabel nutzen
- Hostausfälle kompensieren durch verschieben der VM

uvm

# Grundlagen Linux

## Terminal

- ``ls`` zeigt aktuelles Verzeichnis an
- ``cd`` wechselt Verzeichnis
- ``sudo`` "SuperUser do" --> mache als Admin (root)
- ``./malware.sh`` führt die Datei ``malware.sh`` im aktuellen Verzeichnis aus
- ``.`` aktuelles Verzeichnis
- ``..`` übergeordnetes Verzeichnis
- ``apt`` bzw ``apt-get`` Debian erweiterte Paketverwaltung
- Linux Rechtesystem: ``rwxrwxrwx`` bzw ``777`` Notationen:
  - 6 Buchstaben:
    - r = read
    - w = write
    - x = execute bzw Recht, Ordner zu betreten
    - RWX-Blöcke aneinandergereiht, 1. für Besitzer, 2. für Gruppe, 3. für alle anderen
  - Drei Ziffern:
    - 2^0 (1) = execute / Verzeichnis betreten
    - 2^1 (2) = write
    - 2^2 (4) = read
    - diese addieren, z.B: ich möchte lesen und ausführen, aber nicht schreiben erlauben: 4 + 1 = 5
    - 3 Ziffern aneinandergereiht: 1. für Besitzer, 2. für Gruppe, 3. für alle anderen

Proxy installieren: global in die Umgebung: ``/etc/environment``

```conf
http_proxy="http://hyperion.ba-gera.de:3128/"
https_proxy="http://hyperion.ba-gera.de:3128/"
```

Updates installieren:

```bash
sudo apt update # Paketlisten aktualisieren --> sind nur Listen über die Pakete
sudo apt full-upgrade # oder: sudo apt-get dist-upgrade - macht dasselbe
```

## VBox Guest Additions installieren

- Gasterweiterungen einlegen
- mounten via Dateiverwaltung oder ``mount`` Befehl
- in Verzeichnis wechseln
- VBoxLinuxAdditions.run ausführen
- rebooten
- Fenster resizen

## VMs mit Snapshots vor Schäden schützen

- VM herunterfahren
- im VirtualBox-Manager Sicherungspunkt anlegen
- VM starten
- Schaden abwarten / risikoreiche Aktion ausführen
- im Fehlerfall: Snapshot zurückführen
- wenn alles gut: Snapshot kann gelöscht werden
- es können mehrere unabhängige Snapshots erstellt werden, zwischen deren Zuständen man wechseln kann

# Grundlagen Windows

- Skipped: Installation, Updates

## Features hinzufügen / entfernen

- Win+R --> ``optionalfeatures``
- In Kommandozeile: ``DISM.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux``
                    ``DISM.exe /online /disable-feature /featurename:Microsoft-Windows-Subsystem-Linux``

## Verwaltungsaufgaben

- Eventlog öffnen:
  - Rechtsklick auf Start --> Ereignisanzeige
  - auf Kommandozeile: ``eventvwr.msc``

## Netzlaufwerk verbinden

### via Explorer

- IP-Adresse eines Fileservers im Explorer eingeben
- Rechtsklick auf eine Freigabe
- ``Map Network Drive``
- Dialog sinnvoll ausfüllen

### via CMD

- ``net use * \\adresse\freigabe`` --> `*` bedeutet automatischer Laufwerkbuchstabe
- ``net use`` zeigt alle Netzlaufwerke an
- ``net use * /delete`` löscht alle Verbindungen (Analog mit bspw ``Z:``)
  - ohne Nachfrage: ``/y`` anhängen

### Automatisieren: Skript

ohne for-loop

```bat
@echo off
REM Hinzufügen von 10 Netzlaufwerken
net use * \\adresse\freigabe
net use * \\adresse\freigabe
net use * \\adresse\freigabe
net use * \\adresse\freigabe
net use * \\adresse\freigabe
net use * \\adresse\freigabe
net use * \\adresse\freigabe
net use * \\adresse\freigabe
net use * \\adresse\freigabe
net use * \\adresse\freigabe
```

mit for-loop:

```bat
@echo off

for /l %%x in (1, 1, 10) do net use * \\adresse\freigabe

pause
```

mit Buchstabenvorrat:

```bat
@echo off

for %%x in (A B D E F) do net use * \\adresse\freigabe

pause
```

For-Loop mit Ausgabe:

```bat
@echo OFF
REM Hinzufuegen von 10 Netzlaufwerken
for /l %%x in (1,1,10) do (
echo Geraet %%x hinzugefuegt
net use * \\192.168.71.100\transfer
)
pause
```

## Leere Datei anlegen

```bat
copy nul dateiname.txt
```

## Netzwerkconfig ausgeben

<!---GUI-Methode habe ich ausgelassen-->

```bat
ipconfig
pause
ipconfig /all
```

## ICMPv4 (Ping) eingehend in der Firewall zulassen

### Grafik

- ``wf.msc`` öffnen
- eine Variante: Firewall abschalten
  - in der Übersicht "Windows Defender Firewall Properties" das betreffende Profil im Feld "Firewall state" abschalten
- weitere Variante: Firewall-Regel aktivieren
  - in "Inbound Rules" "File and Printer Sharing (Echo Request - ICMPv4-In)" für das entsprechende Netzwerkprofil öffnen
  - Haken bei "Enabled" setzen

### CMD: vorhandene Regel aktivieren

```bat
@echo off
netsh advfirewall firewall set rule name="File and Printer Sharing (Echo Request - ICMPv4-In)" new enabled=yes
pause
```

### CMD: neue Regel erstellen

```bat
@echo off
netsh advfirewall firewall add rule name="Custom IPv4 allow" new action=allow profile=any protocol=icmpv4:8,any dir=in enable=yes
pause
```

## Ping of Death

### Windows

```bat
REM öffnet 200 CMD-Fenster, die 8KiB-ICMPv4-Requests abschicken
echo "ACHTUNG: Ressourcenhungrig"
pause
for /l %%x (1, 1, 200) do start ping -t -l 65500 127.0.0.1
```

### Linux

<!---//TODO-->

## Windows-Netzwerkeinstellungen via Skript ändern

- Nutzung von NetSh
- Was muss geändert werden?
  - IP-Adresse
  - Subnetzmaske
  - Gateway
  - DNS

```bat
@echo off

REM Lässt sich auch mit if + Klammern realisieren
REM %~1 --> keine Parameter angegeben, stelle Original wieder her
if "%~1" == "" goto orig
if "%1" == "orig" goto orig
if "%1" == "neu" goto neu
goto end

:orig
netsh interface ip set address name="Ethernet" dhcp
netsh interface ip set dns name="Ethernet" source=dhcp
goto end

:neu
netsh interface ip set address name="Ethernet" source=static addr=10.42.69.2 mask=255.255.255.0 gateway=10.42.69.1 gwmetric=0
netsh interface ip set dns name="Ethernet" source=static addr=1.1.1.1
REM Dass der DNS-Server ungültig wäre, ist lediglich eine Warnung. Er wird dennoch übernommen.
goto end

:end
pause
```

## Vorträge

Für die kommenden Stunden sollen Einführungsvorträge für verschiedene Themen erarbeitet werden und dann (ohne Note) für die anderen vorgetragen werden.
Als Redezeit ist 15min pro Redner vorgesehen.
Es soll nicht unbedingt zu sehr in die Tiefe gehen - der Fokus soll auf Sysadmin-Aufgaben liegen, sodass man also schonmal was von den wichtigsten Sachen gehört hat

### Themen

- Vorstellung DHCP-Server
- Vorstellung Samba-Server
- Datensicherung mit ``rsync``
- Apache2 <!--Kampfwebserver-->
- Vorstellung FTP-Server
- Vorstellung Jail
- Vorstellung SSH --> im Sysadmin-Kontext: Installation, Benutzung, Verwaltung, Nutzung Windows ...
- Aufsetzung eines Webservers
- "Nextcloud???"

### Was soll rein?

- Verwaltung
- Zweck
- Beispielkonfigurationen
- Notwendige Konfiguration
- "der Weg dahin"

<!--Max und Basti machen SSH-->

## Linux: Nutzerverwaltung

### Nutzer im Terminal ändern

``sudo -iu nutzer programm`` --> öffnet Programm (z.B. ``bash``) als angegebenen Nutzer inkl. Environment

### alle Nutzer anzeigen

- vollst. Informationen: ``cat /etc/passwd``
- ausschließlich Nutzernamen: ``cat /etc/passwd | cut -d: -f1`` --> trennt anhand von :, gibt das Erste aus
- nach Nutzer suchen: ``cat /etc/passwd | cut -d: -f1 | egrep "test|root"`` --> sucht nach Nutzern mit "test" ODER "root"
- Nutzer zählen: ``cat /etc/passwd | wc -l``

## Linux: Skripte

- Skripte sind Textdateien <!--doh-->
- Anlegen einer leeren Datei: ``touch script.sh``
- ausführbar machen einer Datei: ``chmod +x script.sh`` (gibt dem Besitzer Rechte zur Ausführung)
- Skript in Texteditor öffnen: ``vim script.sh`` oder ``nano script.sh`` oder \[...\]

Beispiel: einen Text variabel oft anhand eines Argumentes ausgeben:

```bash
#!/bin/bash

for i in $( seq 1 $1 )
do
  echo $i
  echo "haus:paula:günther:xaver"
done
```

### SMB-Share einbinden

```bash
#!/bin/bash

sudo apt update
sudo apt install cifs-utils
sudo mount -t cifs -o uid=1000,gid=1000,file_mode=0771,dir_mode=0771 //adresse/freigabe /mnt
# bindet \\adresse\freigabe auf den /mnt-Ordner und gibt Nutzer 1000 sowie Gruppe 1000 volle Rechte
```
