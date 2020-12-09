# Mögliche Prüfungsfragen

- Wie bezieht man Windows ISOs?
  - Media Creation Tool / Microsoft Downloads
- Wie ermittelt man die Windows-Version / RAM-Menge / CPU-Kerne?
  - Windows + Pause
  - ``winver`` (Windows-Verion)
  - Taskmanager (Leistungstab)
  - ``dxdiag``
  - Systeminformationen
- Zweck der Virtual Box Gasterweiterung
  - Drag&Drop
  - Copy&Paste
  - Resize der Fenstergröße
  - USB 3.0
  - Grafiktreiber/Grafikbeschleunigung
  - Peripheriegeräte des Hosts
- Nutzen von Hashing
  - Integrität von Dateien festellen (Abgleichen von gebildetem und übergebenem Hashwert)
- Programm und Parameter, ein Befehl kann zum Parameter werden (man pages, sudo)
  - ``sudo apt list --upgradable``
  - ``sudo apt list -u``
- Wie man Windows optionalfeatures (de)aktiviert?
  - ``Dism /online /enable-feature /featurename:NetFx3``
  - Systemsteuerung  \--> Programme und Features \--> Windows-Features aktivieren oder deaktivieren
- Welche Filesysteme sind Ihnen bekannt?
  - NTFS (Windows)
  - ReFs (Windows)
  - Fat 32 (Windows)
  - xfs (Linux)
  - ext4 (Linux)
- Was ist ein Backup?
  - Kopie von Daten, um sie später wiederherstellen zu können
  - mögliche Tools: cp, scp, rsync,...
- Welchen Zweck hat ein DHCP-Server?
  - automatische Netzwerkkonfiguration
- Welchen Zweck hat ein FTP-Server?
  - Dateiübertragung über ein Netzwerk
- Zweck von FTP
  - Dateitransfer zwischen Clients und Server
- Was ist DD?
  - Disk Dump \--> Sichern und Flashen von USB-Sticks (nicht Prüfungsrelevant)
- Die Zeichen ``>>`` bzw. ``>`` im Skript bzw. tee -a
  - Umleitung der Ausgabe
  - ``>`` File ersetzen
  - ``>>`` An File anfügen
  - tee -a An File anfügen und Ausgabe des Übergebenen
- Unterschied Datensicherung und Datenspiegelung
  - Datensicherung = Datensicherung auf zweitem System. Ist unabhängig von Änderungen an der Quelle.
  - Datenspiegelung = Datenkopie auf demselben System, aber auf verschiedenen Datenträgern. Ist abhängig von Änderungen an der Quelle.
- Unterschied Datenrate und Bandbreite
  - Bandbreite = Frequenzbereich, über den Kommunikation erfolgt. Rein physikalische Kenngröße.
  - Datenrate = Menge der übertragenen Daten in einem bestimmten Zeitraum
- Welchen Zweck erfüllt `rsync`?
  - Remotecopy über Netzwerk
- Welche Informationen benötigt man um sich bei einem SSH-Server einzuloggen?
  - IP/FQDN, Port, Passwort, Nutzer
  - Schlüsselpaar, dessen Public Key in der ``authorized_keys``-Datei des Servers eingetragen ist
- Wie verwendet man Schleifen in Bash-Skripten?

```bash
for i in $( seq 1 $1 )
do
	echo $i
	echo "haus:paula:günther:xaver"
done

for ((i = 1; i <= $#; i++ )); do printf '%s\n' "Arg $i: ${!i}" done
```

- Warum sind Konfigurationsdateien schreibgeschützt? Nennen Sie ein Beispiel!
  - Damit ein unprivilegierter Nutzer nichts kaputt macht
  - ``/etc/environment``
- Welche Installationsschritte müssen Sie für die Installation eines Webservers mit Datenbankanbindung anwenden? <!--Updates, Sicherung, Skripte bearbeiten,...-->
- Was ist ein DDoS-Angriff?
  - Systemüberlastung durch viele Hosts
- Welche Vorteile bietet die Virtualisierung?
  - Flexibilität
  - Ausnutzung Hardware
  - Sicherungspunkte
  - Testumgebung
  - Isolation zwischen Host und Gästen
  - parallele Ausführung mehrerer Betriebssysteme
  - Skalierbarkeit
- Welche Schritte sind bei einem Verwaltungsakt zu beachten? <!--Sehr vage Frage, aber hier seine gewünschte Antwort: Zweck des Verwaltungsaktes, Backup, Installation und Konfiguration (grafisch oder per Skript -> gut für Automatisierung), Testen, Integrieren-->
- Wie überwacht man Netzwerktraffic?
  - Wireshark
- Möglichkeiten zu Betriebssysteminstallation?
  - PXE-Boot
  - Image-Installation
- Was sind die Vorteile eines Skripts gegenüber interaktiver Konfiguration
  - einheitliche Konfiguration, kein versehentliches Ändern
  - Automatisierung möglich
- was sind Kontingente und warum sind sie notwendig?
  - Kontingente: logische Speicher-Begrenzungen für Ordner
  - verhindert übermäßige Nutzung durch Programme und Nutzer, damit System weiter arbeiten kann

Teil 2:

- Browser zeigt "Unable to connect" --> was tun?
  - physische Verbindung prüfen
  - IP-Konfiguration prüfen
    - Windows: ``ipconfig``
    - Linux: ``ip a``
  - Ping zu verlässlichem Server
  - DNS prüfen
  - Proxy-Einstellungen prüfen
    - Linux: ``/etc/environment``
- Was sind Elemente einer Firewall-Regel? (alternativ zu: erstellen Sie eine Firewall-Regel)
