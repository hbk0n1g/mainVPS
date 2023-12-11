# mainVPS
Hauptserver
--> an dem orientieren https://github.com/IvanMurzak/WordPress-VPS/blob/main/README.md

1. Baumstruktur
2. Hauptsystem (VPS)
3. VPS SSH SSHD hardening (HTB Setup)
5. Docker & Docker-compose
6. Nginx Container
7. WireGuard Container
8. Ggf. Shadowsockets
9. C2 installieren (Port und DNS zuordnen!)
10. WordPress Container
11. Datenbanken (redis oder mysql?)
12. SSL
13. Cloud *anbieter raussuchen
14. Ggf. Kubernetes
15. Ggf. RTB Webspace/ -Site
16. FIREWALL EINSTELLEN


1. BAUMSTRUKTUR
   Hauptsystem (dediziert!)
     Ubuntu 22 LTS
     136.244.107.70
     juras.club
       NGINX Container (mit WP abstimmen)
       WireGuard Container (51821)
       C2
       WordPress Container (mit nginx abstimmen)
       DB Container *ggf. mehrere, versch. Funktion
       SSL!
       CLOUD

2. HAUPTSYSTEM & SSH hardening
   ssh als root@IP-VPS
   apt update && upgrade -y
   adduser k0n1g
   usermod -aG sudo k0n1g
   su - k0n1g
   sudo apt update -y && sudo apt full-upgrade -y && sudo apt autoremove -y && sudo apt autoclean -y
   sudo apt install fail2ban -y
   sudo cp /etc/fail2ban/jail.conf /etc/fail2ban/jail.conf.bak
   sudo vim /etc/fail2ban/jail.conf
      darin ganz oben bei [sshd] das 'enabled = true' rauskommentieren (vim dw)
      darunter 'bantime = 4w' und 'maxretry = 3' hinzufuegen
      :wq!
   sudo cp /etc/ssh/sshd_config /etc/ssh/sshd_config.bak
   sudo vim /etc/ssh/sshd_config (HTB einstellungen!)
      das hier kann ansonsten fies schief gehen!
   sudo apt install libpam-google-authenticator -y
      siehe HTB Anleitung, sonst lesen und entscheiden
   google-authenticator
      schritten folgen, emergency scratch unbedingt aufschreiben
   sudo cp /etc/pam.d/sshd /etc/pam.d/sshd.bak
   sudo vim /etc/pam.d/sshd
      rauskommentieren mit # -> @include common-auth
      unten hinzufuegen ->
         auth required pam_google_authenticator.so
         auth required pam_permit.so
         ESC :wq!
   sudo vim /etc/ssh/sshd_config
      unten hinzufuegen ->
         AuthenticationMethods publickey,keyboard-interactive
            DAS HIER HAUT IRGENDWIE NICHT HIN!
               Auf JEDEN FALL!!! einfach sehr genau lesen, verstehen und entsprechend einrichten
         PasswordAuthentication no
4. DOCKER & DOCKER-COMPOSE
   AAAAAAAAA
   2
   3h
