Einführung in SSH
=================

## Einleitung

- **SSH** --> **S**ecure **SH**ell
- als verschlüsselte Alternative zu rlogin, Telnet, FTP entworfen, da unverschlüsselt [Quelle](https://web.archive.org/web/20170803235736/https://www.ssh.com/ssh/port)
- typische Nutzung: Remote Command Line Login, Dateitransfer, Nutzung als Tunnel
- allgemeiner Zweck: sicheres Bereitstellen von Netzwerkservices über ein unsicheres Netzwerk

[QUELLE](https://wiki.archlinux.org/index.php/Secure_Shell)

SSH hat viele verschiedene Einsatzgebiete:

- Verwaltung von Servern, auf die man nicht lokal zugreifen kann
- Sichere Übermittlung von Dateien
- Sicheres Erstellen von Back-ups
- Verbindung zwischen zwei Rechnern mit Ende-zu-Ende-Verschlüsselung
- Fernwartung von anderen Computern

[QUELLE](https://www.ionos.de/digitalguide/server/tools/secure-shell-ssh/)

- Nutzung als VPN-Tunnel und X11-Forwarding (Remote Desktop) [QUELLE](https://wiki.archlinux.org/index.php/OpenSSH)

## Installation

<!--Was hat man mit SSH auf dem Rechner? Verschiede Paketverwaltungen; SFTP-Server-->

### Client

<!--was kann der?-->

### Server

<!--unterteilung in SSH und SFTP-Server-->

## Konfiguration

### Client

<!--Keygen etc-->

### Server

<!--Absichern, Überblick, Umstellung auf Key-based Auth-->

## Absicherung mit Fail2Ban

### Installation

<!--selbsterklärend-->

### Konfiguration

<!--lediglich relevant: SSH, kann aber noch mehr-->

## VPN mit SSH

<!--es ist wohl möglich, mit SSH VPN Verbindungen zu machen-->