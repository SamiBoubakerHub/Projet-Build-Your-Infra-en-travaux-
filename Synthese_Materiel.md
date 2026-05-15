
| **Nom**  | **OS**                  | **Fonctions Principales**                | **Adresses, CIDR**                                                                      | **Disques**                                                                                                                               | **RAM** |
| -------- | ----------------------- | ---------------------------------------- | --------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------- | ------- |
| FW01     | pfSense                 | Filtrage Réseau, Routeur, Accès Internet | **WAN :** 192.168.0.17/24 <br>**LAN :** 172.16.10.254/24 <br>**DMZ :** 172.16.20.254/24 | **Nombre :** 1 <br>**Taille Totale :** 13 Go <br>**Espace Libre (en Go) :** 817 Mo <br>**Espace Libre (en %) :** 6 %<br>                  |         |
| SRVWIN01 | Windows Server 2022     | Active Directory, DNS, DHCP              | 172.16.10.10/24                                                                         | **Nombre :** 1 <br>**Taille Totale :** 50 Go <br>**Espace Libre (en Go) :** 29 Go <br>**Espace Libre (en %) :** 57 %                      |         |
| SRVWIN04 | Windows Server 2022     | WSUS                                     | 172.16.10.11/24                                                                         | **Nombre :** 2 <br>**Taille Totale :** 60 Go, 100 Go <br>**Espace Libre (en Go) :** 46 Go, 93 Go <br>**Espace Libre (en %) :** 77 %, 93 % |         |
| SRVLX01  | Debian 13.1 Trixie      | Gestion de Parc et de Ticketing GLPI     | 172.16.10.20/24                                                                         | **Nombre :** 1 <br>**Taille Totale :** 20 Go <br>**Espace Libre (en Go) :** 15 Go <br>**Espace Libre (en %) :** 75 %                      |         |
| SRVLX02  | Debian 12.13 Bookworm   | Messagerie iRedMail                      | 172.16.10.21/24                                                                         | **Nombre :** 1 <br>**Taille Totale :** 20 Go <br>**Espace Libre (en Go) :** 14 Go <br>**Espace Libre (en %) :** 70 %                      |         |
| IPBX01   | FreePBX 16              | VoIP                                     | 172.16.10.30/24                                                                         | **Nombre :** 1 <br>**Taille Totale :** 16 Go <br>**Espace Libre (en Go) :** 11 Go <br>**Espace Libre (en %) :** 66 %                      |         |
| SRVWEB01 | Debian 12.13 Bookworm   | Web Externe                              | 172.16.20.10/24                                                                         | **Nombre :** 1 <br>**Taille Totale :** 10 Go <br>**Espace Libre (en Go) :** 7 Go <br>**Espace Libre (en %) :** 30 %                       |         |
| CLIENT01 | Windows 10 Professionel | Client                                   | *DHCP*                                                                                  | **Nombre :** 1 <br>**Taille Totale :** 40 Go <br>**Espace Libre (en Go) :** 11 Go <br>**Espace Libre (en %) :** 27 %                      |         |
| CLIENT02 | Windows 10 Professionel | Client                                   | *DHCP*                                                                                  | **Nombre :** 1 <br>**Taille Totale :** 40 Go <br>**Espace Libre (en Go) :** 22 Go <br>**Espace Libre (en %) :** 55 %                      |         |


ipb 2 50% lx1 512 50 % lx2 2.5 80% web 512 17 % win4 6 65 % win1 4 63 % fw 1 25 %

cli1 11/40 27% 3 57%  cli2 1 22/40 55% 3 57 %





















