# SYSTEME & RESEAUX

## 1 - Le réseau, c’est quoi ?

### Pour vous, qu’est ce qu’un réseau ?

Un réseau est un ensemble d'entités reliées/interconnectées/communicants les unes aux autres permettant l’échange de données et le partage de ressources communes.

### Quel est le lien entre la notion de réseau et Internet ?

Le lien entre eux réside dans leur définition: un réseau est une connexion d'une ou plusieurs entités (ordinateurs...) placées dans un environnement, et Internet est la relation entre des ordinateurs qui les connectent du monde entier.

La différence entre eux, en termes simples, le réseau est un ensemble d'appareils qui peuvent communiquer entre eux, tandis qu'Internet est un ensemble de réseaux qui peuvent communiquer entre eux.

Source : https://fr.gov-civil-braga.pt/firefox-quantum-vs-google-chrome-quick-comparison-2020

### Quelle est la différence entre Internet et le Web ? Ou a-t-il été inventé ? (Tips : c’est pas si loin d'où vous êtes )

Le Web est un ensemble d’informations, tandis qu’Internet est le réseau informatique qui permet de les transporter. Internet existait avant le Web, et proposait bien d’autres services, qui fonctionnent toujours aujourd’hui (mail, news, ftp…).

En bref :<br>
- Internet est l’infrastructure de réseaux sur laquelle repose le web et d’autres applications. Pour y avoir accès, il faut une connexion à internet.
- Le web est une des applications d’internet, et de ce fait, est totalement dépendant de lui. Il permet, grâce à un navigateur et à des liens hypertexte, de naviguer entre des sites ou des pages web.

Le Web a été inventé au CERN par Tim Berners-Lee.

Source : 
- https://interstices.info/idee-recue-web-et-internet-cest-la-meme-chose/#:~:text=On%20confond%20souvent%20Internet%20et,qui%20permet%20de%20les%20transporter.
- https://www.cyberpreventys.com/conseils-informatique-cybersecurite/difference-internet-web/


### Quels sont les différents types de réseaux informatiques ? Pour chaque type de réseau, donner un exemple concret.

- Le PAN (ex : 2 appareils connectés en Bluetooth, USB, FireWire...)
- Le LAN (ex : Plusieurs appareils connectés sur un même WiFi/réseau local)
- Le MAN
- Le WAN
- Le GAN (ex: Internet)

Source : https://www.infoexpress.fr/quels-sont-les-differents-reseaux-informatiques/


### Quels sont les principaux équipements physiques d’un réseau LAN?
- Un routeur pour la connectivité Internet.
- Des bornes wifi.
- Des cables ethernet.
- Des Serveurs.
- Des PC.
- Des portables.
- Et des switchs.

Source : https://blog.netwrix.fr/2019/07/24/tout-ce-quil-faut-savoir-sur-les-equipements-reseau/


### Qu’est ce que la commande ping ? A quoi sert-elle ?

Dans une très grande majorité des cas, la commande ping sert à tester la communication entre deux équipements connectés à un réseau IP, mais la commande ping peut servir à d'autres choses. Voici une liste de trois cas courants de l'utilisation du ping :

- Tester la communication entre deux équipements connectés à un réseau
- Mesurer la fiabilité d'un réseau à un instant t
- Mesurer la latence d'un réseau à un instant t

ping google.com<br>
ping 192.0.2.255<br>
ping 172.217.20.174

Pour chaque commande on a :<br>
64 bytes from IP: icmp_seq=1 ttl=117 time=12.0 ms<br>
- 64 bytes from IP -> C'est le message qui prouve l'hôte distant a répondu.
- icmp_seq -> indique le nombre de paquets envoyés
- ttl=117 -> TTL signifie Time To Live, ce qui correspond à la durée de vie du paquet avant qu'il ne soit détruit. En fait, lorsqu'un ping est émit il y a une valeur initiale pour le TTL qui est généralement fixée à 64 (ou 128). A chaque fois que le paquet va passer au travers d'un routeur, le TTL sera réduit de 1. Lorsque l'on voit un TTL=56, on peut en déduire que le paquet a traversé 8 routeurs avant d'atteindre sa cible : ce n'est pas étonnant puisque 1.1.1.1 correspond à l'adresse IP du DNS CloudFlare, sur Internet.
- time=12.0 ms -> Le temps nécessaire pour que le paquet puisse atteindre l'hôte distant (IP) et faire le chemin retour pour revenir à notre machine. Ce temps est toujours exprimé en millisecondes.

