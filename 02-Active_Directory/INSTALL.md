
# Installation d'Active Directory

## Sommaire

1. Prérequis
2. Installation d'Active Directory

---

## 1. Prérequis

### A. Matériel

- OS Windows Server 2022
- 4 Go RAM minimum
- 50 Go d'espace minimum
- 1 carte réseau en Réseau Interne sur le réseau LAN_PHARMGREEN
  
  
### B. Configuration Réseau VM

- Adresse IP Statique : 172.16.10.10
- Adresse DNS : 172.16.10.10
- Adresse Passerelle : 172.16.10.254

---

## 2. Installation d'Active Directory

Après avoir lancé votre VM et s'être connecté sur la session Administrateur avec le mot de passe préalablement saisi pendant l'installation de Windows Server 2022, le Gestionnaire de Serveurs "Server Manager" se lance.
- Cliquer sur `Add roles and features`.
- Continuer en cliquant sur `Next`.
- Sélectionner `Role-based or feature-based installation` et cliquer sur `Next`.
- Sélectionner `Select a server from the server pool`, vérifier que le serveur sélectionné soit celui voulu, ici `SRVWIN01.tssr.lan` avec l'adresse `172.16.10.10` et cliquer sur `Next`.
- Sélectionner `Active Directory Domain Services` et cliquer sur `Next`.
- Cliquer sur `Next` pour les 2 prochaines pages.
- Cliquer sur `Install` pour confirmer l'installation.
- Une fois l'installation terminée, cliquer sur `Close`.

---

#### Voilà, vous avez installé le rôle Active Directory !
#### On peut maintenant passer à la configuration du Serveur AD.


