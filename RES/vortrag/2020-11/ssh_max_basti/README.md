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

- Debian und Verwandte: `sudo apt install openssh-client`
- Arch und Verwandte: `sudo pacman -S openssh` (Kombipaket aus Server und Client)

--> Info an Max: Live "Demo" der Man-Page

### Server

<!--Unterteilung in SSH und SFTP-Server-->

- Debian und Verwandte: `sudo apt install openssh-server` und `sudo apt install openssh-sftp-server`
- Arch und Verwandte: `sudo pacman -S openssh` (Kombipaket aus Server und Client)

- Starten des Servers mit systemd: `sudo systemctl start sshd`
- Autostart des Servers mit systemd: `sudo systemctl enable sshd`

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

```bash

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

- Schlüssel werden automatisch generiert
- Konfigurationsdatei: ``/etc/ssh/sshd_config``
- Standardkonfiguration ist zwar ausreichend, aber für Produktivbetrieb kann verbessert werden:

```conf
AllowUsers user1 user2
# erlaubt Zugriff nur für best. Nutzer

AllowGroups group1 group2
#erlaubt Zugriff nur für best. Gruppen

Port 4269
# ändert den Port, auf dem der Server lauscht

PermitRoot no
```

``authorized_keys``-Datei vor unbefugten Zugriffen schützen: ``chmod 600 ~/.ssh/authorized_keys``

Um Brute-Force Angriffen und schwachen Kennwörtern entgegenzuwirken, kann man die passwortbasierte Authentifizierung abschalten:

- sicherstellen, dass SSH-Schlüssel mit ausreichenden Rechten dem Server bekannt sind
- in ``/etc/sshd_config`` folgende Optionen setzen

```bash
PasswordAuthentication no
PubkeyAuthentication yes
ChallengeResponseAuthentication no
```

Beispiel-Konfiguration:

```bash
#       $OpenBSD: sshd_config,v 1.103 2018/04/09 20:41:22 tj Exp $

# This is the sshd server system-wide configuration file.  See
# sshd_config(5) for more information.

# This sshd was compiled with PATH=/usr/bin:/bin:/usr/sbin:/sbin

# The strategy used for options in the default sshd_config shipped with
# OpenSSH is to specify options with their default value where
# possible, but leave them commented.  Uncommented options override the
# default value.

#Port 22
#AddressFamily any
#ListenAddress 0.0.0.0
#ListenAddress ::

#HostKey /etc/ssh/ssh_host_rsa_key
#HostKey /etc/ssh/ssh_host_ecdsa_key
#HostKey /etc/ssh/ssh_host_ed25519_key

# Ciphers and keying
#RekeyLimit default none

# Logging
#SyslogFacility AUTH
#LogLevel INFO

# Authentication:

#LoginGraceTime 2m
PermitRootLogin no
#StrictModes yes
#MaxAuthTries 6
#MaxSessions 10

PubkeyAuthentication yes

# Expect .ssh/authorized_keys2 to be disregarded by default in future.
#AuthorizedKeysFile     .ssh/authorized_keys .ssh/authorized_keys2

#AuthorizedPrincipalsFile none

#AuthorizedKeysCommand none
#AuthorizedKeysCommandUser nobody

# For this to work you will also need host keys in /etc/ssh/ssh_known_hosts
#HostbasedAuthentication no
# Change to yes if you don't trust ~/.ssh/known_hosts for
# HostbasedAuthentication
#IgnoreUserKnownHosts no
# Don't read the user's ~/.rhosts and ~/.shosts files
#IgnoreRhosts yes

# To disable tunneled clear text passwords, change to no here!
PasswordAuthentication no
#PermitEmptyPasswords no

# Change to yes to enable challenge-response passwords (beware issues with
# some PAM modules and threads)
ChallengeResponseAuthentication no

# Kerberos options
#KerberosAuthentication no
#KerberosOrLocalPasswd yes
#KerberosTicketCleanup yes
#KerberosGetAFSToken no

# GSSAPI options
#GSSAPIAuthentication no
#GSSAPICleanupCredentials yes
#GSSAPIStrictAcceptorCheck yes
#GSSAPIKeyExchange no

# Set this to 'yes' to enable PAM authentication, account processing,
# and session processing. If this is enabled, PAM authentication will
# be allowed through the ChallengeResponseAuthentication and
# PasswordAuthentication.  Depending on your PAM configuration,
# PAM authentication via ChallengeResponseAuthentication may bypass
# the setting of "PermitRootLogin without-password".
# If you just want the PAM account and session checks to run without
# PAM authentication, then enable this but set PasswordAuthentication
# and ChallengeResponseAuthentication to 'no'.
UsePAM yes

#AllowAgentForwarding yes
#AllowTcpForwarding yes
#GatewayPorts no
X11Forwarding yes
#X11DisplayOffset 10
#X11UseLocalhost yes
#PermitTTY yes
PrintMotd no
#PrintLastLog yes
#TCPKeepAlive yes
#PermitUserEnvironment no
#Compression delayed
#ClientAliveInterval 0
#ClientAliveCountMax 3
#UseDNS no
#PidFile /var/run/sshd.pid
#MaxStartups 10:30:100
#PermitTunnel no
#ChrootDirectory none
#VersionAddendum none

# no default banner path
#Banner none

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

# override default of no subsystems
Subsystem       sftp    /usr/lib/openssh/sftp-server

# Example of overriding settings on a per-user basis
#Match User anoncvs
#       X11Forwarding no
#       AllowTcpForwarding no
#       PermitTTY no
#       ForceCommand cvs server

Match Address 192.168.178.0/24
        PasswordAuthentication yes
```
<!--Anmerkung auf Wunsch von Herr Günther: -->
Nach Änderung der Config Neustart des Servers notwendig:

```shell
sudo systemctl restart sshd
```

## Nutzung

### Login auf Remote Shell (Cross-Plattform)

```shell
$ ssh pi@raspberry
```

### Dateitransfer mit Filezilla (Cross-Plattform)

- Server: ``sftp://fqdn.oder.ip``
- Benutzer: auf dem Server existierender Nutzer eingeben
- Passwort analog
- Port: SSH-Port vom Server

im Falle Schlüsselbasiertes Auth:

- Filezilla kann automatisch Putty-Agent "Pageant" nutzen
- alternativ Pfad des priv. Schlüssels unter ``Bearbeiten - Einstellungen - SFTP``

### Dateitransfer mit scp (Commandline)

- vom Localhost zum Server: ``scp virus.exe nutzer@fqdn.oder.ip:/ziel/pfad/``
- vom Server zum Localhost: ``scp nutzer@fqdn.oder.ip:/quell/pfad/virus.exe /ziel/pfad/``

<!--Todo: SSH-Shell, Dateitransfer, VPN (?), SSHFS-->

## Absicherung mit Fail2Ban

- nach best. Anzahl Fehlversuchen wird IP-Adresse in Firewall gesperrt
- 

### Installation

```shell
$ sudo apt install fail2ban
```
<!--selbsterklärend-->

### Konfiguration

Config: `/etc/fail2ban/jail.conf`

```c
ignoreip = 127.0.0.1/8
bantime = 600 # sekunden
findtime = 600 # sekunden
maxretry = 3
destemail = root@localhost
sendername = Fail2Ban
mta = sendmail
```

<!--lediglich relevant: SSH; kann aber noch mehr-->

## VPN mit SSH

<!--es ist wohl möglich, mit SSH VPN Verbindungen zu machen-->