Source :
- https://www.it-connect.fr/le-ping-pour-les-debutants/
- https://www.ibm.com/docs/fr/power9?topic=commands-ping-command


## 2 — Création d’un réseau entre un PC et un serveur

### Quelles sont les machines / types de machines qui vont intervenir dans ce réseau ?

Les machines / types de machines qui vont intervenir dans ce réseau sont :
- Un Routeur 
- Un PC
- Un Serveur

### Quel type de support de communication choisir ? (câble cuivre, fibre optique, Sans-fil…) ?

Pour notre cas, il serait plus judicieux d'utiliser un support de communication guidée, soit avec un câble.<br>
Comme ici nous sommes sur un environnement locale, on peut utiliser un câble cuivre ou une fibre optique pour une meilleure performance.

Les supports de communication/transmission guidées :
- les câbles en cuivre :
- la fibre optique : 

Les supports de communication/transmissions non-guidées : 
Ce sont toutes les technologies sans-fils type WiFi, Bluetooth ...

Source : https://fr.wikibooks.org/wiki/Les_r%C3%A9seaux_informatiques/Les_supports_de_transmission

### Comment les machines sont identifiées au sein d’un réseau ?
#### Qu’est ce qu’une interface réseau ?

Il s'agit du point de connexion entre deux réseaux. C'est la partie qui assure la connexion entre un terminal utilisateur et un réseau (public ou privé).

#### Qu’est ce qu’une adresse MAC ?

https://www.noodo-wifi.com/faq/adresse-mac/ <br>
L'adresse MAC (Media Access Control) est l'adresse physique d'un périphérique réseau. <br>
Une adresse MAC est sensée être unique au monde. C'est une sorte de plaque d'immatriculation d'un appareil électronique.<br>
Elle peut être modifiée dans certains cas mais c'est assez rare car elle est activée dès la fabrication en usine. <br>
L'adresse MAC se présente sous la forme suivante : XX.XX.XX.XX.XX.XX <br>
Les 12 caractères sont des aplhanumériques de 0 à 9 et de A à F. <br>
Les 6 premiers chiffres permettent d'identifier le fabricant de l'appareil.

#### Qu’est ce qu’une adresse IP ? Comment peut-on la paramétrer ?

L'adresse IP (Internet Protocol) est un numéro d'identification unique attribué de façon permanente (ou provisoire) à chaque périphérique faisant partie d'un réseau informatique utilisant l'Internet Protocol.<br>
L'adresse IP est à l'origine du système d'acheminement (le routage) des paquets de données sur internet.
Il existe deux grandes versions d'adresses IP :

IPV4 (IP Version 4) : codée en 32 bits.<br>
C'est la plus utilisée, généralement représentée en notation décimale avec 4 nombres compris entre 0 et 255, séparés par des points.
ex: 181.174.87.53<br>
IPV6 (IP Version 6) : codée en 128 bits.<br>

```
Explication de l'adresse IP :
L'IPV4 est codée en 32 bits.
C'est à dire que les 4 séries de nombres représentent un total de 32 bits.
Donc : 181.174.87.53 représente une série de : <[8 bits] . [8 bits] . [8 bits] . [8 bits]>
```

Source :
https://fr.wikipedia.org/wiki/Adresse_IP

### Comment tester la bonne configuration et la communication entre deux machines (Dans la vraie vie et pas sur Cisco Packet Tracer) ?

Tout simplement en utilisant la commande PING suivi de l'adresse IP de l'entité ou le nom de domaine si on veut communiquer avec un site.

Exemple : ping google.com ou ping 172.217.20.174


## 3 — Ajout d’un PC au réseau

### Ajouter une carte réseau supplémentaire à votre serveur. Quel est le problème avec cette solution ?

La carte réseau est installée sur la carte mère. Le problème est que l'on doit manipuler sur la carte mère du serveur si on veut en ajouter un nouveau. C'est une opération assez délicate car si durant l'opération on endommage la carte mère, le serveur ne fonctionnera plus.

