<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Inhaltsverzeichnis**

- [Betriebssystemverwaltung](#betriebssystemverwaltung)
- [Vorteile Virtualisierung](#vorteile-virtualisierung)
- [Grundlagen](#grundlagen)
  - [Terminal](#terminal)
  - [VBox Guest Additions installieren](#vbox-guest-additions-installieren)
  - [VMs mit Snapshots vor Schäden schützen](#vms-mit-snapshots-vor-sch%C3%A4den-sch%C3%BCtzen)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

Betriebssystemverwaltung
========================

<!---
created by Maximilian Kerst, 05.10.2020

Disclaimer von Max: was ich hier reinschreibe, ist zT sehr oberflächlich, da wir hier erstmal Basics behandeln.
Falls jemand damit ein Problem hat, kann er gerne Details hinzufügen :-)
-->

# Vorteile Virtualisierung

- System anhalten, Snapshots, etc
- Experimente ohne Schäden
- viele VMs pro Host
- unterschiedliche Betriebssysteme komfortabel nutzen
- Hostausfälle kompensieren durch verschieben der VM

uvm

# Grundlagen

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
