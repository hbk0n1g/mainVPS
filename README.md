# mainVPS
Hauptserver
--> an dem orientieren https://github.com/IvanMurzak/WordPress-VPS/blob/main/README.md

1. Baumstruktur
2. Funktion
3. Hauptsystem (VPS)
4. VPS hardening
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
   -Hauptsystem (dediziert!)
     -Ubuntu 22 LTS
     -136.244.107.70
     -juras.club
       -NGINX Container (mit WP abstimmen)
       -WireGuard Container (51821)
       -C2
       -WordPress Container (mit nginx abstimmen)
       -DB Container *ggf. mehrere, versch. Funktion
       -SSL!
       -CLOUD

   
       
