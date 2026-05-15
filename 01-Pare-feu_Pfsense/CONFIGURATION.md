
# Configuration de Pfsense

## Sommaire

1. Configuration CLI de Pfsense
2. Configuration WebGUI de Pfsense

---
## 1. Configuration CLI de Pfsense

### A. Configuration de l'interface LAN

Relancer votre machine avec Pfsense installé, et après chargement, vous arrivez devant un menu.
Nous allons entamer une première configuration de la machine pour pouvoir se connecter sur une machine client en WebGUI, ce qui facilitera les manipulations à venir.
- Taper 2 pour configurer les interfaces déjà existantes, `2) Set interface(s) IP address`.
- Vous devriez avoir deux interfaces déjà affichées : 
```
Available interfaces:

1 - WAN (em0 -dhcp, dhcp6)
2 - LAN (em1 - static) 
```
- Choisir l'interface LAN en tapant 2.
- Taper `n` pour ne pas configurer l'interface automatiquement.
- Saisir l'adresse IP préalablement choisi pour le LAN qui est affiché dans le [Tableau Récapitulatif](00-Preparation/Tableau_Recapitulatif_Elements_du_Reseau), donc ici `172.16.10.254`.
- Saisir le masque de sous-réseau, ici 255.255.255.0 et donc `24`.
- Appuyer sur Entrée concernant la prochaine question.
- Taper `n` pour ne pas configurer une adresse IPv6 via DHCP6.
- Appuyer sur Entrée concernant la prochaine question.
- Taper sur `y` pour activer le service DHCP sur le réseau LAN, nous en aurons besoin pour accéder à la configuration WebGUI sur la machine client. Service que l'on désactivera une fois que le DHCP sera mis en place sur le serveur dédié.
- Taper la première adresse IP de la plage d'adresse IP auxquelles les machines connectées sur le réseau pourront se faire attribuer une configuration IP. Ici, `172.16.10.100`.
- Taper ensuite la dernière adresse IP de la plage d'adresse IP. Ici, `172.16.10.200`.
- Taper ensuite `y` pour activer le protocole HTTP et donc pour pouvoir accéder à la configuration avec une adresse http.
- Appuyer sur Entrée pour continuer.
  
#### Vous avez configuré votre interface LAN et mis en place une attribution (temporaire) de configuration IP sur le réseau LAN !

---

### B. Configuration de l'interface DMZ

Nous allons continuer la configuration des interfaces en continuant avec celle que l'on appellera DMZ. Mais elle n'a pas été assignée pour l'instant, et donc, elle est désactivée.
- De retour au menu, taper sur 1 pour sélectionner l'option `1) Assign Interfaces`.
- Taper `n` à la prochaine question, car nous n'aurons pas besoin de configurer des VLANs.
- Saisir `em0`, pour l'assigner à l'interface WAN.
- Saisir `em1`, pour l'assigner à l'interface LAN.
- Saisir `em2`, pour l'interface optionnelle qui celle qui correspond au DMZ, qui s'appellera pour l'instant OPT1.
- Taper `y` pour continuer après avoir vérification de la configuration des interfaces.
L'interface DMZ est activée mais n'a pas encore le nom voulu et une configuration viable.  Pour ce faire, nous allons effectuer exactement la même étape que pour la configuration IP de l'interface LAN. Mais concernant le nom, nous le ferons plus tard en graphique.
- Taper 2 pour `2) Set interface(s) IP address`.
- Taper 3 pour choisir `OPT1`.
- Taper `n` pour ne pas attribuer de configuration IP via DHCP.
- Saisir l'adresse IP préalablement choisi pour le DMZ qui est affiché dans le [Tableau Récapitulatif](00-Preparation/Tableau_Recapitulatif_Elements_du_Reseau), donc ici `172.16.20.254`.
-  Saisir le masque de sous-réseau, ici 255.255.255.0 et donc `24`.
- Appuyer sur Entrée concernant la prochaine question.
- Taper `n` pour ne pas configurer une adresse IPv6 via DHCP6.
- Appuyer sur Entrée concernant la prochaine question.
- Taper sur `n` pour ne pas configurer une attribution automatique de configuration IP via DHCP.
- Appuyer sur Entrée concernant la prochaine question.
  
#### Vous avez activé et configuré votre interface DMZ (OPT1 pour l'instant) !

---

## 2. Configuration WebGUI de Pfsense
  
Nous allons maintenant rentrer dans le vif du sujet. Nous allons effectuer la configuration initiale de pfsense, renommer le nom provisoire OPT1 initialement prévu pour l'interface DMZ et établir des règles de filtrage réseau, des règles d'autorisation et de blocage.

---
### A. Connexion et configuration initiale de Pfsense en WebGUI

