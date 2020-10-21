<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Inhaltsverzeichnis**

- [Betriebssystemverwaltung](#betriebssystemverwaltung)
- [mögliche Prüfungsfragen](#mögliche-prüfungsfragen)
- [Vorteile Virtualisierung](#vorteile-virtualisierung)
- [Grundlagen Linux](#grundlagen-linux)
  - [Terminal](#terminal)
  - [VBox Guest Additions installieren](#vbox-guest-additions-installieren)
  - [VMs mit Snapshots vor Schäden schützen](#vms-mit-snapshots-vor-schäden-schützen)
- [Grundlagen Windows](#grundlagen-windows)
  - [Features hinzufügen / entfernen](#features-hinzufügen--entfernen)
  - [Verwaltungsaufgaben](#verwaltungsaufgaben)
  - [Netzlaufwerk verbinden](#netzlaufwerk-verbinden)
    - [Via Explorer](#via-explorer)
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

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

Betriebssystemverwaltung
========================

<!---
created by Maximilian Kerst, 05.10.2020

Disclaimer von Max: was ich hier reinschreibe, ist zT sehr oberflächlich, da wir hier erstmal Basics behandeln.
Falls jemand damit ein Problem hat, kann er gerne Details hinzufügen :-)
-->

# mögliche Prüfungsfragen

<!---unvollständig!!! (LG Max)-->

- wie Windows ISO beziehen?
- Wie ermittelt man die Windows-Version / RAM-Menge / CPU-Kerne

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

### Via Explorer

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
  - in der Übersicht "Widnows Defender Firewall Properties" das betreffende Profil im Feld "Firewal state" abschalten
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