<!----------
title: "Betriebssystemverwaltung"
date: "Semester 3"
keywords: [Betriebssystemverwaltung, DHGE, Semester 3]
---------->

Betriebssystemverwaltung
========================

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Inhaltsverzeichnis**

- [Mögliche Prüfungsfragen](#m%C3%B6gliche-pr%C3%BCfungsfragen)
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
  - [FTP-Vortrag](#ftp-vortrag)
  - [Samba](#samba)
  - [DHCP](#dhcp)
  - [MQTT](#mqtt)
  - [Apache2](#apache2)
  - [Fail2Ban](#fail2ban)
    - [Konfiguration](#konfiguration)
  - [Rsync](#rsync)
    - [vollständige Systemsicherung](#vollst%C3%A4ndige-systemsicherung)
  - [Quota](#quota)
    - [Windows](#windows-1)
    - [Linux](#linux-1)
  - [Nextcloud](#nextcloud)
  - [Prüfungsvorbereitung <!--Hallelujah-->](#pr%C3%BCfungsvorbereitung---hallelujah--)
    - [Aufgabe 1](#aufgabe-1)
    - [Aufgabe 2](#aufgabe-2)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

<!--
created by Maximilian Kerst, 05.10.2020

Disclaimer von Max: was ich hier reinschreibe, ist zT sehr oberflächlich, da wir hier erstmal Basics behandeln.
Falls jemand damit ein Problem hat, kann er gerne Details hinzufügen :-)
-->

<!--newpage-->

# Mögliche Prüfungsfragen

- Wie bezieht man Windows ISOs?
- Wie ermittelt man die Windows-Version / RAM-Menge / CPU-Kerne?
- Zweck der Virtual Box Gasterweiterung
- Nutzen von Hashing
- Befehle und Parameter, ein Befehl kann zum Parameter werden (man pages, sudo)
- Wie man Windows optionalfeatures (de)aktiviert?
- Welche Filesysteme sind Ihnen bekannt?
- Was ist ein Backup?
  - Kopie von Daten, um sie später wiederherstellen zu können
  - mögliche Tools: cp, scp, rsync,...
- Welchen Zweck hat ein DHCP-Server?
  - automatische Netzwerkkonfiguration
- Welchen Zweck hat ein FTP-Server?
  - Dateiübertragung über ein Netzwerk
- Zweck von FTP
- Was ist DD?
- Die Zeichen ">>" bzw. ">" im Skript bzw. tee -a
- Unterschied Datensicherung und Datenspiegelung
- Unterschied Datenrate und Bandbreite
- Welchen Zweck erfüllt `rsync`?
- Was ist ein Backup? Wie kann man ein Backup erstellen?
- Welche Informationen benötigt man um sich bei einem SSH-Server einzuloggen?
- Wie verwendet man Schleifen in Bash-Skripten?
- Warum sind Konfigurationsdateien schreibgeschützt? Nennen Sie ein Beispiel!
- Welche Installationsschritte müssen Sie für die Installation eines Webservers mit Datenbankanbindung anwenden? <!--Updates, Sicherung, Skripte bearbeiten,...-->
- Was ist ein DDoS-Angriff?
- Welche Vorteile bietet die Virtualisierung?
- Welche Schritte sind bei einem Verwaltungsakt zu beachten? <!--Sehr vage Frage, aber hier seine gewünschte Antwort: Zweck des Verwaltungsaktes, Backup, Installation und Konfiguration (grafisch oder per Skript -> gut für Automatisierung), Testen, Integrieren-->
- Was sind die Vorteile eines Skripts gegenüber interaktiver Konfiguration
- was sind Kontingente und warum sind sie notwendig?

<!--newpage-->

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

## FTP-Vortrag

- Kommunikationsprotokoll
- Datenaustausch zwischen Computern
- Clientgesteuerte Übertragung zw. zwei Servern
- Steuerkanal: Port 21
- Datenkanal: Port 20
- aktives oder passives FTP --> passiv kan NAT umgehen
- FTPS --> FTP mit TLS
- Installation Client: ``sudo apt install ftp``
- Installation Server: ``sudo apt vsftp``
- Windows: Server als Windows-Feature oder mit Filezilla
- interaktive FTP-Shell:
  - ``put dateiname`` --> hochladen
  - ``get dateiname`` --> herunterladen
  - ``pass`` --> schalten in den passiven Modus

Konfigurationsskript von Fabian und Charlotte:

```sh
#!/bin/bash

# lokale nutzer erlauben?
# -i(n-place: in der datei); s(earch); g(lobal: alle vorkommnisse)
read -p "lokale benutzer erlauben? (y/n) " c

if [ $c == "n" ]
then
 sudo sed -i 's/local_enable=YES/#local_enable=YES/g' /etc/vsftpd.conf
fi

# schreibzugriff erlauben?
# -i(n-place: in der datei); s(earch); g(lobal: alle vorkommnisse)
read -p "schreibzugriff erlauben? (y/n) " c

if [ $c == "y" ]
then
 sudo sed -i 's/#write_enable=YES/write_enable=YES/g' /etc/vsftpd.conf
fi

# anonym erlauben?
read -p "anonymen zugriff erlauben? (y/n) " c

if [ $c == "y" ]
then
 sudo sed -i 's/anonymous_enable=NO/anonymous_enable=YES/g' /etc/vsftpd.conf
fi

# ftp user erstellen?
read -p "ftp user erstellen? (y/n) " c

if [ $c == "y" ]
then
 # zugriff auf ftpuser beschränken
 echo "userlist_enable=YES
userlist_file=/etc/vsftpd.user_list
userlist_deny=NO" | sudo tee -a /etc/vsftpd.conf

 # ftpuser anlegen und userliste schreiben
 sudo adduser ftpuser --quiet --gecos "" --disabled-password
 read -sp "passwort eingeben: " pw | sudo chpasswd "ftpuser:$pw"
 echo "ftpuser" | sudo tee -a /etc/vsftpd.user_list
fi

# konfiguration übernehmen
sudo systemctl restart vsftpd.service
```

- Scripting möglich: FTP-Kommandos können in eine Textdatei geschrieben werden. Aufruf mit ``ftp dateiname``

## Samba

- Open-Source Implementierung des SMB-Protokolls
- Konfigurationsdatei in ``/etc/smb/smb.conf``

Freigabeordner erstellen:

```conf
[freigabename]
  path = pfad
  valid users = nutzername
  read only = no
```

- erstellen eines Nutzers: ``sudo smbpasswd -a nutzer``

## DHCP

- **D**ynamic **H**ost **C**onfiguration **P**rotocol
- automatisches Einbinden von Clients in TCP/IP-Netze (IP-Adresse, Gateway, Subnetzmaske, DNS)
- "automatische Zuordnung" - Client wird für Netzwerk konfiguriert, Einstellungen werden gespeichert
- "dynamische Zuordnung" - automatische Konfiguration, aber läuft nach Lease-Zeit ab

**Ablauf einer DHCP-Anfrage**

- `DHCP-Discover`: Client sendet Packet mit seiner MAC an alle anderen Clients im Netz
- `DHCP-Offer`: DHCP-Server nimmt Anfrage entgegen, antwortet mit zuweisbarer IP
- `DHCP-Request`: Client bestätigt Zusweisung der empfangenen IP
- `DHCP-Ack`: DHCP-Server bestätigt Zuweisung und sendet weitere Konfiguration (Gateway, DNS, ...)

**Wichtige Befehle**

```bash
# Neue DHCP Anfrage senden
sudo dhclient eth1
# Aktuelle IP freigeben
sudo dhclient -r eth1
```

## MQTT

- Übertragung von Daten mit geringer Bandbreite und instabiler Verbindung
- integriertes QoS
- serverseitig session-orientiert
- so wenig Metadaten auf Clients wie möglich
- datenagnostisch
- ereignisgesteuert: Publish/Subscribe-Modell
  - Publish von Clients auf Broker mit best. "Topic" zum Senden
  - Subscribe von Clients zum Broker mit best. "Topic" zum Empfangen
- Broker --> "Postfiliale"
  - nimmt Nachrichten an, verteilt sie an Empfänger, entweder sofort oder wenn Empfänger verfügbar
  - Broker-Redundanz: Einsatz mehrerer Broker möglich
- Clients (Publisher) nehmen ereignisgesteuert Kontakt zu Broker auf
- Clients können gleichzeitig Subscriber und Publisher sein
- ordnerartige Topic-Struktur zum Ordnen von Messages: `labor/exp1/temp/sensor1`
  - müssen mind. 1 Zeichen lang sein
  - dürfen Leerzeichen enthalten
  - case-sensitiv
  - hierarchische Ordnung
  - oberste Struktur --> ohne führendes `/`
  - single-level-wildcard (z.B. für Subscribers): `+`
  - multi-level-wildcard: `*` --> darf nur am Ende stehen
- verschiedene QoS-Level:
  - 0: Nachrichten "at most once", keine garantierte Auslieferung, keine Empfangsbestätigung, keine Speicherung
  - 1: Nachrichten "at least once", wird mind. 1x an Subscriber geliefert, Empfangsbestätigung via PUBACK-Paket, Mehrfachauslieferung möglich
  - 2: Nachrichten "exactly once", genau einmal gesendet und empfangen, großer Overhead durch komplexeres Bestätigungssystem
- verzögerte Nachrichten durch "Retained Messages"
  - kein Verwerfen der Nachrichten bei setzen der "retained-Flag"
  - Broker speichert **letzte Nachricht** eines Topics
  - sendet Messages, wenn Client verfügbar
- Session-Speicherung durch Persistente Sessions
  - speichert Informationen zum Status der Sessions
- Aktionen bei Verbindungsabbruch durch Last Will und Testament definierbar
  - bei Abbruch des Publishers wird ggf. eine Nachricht übermittelt, es sei denn, der Client kehrt vor Timeout zurück bzw. meldet sich regulär ab
- Authentifizierung und Sicherheit:
  - Support für VPN und TLS
  - Auth via Nutzer und Passwort (brokerseitig)
  - Erhöhung der Sicherheit durch ``clientId`` (einzigartiger Identifier)
  - Einschränkung von Topics, Handlungen und QoS für Nutzer möglich
- Einsatzgebiete da wo...
  - keine Client2Client-Kommunikation möglich
  - kompakte Datenübertragung gefordert
  - instabile oder langsame Verbindungen vorhanden
- Installation:

```bash
sudo apt update
sudo apt install mosquitto
sudo apt install mosquitto-clients
```

- Nutzung:
  - Subscriber: ``mosquitto_sub -h host -t topic # oder auch: topic/#``
  - Publisher: ``mosquitto_pub -h host -t topic -m message``

## Apache2

<!--Kampfwebserver-->

Apache2 vs. Ngin:

- Apache
  - älter, hat besseren Support und Verbreitung
  - ist mit Modulen erweiterbar
  - kann Interpretersprachen direkt verarbeiten
  - kann pro Thread nur eine Anfrage bearbeiten
  - unterstützt dezentrales Deployment via ``.htaccess`` Dateien
- Nginx
  - kann mehrere Anfragen pro Thread verarbeiten
  - nur statische Inhalte können bereitgestellt werden
  - erfordert z.B. für PHP einen externen Processor wie ``php-fpm``
  - nur zentrale Konfiguration
  - schneller

Konfiguration:

- ``a2dissite`` deaktiviert eine Seitenkonfiguration
- ``a2ensite`` aktiviert eine Seitenkonfiguration
- ``systemctl reload apache2`` lädt Konfiguration neu
- ``a2enmod`` aktiviert ein Apache-Modul, z.B. ``ssl`` oder ``rewrite``
- SSL erfordert einen neuen VirtualHost, der auf Port 443 hört

in den Config-Dateien:

- mehrere VirtualHosts möglich: ``<Virtualhost *:80> ... </VirtualHost>``
- darin mehrere Felder, die die Seiteneigenschaften enthalten (s. Beispielkonfiguration und \[Vortragsnotizen\])

Konfiguration einer Firewall:

```bash
sudo apt install ufw
sudo ufw enable
sudo ufw app list # gib Liste an Anwendungen aus
sudo ufw app info 'Apache Full'
sudo ufw allow 'Apache Full'
```

## Fail2Ban

- Schutz vor Brute-Force-Attacken
- Nutzung von "Jails" (Gefängnis) --> IP-Adressen werden bei (nicht-)Erfüllung in Sperrliste geschrieben
- besteht aus Client und Server
- geschrieben in Python

Funktionsweise (grob):
Fail2Ban überwacht zuvor angebene Logdateien nach einem definierten Filter (=Name des Service) auf Anmeldeversuche
1. Anmeldeversuch
2. Ergebnis des Versuch wird in Log geschrieben
3. Nach best. erfolglosen Versuchen: IP-Adresse für best. Ports für best. Zeit sperren (intern: Firewall Regel wie z.B. iptables)
4. optional Emailversand möglich
5. Freigabe der IP-Adresse nach Ablauf der Sperrzeit
6. erneute Versuche möglich

### Konfiguration

- in ``/etc/fail2ban``
- relevant: ``jail.conf``, ``jail.local``, ``action.d/``
  - nur jail.local bearbeiten, da ``jail.conf`` beim Update überschrieben wird

Beispiel:

```conf
[servicename]
enabled=true
port=22
filter = sshd
logpath=/var/log/auth.log # Überwachte Datei, die zum Erkennen der Fehlversuche genutzt wird
maxretry=3
```

- Überprüfen des Fail2Ban-Status: ``sudo fail2ban-client status`` und ``sudo fail2ban-client status sshd``
- IP-Adresse entbannen: ``sudo fail2ban-client set sshd unbanip ipadress``

## Rsync

- Abgleich von Dateien von lokalen System und Remotesystem
- Differenzial-basiert mit Quick-Check-Algorithmus
- Zweck
  - Sicherung
  - Spiegelung und Synchronisierung
  - reguläre Datenübertragung
  - kann verlustfrei unterbrochen werden
- Bandbreiteneinsparung, da nur Differenz kopiert
- Funktionsweise
  - Datei existiert noch nicht auf Ziel: vollst. Datei kopieren
  - Datei existiert auf Ziel: Prüfsummen bilden --> sind identisch?
  - wenn nicht identisch: Bildung von Differenzial, Kopie davon schicken
- Aufruf: ``rsync [OPTIONEN] QUELLEN ZIEL``
- Beispieloption: ``-a`` --> Übernahme aller Rechte und Eigentümer

### vollständige Systemsicherung

- benötigt root-Rechte, aber root über SSH sollte gesperrt sein --> eigener Nutzer für ausschließlich rsync
- ``rsync --rsync-path="sudo rsync" --delete -avzbe ssh rsyncnutzer@example.com:/ /backup --backup-dir=~/old``
  - ``--delete``, ``-b`` und ``--backup-dir`` kann auch weggelassen werden, aber dann werden gelöschte Dateien auf der Quelle nicht auf dem Ziel gelöscht

## Quota

- Zweck: Verminderung spontaner Out of Storage Situationen, Begrenzung von Speicherplatz für Nutzer

### Windows

- GUI (empfohlen): durch RSAT Tool / FSRM (Ressourcen-Manager für Dateiserver)
- Konfiguration globaler Emails notwendig
- es gibt Kontingent-Vorlagen
- Warnschwellen, Berichte an Nutzer und Admins (Eventlog + Mail), Befehle möglich (einstellbar)

### Linux

- Installation:

```bash
sudo apt update
# sudo apt full-upgrade
sudo apt install quota
quota --version # Kontrolle
```

- Konfiguration:
  - Option in der ``/etc/fstab`` notwendig: ``usrquota,grpquota``
  - ohne reboot neu mounten: ``mount -o remount /mountpoint``
  - Kontrolle: ``cat /proc/mounts | grep '/mountpoint'``
- ``sudo quotacheck -ugm /mountpoint`` erstellt Konfigurationen
- ``sudo quotaon -v /mountpoint`` aktiviert Quota
- ``sudo edquota -u user`` Soft- und Hard-Limits konfigurieren
- ``sudo repquota -s /mountpoint`` erstellt Report

## Nextcloud

- Zweck: freie Speicherung von Daten auf priv. Server
- Synchronisation von Daten
- Videokonferenzen und Screenshare möglich (via Erweiterungen)
- Anm. v. Max: FOSS-Ersatz für Cloudspeicher
- Vorteile:
  - kein Kontrollverlust über Daten
- Nachteile:
  - eigene Resourcen zum Betrieb nötig
  - hoher Konfigurationsaufwand <!--naja nee-->
-

## Prüfungsvorbereitung <!--Hallelujah-->

### Aufgabe 1

- OS: Windows
- alle Netzlaufwerke trennen
- "Glinka" Buchst. E zuweisen
- "Guenther" Buchst. F zuweisen
- "Herbst" Buchs. O zuweisen

```bat
@echo off
net use E: /delete /yes
net use F: /delete /yes
net use O: /delete /yes

net use E: \\192.168.71.100\Transfer\Glinka
net use F: \\192.168.71.100\Transfer\Guenther
net use O: \\192.168.71.100\Transfer\Herbst

pause
```

### Aufgabe 2

- OS: Linux
- ``service.conf`` anlegen, prüfen, ob schon vorhanden
- nur Benutzer hat ``RWX``-Rechte
- schreiben Sie mit zwei unterschiedlichen Methoden in die Datei
  - 1 Mal "Zeile 1"
  - 1 Mal "Zeile 2"
- Austausch von "Zeile2" durch "Zeile2=ON"
- Ausgabe von ``service.conf``

```sh
#!/bin/bash
if [ -f "service.conf" ]; then
  echo "Datei existiert schon. Fahre trotzdem fort."
fi
touch service.conf
chmod 700 service.conf
echo Zeile1 > service.conf
echo Zeile2 >> service.conf
sed -i 's/Zeile2/Zeile2=ON/g' service.conf
cat service.conf
```

```txt
Schreiben Sie ein Script mit dem Namen pv_XXXX_verwaltungsaufgabe_02
1. Legen Sie eine Datei (uebung2.conf) an, sofern sie nicht existert
2. Vergeben Sie folgende für die uebung2.conf nur Lese-Rechte für den user
3. Legen Sie ein Verzeichnis an (verwenden sie einen Parametrierung, so dass keine Fehler zum Abbruch des Scriptes führen)
4. Kopieren Sie die Datei in dieses Verzeichnis
5. Schreiben Sie den Hostnamen des Computers in die Kopie der Datei
6. Installieren Sie mc
7. Starten Sie den dhcp service neu
```

```sh
if [ ! -f "uebung2.conf" ]; then
  touch uebung2.conf
fi
chmod 400 uebung2.conf
mkdir -p test
cp uebung2.conf test/
cat /etc/hostname > test/uebung2.conf
sudo apt install mc
sudo systemctl restart dhcpd
```