Pour cela, on va laisser la machine pfsense de côté, tout en la laissant allumer car nous allons configurer pfsense via une autre machine, une machine client de préférence.
Avant de mettre en route la machine client, bien vérifier qu'il n'y a qu'une seule carte réseau et qu'elle est configurée en Réseau Interne avec le nom LAN_PHARMGREEN.
- Démarrer votre machine client.
- Vérifier que le paramétrage IPv4 est bien sélectionné en DHCP, attribution automatique de configuration IP.
- Ouvrir un Navigateur Web.
- Taper l'adresse IP de l'interface LAN configurée précédemment avec `http://` avant cette dernière dans la barre d'adresse du navigateur, donc ici http://172.16.10.254.
- Vous arrivez devant la page de connexion pfsense.
- Saisir `admin` dans le champ "Username" et `pfsense` dans le champ "Password". C'est la session administrateur à laquelle se connecter et le mot de passe est celui par défaut. Il faudra le changer pour plus de sécurité après la configuration initiale.
- Comme c'est la première connexion du pare-feu en WebGUI, vous arriverez sur l'assistant de configuration. Vous arrivez sur la page de bienvenue. Cliquer sur Next.
- Cliquer sur Next sur la page "Netgate® Global Support is available 24/7".
- Vous arrivez sur la page "General Information". Changer le hostname pfSense en **FW01**. Changer le domaine home.arpa en **tssr.lan**. Saisir **1.1.1.1** dans le champ "Primary DNS Server" et **8.8.8.8** dans le champ "Secondary DNS Server", les adresses DNS saisies correspondent respectivement à celles de Clouflare et de Google. Lancer ensuite la case "Override DNS" cochée et cliquer sur Next.
- Sélectionner Europe/Paris dans le champ "Timezone" de la page "Time Server Information".
- Sur la prochaine page, "Configure WAN Interface", vérifier si le DHCP est bien sélectionné et décocher les paramètres "Block RFC1918 Private Networks" et "Block bogon networks" situés tout à fait en bas de la page. Cliquer sur Next.
- Page "Configure LAN Interface". Vérifier si l'adresse IP et le masque de sous-réseau dans les champs "LAN IP Address" et "Subnet Mask" sont bien ceux voulus. Cliquer sur Next.
- Page "Set Admin WebGUI Password". Changer le mot de passe de la session admin. Cliquer sur Next.
- Cliquer sur Reload sur la page qui suit.
- Après chargement d'une page précédente, vous devriez arriver à la page "Wizard completed." où un message de félicitations vous est adressé vous confirmant que la configuration initiale de pfsense est terminée. Vous pouvez cliquer sur Check for updates pour vérifier s'il y a des mises à jour plus récentes sinon cliquer sur Finish.
- Vous arrivez sur le tableau de bord, le "dashboard" avec un popup de conditions de droits et d'utilisation. Cliquer sur Accept et Close.
  
  #### Vous avez terminé la configuration initiale de votre pare-feu Pfsense !

---

### B. Changement de nom de l'interface DMZ

Sur le dashboard, on peut voir plusieurs fenêtres, des "widgets" plutôt utiles qui nous permet d'obtenir des informations sur le système, les disques et les interfaces.
- Descendre jusqu'au widget "Interfaces" et cliquer sur "OPT1".
- On arrive dans la configuration de l'interface censé être le DMZ. Saisir "DMZ" à la place d'OPT1 dans le champ "Description".
- Vérifier si l'adresse IP et le masque de sous-réseau est bien celui souhaité dans la partie "Static IPv4 Configuration".
- Cliquer sur Save.
- Cliquer ensuite sur Apply Changes.

#### Voilà, vous avez enfin pu mettre le vrai nom de votre interface DMZ !

---

### C. Configuration des règles du pare-feu

Nous allons maintenant établir des règles de passage au pare-feu sur le réseau LAN et le réseau DMZ pour augmenter la sécurité et mettre en place un filtrage réseau viable.
- Dans les onglets en haut, cliquer sur "Firewall" et "Rules".
- On arrive sur une page consacré aux règles de pare-feu mais sur la partie WAN, or, c'est la partie LAN qui nous intéresse et non WAN. Cliquer sur l'onglet LAN.
On constate qu'il y a déjà 3 règles présentes :
- Anti-Lockout Rule : Règle système qui permet d'éviter de perdre l'accès à l'interface Web de pfsense depuis le LAN.
- Default allow LAN to any rule : Règle par défaut qui permet un accès ouvert du réseau LAN vers l'extérieur sur tous les ports en IPv4.
- Default allow LAN IPv6 to any rule : Règle par défaut qui permet un accès ouvert du réseau LAN vers l'extérieur sur tous les ports en IPv6.
Ce sont les règles établies par défaut par Pfsense. Mais elles représentent une grosse faille de sécurité. Pour ce faire, nous allons créer d'autres règles avant de désactiver ces dernières.
Nous allons ajouter 6 règles : 
- Une règle d'autorisation pour le protocole DNS.
- Une règle d'autorisation pour le protocole HTTP.
- Une règle d'autorisation pour le protocole HTTPS.
- Une règle d'autorisation pour le protocole ICMP.
- Une règle d'autorisation pour le protocole SSH.
- Une règle de blocage pour 
- Cliquer sur Add (flèche vers le haut) pour ajouter une nouvelle règle.