Le problème est qu'une carte réseau a également un nombre limité de ports RJ45. S'il y avait un nombre d'appareils plus élevés que le nombre de ports contenu par la carte réseau on reviendrait au problème de base.

Source : https://www.inmac-wstore.com/guides-achat-composants-definition-role-carte-reseau/cp37684.htm

### Ajouter un équipement d’interconnexion à votre réseau. Mais quel équipement choisir pour effectuer cette interconnexion.

Il faudra dans ce cas ajouter un Switch.

Un Switch est se présente sous la forme d’un boîtier doté de ports Ethernet RJ45. Le nombre de ports peut aller d’un faible nombre (4, 5, 10, 20, etc.) à plusieurs centaines pour les structures importantes (centres d’affaires, salles de serveurs informatiques, etc.).

Ainsi, cette solution matérielle assure la communication, la réception et la redistribution de messages, entre les différents ordinateurs et serveurs d’un même réseau. Contrairement à un hub, le switch opte pour une répartition « intelligente » de l’information. En se basant sur une table d’adressage (adresse MAC et port), il va ainsi redistribuer l’information uniquement aux appareils informatiques concernés. À l’inverse, un hub transmet la donnée à l’ensemble des appareils actifs sur le réseau local.

Source : https://talice.com/actualites/quest-ce-quun-switch


## 4 — Connexion avec une autre entreprise

### Soit l’adresse réseau suivante : 192.168.1.0
#### ◆ Quel est son masque ?
Son masque est 255. 255. 255. 0
#### ◆ Combien d'adresses IP peut-on attribuer dans ce réseau. Attention, il y a un piège : faite une recherche sur l’adresse IP de broadcast
- 192.168.1.0 --> correspond à l'adresse réseau
- 192.168.1.255 --> correspond à l'adresse IP de broadcast --> on utilisera cette adresse lorsque l'on voudra communiquer des données à chaque entités du réseau

La partie de l'IP qui identifie la machine est celle après le dernier "point", on peut lui attribuer une valeur entre 0 et 255 (0 inclus) donc 256 valeurs car ici on utilise la version IPV4 qui s'écrit sur 4 octets en décimal (XXX.XXX.XXX.XXX) où 1 octets vaut 8 bits donc 2^8 = 256.

Cependant, l'adresse réseau et l'adresse de broadcast sont déjà occupées. Cela veut donc dire que l'on pourra attribuer 254 (256 - 2) adresse IP dans ce réseau.

### Soit les adresses ip suivantes : 192.168.1.1/24 et 192.168.24.3/24
#### ◆ Sont-elles sur le même réseau ?
Non ces adresses IP ne sont pas sur le même réseau. On peut le voir à l'aide de leur **masque** qui est le nombre après le "/" ici 24.<br>
Ce "24" signifie que les **24 premiers bits** correspondent à la partie de l'IP qui identifie le réseau, autrement dit **l'adresse réseau**<br>
**Explication :** Ici on utilise la version IPV4 qui s'écrit sur 4 octets en décimal (XXX.XXX.XXX.XXX) et où 1 octets = 8 bits. La somme totale de tous les bits est égale à 32 bits (8 x 4 = 32).<br>
Comme les adresses ci-dessus ont un **masque de 24 bits**, cela veut dire que les **3 premiers octets donc les 24 premiers bits** correspondent à **l'adresse réseau**, et **les 8 derniers bits permettent d'identifier la machine**.

#### ◆ Quelles sont les adresses réseaux respectives ?

Les adresses réseaux respectives sont :
- 192.168.1.0
- 192.168.24.0


## 5 —Lien avec les modèles théoriques : OSI et TCP/IP

### Modèle OSI

#### ➔ Faites une recherche sur le modèle OSI et lister ces différentes couches. Pour chaque couche, faites une courte description de ce qu’elle représente et donnez un élément qui peut être associé à cette couche.

Le **Modèle Open Systems Interconnection (OSI)** fournit une norme permettant à différents systèmes informatiques de communiquer entre eux.

Le **modèle OSI** peut être considéré comme un *langage universel pour la **mise en réseau d’ordinateurs**. La base du concept est de diviser un système de communication en **sept couches** abstraites, chacune empilée sur la dernière.<br>
Chaque couche du modèle OSI assure un rôle particulier et communique avec les couches au-dessus et en dessous d'elle.

