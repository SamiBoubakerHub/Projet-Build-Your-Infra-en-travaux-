# Projet 3 : Build Your Infra
---
## TSSR-1025-P3-G8
---

![Image_de_présentation](Ressources/Logo_Pharmgreen.png)

## Sommaire
---
- [Présentation du Projet](#presentation-du-projet)
- [Contexte](#contexte)
- [Le Groupe de Projet](#le-groupe-du-projet)
- [Entreprise Ciblée](#entreprise-ciblee)
- [Objectifs](#objectifs)
- [Vue d'Ensemble de l'Infrastructure Réalisée](#vue-densemble-de-linfrastructure-realisee)
- [Organisation de la Documentation](#organisation-de-la-documentation)


## ## Présentation du Projet  

Troisième projet réalisé dans le cadre de la formation TSSR (Technicien Supérieur Systèmes et Réseaux) de l'école Wild Code School, il a pour but d'imaginer et de concevoir une Infrastructure Réseau Centralisée et Sécurisée d'une entreprise fictive.

---
## Contexte

Notre société a été embauchée par l'entreprise Pharmgreen, au sein du département Systèmes d'Information, pour renouveler durablement leur infrastructure réseau centralisée et sécurisée.

---
## Le groupe de Projet

Netwild, société fictive et prestataire de services a été mandatée par l'entreprise Pharmgreen afin d'imaginer, de concevoir et d'établir une infrastructure réseau sécurisée conformément aux demandes de cette dernière.  
Intervenant Technique : Sami Boubaker
DSI : Dominique Colleville

---
## Entreprise Ciblée

Pharmgreen, entreprise lyonnaise comme son fondateur, Gilles Faure, est une pionnière actuelle dans le domaine de la santé grâce à ses dispositifs médicaux innovants d'origine végétale,  répondant ainsi à une demande croissante pour des solutions de santé naturelles et respectueuses de l'environnement. Grâce à des procédés de fabrication innovants et des collaborations avec des experts en botanique et en médecine naturelle, elle s'engage à fournir des produits de haute qualité, bénéfiques à la fois pour les patients et pour la planète.

---
## Objectifs

- Mettre en place un filtrage réseau.
- Mettre en place un domaine Active Directory.
- Centralisation de la gestion des utilisateurs et des machines présentes sur le domaine.
- Mettre en place les services réseaux essentiels DNS et DHCP.
- Mettre en place une Gestion de Parc et de Ticketing.
- Mettre en place une gestion centralisée des mises à jour sur toutes les machines existantes.
- Mettre en place un service de messagerie pour tous les comptes utilisateurs existants.
- Mettre en place un service de téléphonie pour tous les comptes utilisateurs.

---
## Vue d'Ensemble de l'Infrastructure Réalisée

- Un pare-feu conçu avec Pfsense :
	--> Serveur FW01 
- Un domaine Active Directory pour la gestion centralisée des utilisateurs et ordinateurs :
	--> Serveur SRVWIN01
- Des services d'infrastructure dédiés (DNS,DHCP) :
	--> Serveur SRVWIN01
- Un système de Gestion de Parc et de Ticketing (GLPI) :
	--> Serveur SRVLX01
- Une gestion centralisée des mises à jours (WSUS) :
	--> Serveur SRVWIN04
- Un service de messagerie (iRedMail) :
	--> Serveur SRVLX02
- Un service de téléphonie IP (FreePBX) :
	--> Serveur IPBX01

---
## Organisation de la Documentation

Vous trouverez dans la Documentation présente dans les répertoires : 
- un fichier INSTALL pour chaque service.
- un fichier CONFIGURATION pour chaque service.
- un fichier USER_GUIDE pour les services Gestion de Parc, Messagerie et VoIP.
- un répertoire avec tous les fichiers propres à la préparation et à la réalisation du projet.
- un répertoire Ressources.
---