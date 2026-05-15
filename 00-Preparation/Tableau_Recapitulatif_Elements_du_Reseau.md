
| **Nom**      | **Type** | **OS**       | **Interface** | **Interconnexions**     | **Zone** | **Rôle(s)**                      | **Adresse Réseau** | **Adresse IP** | **Passerelle (Gateway)** |
| ------------ | -------- | ------------ | ------------- | ----------------------- | -------- | -------------------------------- | ------------------ | -------------- | ------------------------ |
| **FW01**     | Pare-Feu | pfSense      | WAN           | Vers Box Internet       | WAN      | Accès Internet / Filtrage Réseau | 192.168.0.0/24     | 192.168.0.17   | 192.168.0.1              |
|              |          |              | LAN           | Vers Switch Virtuel LAN | LAN      | Passerelle par défaut du LAN     | 172.16.10.0/24     | 172.16.10.254  | -                        |
|              |          |              | DMZ           | Vers Switch Virtuel DMZ | DMZ      | Passerelle par défaut de la DMZ  | 172.16.20.0/24     | 172.16.20.254  | -                        |
| **SRVWIN01** | Serveur  | Win Srv 2022 | LAN           | Vers Switch Virtuel LAN | LAN      | Active Directory, DNS, DHCP      | 172.16.10.0/24     | 172.16.10.10   | 172.16.10.254            |
| **SRVWIN04** | Serveur  | Win Srv 2022 | LAN           | Vers Switch Virtuel LAN | LAN      | WSUS                             | 172.16.10.0/24     | 172.16.10.11   | 172.16.10.254            |
| **SRVLX01**  | Serveur  | Debian 13    | LAN           | Vers Switch Virtuel LAN | LAN      | GLPI                             | 172.16.10.0/24     | 172.16.10.20   | 172.16.10.254            |
| **SRVLX02**  | Serveur  | Debian 12    | LAN           | Vers Switch Virtuel LAN | LAN      | Messagerie                       | 172.16.10.0/24     | 172.16.10.21   | 172.16.10.254            |
| **IPBX01**   | Serveur  | FreePBX      | LAN           | Vers Switch Virtuel LAN | LAN      | VoIP                             | 172.16.10.0/24     | 172.16.10.30   | 172.16.10.254            |
| **SRVWEB01** | Serveur  | Debian 12    | DMZ           | Vers Switch Virtuel DMZ | DMZ      | Web Externe                      | 172.16.20.0/24     | 172.16.20.10   |                          |
| **CLIWIN01** | Client   | Win 10       | LAN           | Vers Switch Virtuel LAN | LAN      | Poste Utilisateur                | 172.16.10.0/24     | _DHCP_         | _DHCP_                   |
| **CLIWIN02** | Client   | Win 10       | LAN           | Vers Switch Virtuel LAN | LAN      | Poste Utilisateur                | 172.16.10.0/24     | _DHCP_         | _DHCP_                   |