Les voicis :
- 7 - **La couche applicative:**<br>
  C’est la seule couche qui interagit directement avec les données de l’utilisateur. Les applications logicielles comme les navigateurs web et les clients e-mail se servent de la couche applicative pour initier des communications. Néanmoins ces applications ne font pas parties de la couche, ils sont distincts.<br>
  Cette couche est en fait responsable des protocoles et de la manipulation des données sur lesquels le logiciel s’appuie pour présenter des données significatives à l’utilisateur.<br>
  Les protocoles de la couche applicative incluent HTTP et SMTP (Simple Mail Transfer Protocol est l’un des protocoles permettant les communications par courrier électronique). 
- 6 - **La couche de présentation:**<br>
  Cette couche est principalement responsable de la préparation des données afin qu’elles puissent être utilisées par la couche applicative ; en d’autres termes, la couche 6 rend les données présentables pour les applications. La couche de présentation est responsable de la traduction, du chiffrement et de la compression des données.<br>
  cf. lien source pour + de détails
- 5 - **La couche de session:**<br>
  Il s’agit de la couche responsable de l’ouverture et de la fermeture de la communication entre les deux appareils. L’intervalle entre l’ouverture et la fermeture de la communication est appelé session. La couche de session garantit que la session reste ouverte suffisamment longtemps pour transférer toutes les données échangées, puis ferme rapidement la session afin d’éviter le gaspillage de ressources.<br>
  cf. lien source pour + de détails
- 4 - **La couche de transport:** <br>
  La couche 4 est responsable de la communication de bout en bout entre les deux appareils. Cela inclut la récupération de données de la couche de session et leur décomposition en morceaux appelés segments avant de les envoyer à la couche 3. La couche de transport sur le dispositif de réception est chargée de réassembler les segments en données que la couche de session peut consommer.<br>
  cf. lien source pour + de détails
- 3 - **La couche réseau:**<br>
  La couche réseau est chargée de faciliter le transfert de données entre deux réseaux différents. Si les deux périphériques en communication sont sur le même réseau, la couche réseau est inutile. La couche réseau divise les segments de la couche transport en unités plus petites, appelées paquets, sur le périphérique de l'expéditeur et réassemble ces paquets sur le périphérique récepteur. La couche réseau trouve également le meilleur chemin physique pour que les données atteignent leur destination ; c'est ce qu'on appelle le routage.

  Les protocoles de la couche réseau sont IP, ICMP (Internet Control Message Protocol), IGMP (Internet Group Message Protocol), et la suite IPsec .
- 2 - **La couche de liaison de données:** <br>
  La couche liaison est très similaire à la couche réseau, sauf que la couche liaison facilite le transfert de données entre deux périphériques sur le même réseau. La couche liaison prend les paquets de la couche réseau et les divise en fragments plus petits appelés images. A l'instar de la couche réseau, la couche liaison est également responsable du contrôle des flux et des erreurs dans les communications intra-réseau (la couche transport n’effectue que le contrôle des flux et des erreurs pour les communications inter-réseaux).
- 1 - **La couche physique:** <br>
  Cette couche inclut les équipements physiques impliqués dans le transfert de données, tels que les câbles et les commutateurs. C'est également la couche où les données sont converties en une séquence binaire, qui est une chaîne de 1s et de 0s. La couche physique des deux périphériques doit également convenir d'une convention de signal afin que les 1s puissent être distinguées des 0s sur les deux périphériques.

#### ➔ En quoi ce modèle est important?
L’Internet moderne ne suit pas strictement le modèle OSI (il suit plutôt la suite simplifiée de protocoles Internet), mais ce modèle reste très pratique pour dépanner les problèmes réseau. Si une personne ne peut pas connecter son ordinateur portable à Internet, ou si un site Web est neutralisé pour des milliers d’utilisateurs, le modèle OSI peut aider à résoudre le problème et en isoler la source. Si le problème peut être réduit à une couche spécifique du modèle, beaucoup de travail inutile peut être évité.

Source : https://www.cloudflare.com/fr-fr/learning/ddos/glossary/open-systems-interconnection-model-osi/


### Modèle TCP/IP

#### ➔ Qu’est ce que TCP et IP ?
#### ➔ Décrivez les couches qui le composent
#### ➔ Faites le lien avec le modèle OSI

