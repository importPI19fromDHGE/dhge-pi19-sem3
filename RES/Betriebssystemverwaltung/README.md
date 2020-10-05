# Betriebssystemverwaltung

created by Maximilian Kerst, 05.10.2020

Disclaimer von Max: was ich hier reinschreibe, ist zT sehr oberflächlich, da wir hier erstmal Basics behandeln.
Falls jemand damit ein Problem hat, kann er gerne Details hinzufügen :-)

## Vorteile Virtualisierung

- System anhalten, Snapshots, etc
- Experimente ohne Schäden
- viele VMs pro Host
- unterschiedliche Betriebssysteme komfortabel nutzen
- Hostausfälle kompensieren durch verschieben der VM

uvm

## Grundlagen

### Terminal

- ``ls`` zeigt aktuelles Verzeichnis an
- ``cd`` wechselt Verzeichnis
- ``sudo`` "SuperUser do" --> mache als Admin (root)
- ``./malware.sh`` führt die Datei ``malware.sh`` im aktuellen Verzeichnis aus
- ``.`` aktuelles Verzeichnis
- ``..`` übergeordnetes Verzeichnis
- ``apt`` bzw ``apt-get`` Debian erweiterte Paketverwaltung
- Linux Rechtesystem: ``rwxrwxrwx`` bzw ``777`` Notationen:
  - r = read
  - w = write
  - x = execute bzw Recht, Ordner zu betreten
  - RWX-Blöcke aneinandergereiht, 1. für Besitzer, 2. für Gruppe, 3. für alle anderen

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

### VBox Guest Additions installieren

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
