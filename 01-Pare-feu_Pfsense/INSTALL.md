
# Installation de Pfsense

## Sommaire

1. Prérequis
2. Installation de Pfsense

---

## 1. Prérequis

### A. Matériel

- OS Pfsense FreeBSD
- 1 Go RAM minimum
- 10 Go d'espace minimum
- 1 carte réseau en Bridge
- 1 carte réseau en Réseau Interne sur le réseau LAN_PHARMGREEN
- 1 carte réseau en Réseau Interne sur le réseau DMZ_PHARMGREEN

### B. Autre

- 1 Client avec une carte réseau en Réseau Interne sur le réseau LAN_PHARMGREEN

---

## 2. Installation de Pfsense

Après avoir lancé votre VM, l'affichage de l'assistant d'installation de Pfsense se lance.
- Cliquer sur `Accept`.
- Cliquer sur `Install - Install` pfSense et `OK`.
- Sélectionner `Auto (ZFS)` - `Guided Root-on-ZFS` et cliquer sur `OK`.
- Sélectionner `>>> Install` - `Proceed with Installation`.
- Sélectionner `stripe` - `Stripe - No Redundancy`.
- Appuyer sur espace pour cocher la case `ada0` - `VBOX HARDISK`
- Cliquer sur `YES` pour formater le disque.
- L'installation se lance.
- Une fois l'installation effectuée, un message s'affiche. Cliquer sur Reboot pour relancer la machine.
- Après avoir redémarré, vous retombez sur le même affichage qu'au début avec l'assistant de configuration.  Eteignez la machine en envoyant le signal d'extinction.
- Retirer l'OS du Lecteur Optique sur votre hyperviseur.

---

#### Voilà, vous avez installé Pfsense !