Source : <br>
- https://www.frameip.com/tcpip/
- https://www.cloudflare.com/fr-fr/learning/ddos/glossary/tcp-ip/


## Service DNS

### 1 - Un service DNS, c’est quoi ?

Pour comprendre ce qu’est un service DNS, rendez vous sur :<br>
- https://cours-systemes-reseaux.williamburillon.com/#/c/dns .
- https://developer.mozilla.org/fr/docs/Learn/Getting_started_with_the_web/How_the_Web_works

#### Livrables : PC10 veut envoyer un ping à PC11
➔ Quel est l’ordre des actions (Requête/Réponse DNS, ping) effectuées pour
réaliser cette tâche ? Attention : le PC10 ne connaît pas l’adresse IP de PC11.

En reprenant le schéma du livrable, l’ordre des actions sera le suivant :<br>
ping → requête/réponse DNS

Explication :<br>
- PC 10 va effectuer un ping, le ping contient le nom de PC11 mais pas l’IP (c’est impossible de faire une requête entre 2 machines juste avec le nom sans l’adresse IP)
- Le ping va donc passer par le Switch pour d’abord se diriger vers le Serveur DNS.
- Le Serveur DNS va permettre de faire l’association entre le nom de la machine et son adresse IP (en gros elle traduit le nom en IP).
- Après avoir fait l’association, il renvoie cette information au PC10.
- PC10 a donc désormais l’adresse IP de PC11 et peut donc communiquer sa requête avec PC11


### 2 — Déployez et configurez un serveur DNS sur Cisco Packet Tracer
cf.google-drive


### 3 — Configurer un record DNS avec Cloudflare

#### ➔ Faites une recherche sur les principes de base des noms de domaine afin de comprendre ce qu’est un sous-domaine

**Nom de domaine :**<br>
Un nom de domaine (souvent appelé simplement domaine) est un nom facilement mémorisable associé à une adresse IP physique sur Internet. Il s'agit du nom unique qui apparaît après le signe @ dans les adresses e-mail, et après www. dans les adresses Web. Par exemple, le nom de domaine example.com peut être associé à l'adresse physique 198.102.434.8. "google.com" et "wikipedia.org" sont deux autres exemples de noms de domaine.Le fait d'utiliser un nom de domaine, plutôt qu'une adresse IP numérique, pour identifier un emplacement sur Internet facilite grandement la mémorisation et la saisie des adresses Web.

**Sous-domaine :**<br>
Un sous-domaine est un domaine appartenant à un domaine plus important. Par exemple, "mail.google.com", "www.google.com" et "docs.google.com" sont tous des sous-domaines de "google.com". Les propriétaires de domaines peuvent créer des sous-domaines pour attribuer des adresses facilement mémorisables aux pages Web ou aux services au sein de leur domaine de premier niveau.

Source : https://support.google.com/a/answer/2573637?hl=fr

#### ➔ Une explication des différents types d’enregistrement DNS

Il existe plusieurs types d’enregistrements DNS dont les plus courants sont :<br>
- A : Permet de faire la correspondance entre un nom DNS et une adresse IP (ipv4)
- AAAA : Permet de faire la correspondance entre un nom DNS et une adresse IP (ipv6)
- CNAME : Permet de faire la correspondance entre deux noms DNS
- MX : Permet de configurer les serveurs de mails pour une zone DNS donnée
- TXT : Cet enregistrement permet de stocker une chaîne de 1024 caractères au maximum
- SRV: Cet enregistrement sert à indiquer quel est le serveur qui gère un service spécifique tel que la messagerie instantanée, SIP, etc

Source : https://help.adk-media.com/quels-sont-les-differents-type-enregistrements-dns.html

#### ➔ Un screenshot de votre enregistrement DNS dans Cloudflare
cf. googledrive + livrable

#### ➔ Un screenshot de votre site web qui affichera votre nom
cf. googledrive + livrable


## Protocole HTTP

### - Qu’est ce qu’une API (et plus spécifiquement une API REST) ?
### - Qu’est ce que le protocole HTTP ?
### - Quelles sont les méthodes disponibles avec le protocole HTTP ?
### - Quelle est la différence entre le protocole HTTP et le protocole HTTPS ?
### - Qu’est ce qu’un Bearer token ?
