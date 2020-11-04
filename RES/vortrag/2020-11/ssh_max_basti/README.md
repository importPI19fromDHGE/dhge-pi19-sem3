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

- SSH-Client meist schon vorinstalliert

### Client

<!--was kann der?-->

- Debian und Verwandte: ``sudo apt install openssh-client``
- Arch und Verwandte: ``sudo pacman -S openssh`` (Kombipaket aus Server und Client)

--> Info an Max: Live "Demo" der Man-Page

### Server

<!--Unterteilung in SSH und SFTP-Server-->

- Debian und Verwandte: ``sudo apt install openssh-server`` und ``sudo apt install openssh-sftp-server``
- Arch und Verwandte: ``sudo pacman -S openssh`` (Kombipaket aus Server und Client)

- Starten des Servers
    - mit systemd: ``sudo systemctl start sshd``
    - mit SystemV / Upstart: ``sudo service sshd start``
- Autostart des Servers:
    - mit systemd: ``sudo systemctl enable sshd``

## Konfiguration

### Client

<!--Keygen etc-->

Um sich passwortlos gegenüber einem Server zu authentifizieren, benötigt man ein Schlüsselpaar:

```shell
$ ssh-keygen -t rsa
Generating public/private rsa key pair.
Enter file in which to save the key (C:\Users\User/.ssh/id_rsa):
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in C:\Users\User/.ssh/id_rsa.
Your public key has been saved in C:\Users\User/.ssh/id_rsa.pub.
The key fingerprint is:
SHA256:mstyW1phoEPqbMT3stzYUapfT6V/rBpMMyEHMmjiTp0 user@DESKTOP-EPNUPVN
The key\'s randomart image is:
+---[RSA 2048]----+
|       .+        |
|    . o. .       |
|   ..+... o      |
| . oo.E. o .     |
|  +o+   S + .    |
| + ..o * + =     |
|  + . * + =  .   |
| . ..O.B o o  o  |
|    =+O.  o.oo   |
+----[SHA256]-----+
```

Kopieren des öff. Schlüssels auf den Server (insofern passwortbasierte Auth aktiviert ist)

```shell
cat ~/.ssh/id_rsa.pub | ssh pi@raspberry "mkdir -p ~/.ssh && chmod 700 ~/.ssh && cat >>  ~/.ssh/authorized_keys"
```

[Quelle](https://www.digitalocean.com/community/tutorials/how-to-set-up-ssh-keys-2)

Darüber hinaus keine besondere Config notwendig.

Beispiel-Konfiguration:

```conf

# This is the ssh client system-wide configuration file.  See
# ssh_config(5) for more information.  This file provides defaults for
# users, and the values can be changed in per-user configuration files
# or on the command line.

# Configuration data is parsed as follows:
#  1. command line options
#  2. user-specific file
#  3. system-wide file
# Any configuration value is only changed the first time it is set.
# Thus, host-specific definitions should be at the beginning of the
# configuration file, and defaults at the end.

# Site-wide defaults for some commonly used options.  For a comprehensive
# list of available options, their meanings and defaults, please see the
# ssh_config(5) man page.

Host *
#   ForwardAgent no
#   ForwardX11 no
#   ForwardX11Trusted yes
#   PasswordAuthentication yes
#   HostbasedAuthentication no
#   GSSAPIAuthentication no
#   GSSAPIDelegateCredentials no
#   GSSAPIKeyExchange no
#   GSSAPITrustDNS no
#   BatchMode no
#   CheckHostIP yes
#   AddressFamily any
#   ConnectTimeout 0
#   StrictHostKeyChecking ask
#   IdentityFile ~/.ssh/id_rsa
#   IdentityFile ~/.ssh/id_dsa
#   IdentityFile ~/.ssh/id_ecdsa
#   IdentityFile ~/.ssh/id_ed25519
#   Port 22
#   Protocol 2
#   Ciphers aes128-ctr,aes192-ctr,aes256-ctr,aes128-cbc,3des-cbc
#   MACs hmac-md5,hmac-sha1,umac-64@openssh.com
#   EscapeChar ~
#   Tunnel no
#   TunnelDevice any:any
#   PermitLocalCommand no
#   VisualHostKey no
#   ProxyCommand ssh -q -W %h:%p gateway.example.com
#   RekeyLimit 1G 1h
    SendEnv LANG LC_*
    HashKnownHosts yes
    GSSAPIAuthentication yes
```

### Server

<!--Absichern, Überblick, Umstellung auf Key-based Auth-->

## Nutzung

<!--Todo: SSH-Shell, Dateitransfer, VPN (?), X11-Forwarding (?), SSHFS-->

## Absicherung mit Fail2Ban

### Installation

<!--selbsterklärend-->

### Konfiguration

<!--lediglich relevant: SSH, kann aber noch mehr-->

## VPN mit SSH

<!--es ist wohl möglich, mit SSH VPN Verbindungen zu machen-->