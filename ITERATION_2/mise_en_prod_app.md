# MISE EN PRODUCTION D'UNE APPLICATION

## Connection à un serveur distant avec SSH et administration Linux

Source :
- https://www.youtube.com/watch?v=gxQKw7A6qDM --> intro sur le SSH
- https://www.hostinger.fr/tutoriels/ssh-linux --> introduction sur le ssh
- https://doc.ubuntu-fr.org/ssh --> connexion via ssh

### En quoi ça consiste ?
Tout simplement de rendre l'application qui marche uniquement sur votre ordi (en locale) accessible à tout le monde

### SSH c'est quoi ?
SSH, ou Secure Shell, est un protocole d’administration à distance qui permet aux utilisateurs de contrôler et de modifier leurs serveurs distants sur Internet.

### Quels sont les protocoles qui ont été remplacés par SSH ?
Les protocoles qui ont été remplacés par SSH sont le TELNET (non chiffré) ainsi que le FTP.

Le protocole SSH, utilise des techniques cryptographiques pour s’assurer que toutes les communications vers et depuis le serveur distant se produisent de manière chiffrée, et donc apporte plus de sécurité lors de l'administration de serveurs distants. <br>
Il fournit un mécanisme pour authentifier un utilisateur distant, transférer les entrées du client vers l’hôte et relayer la sortie vers le client.

### Quelles sont les différents modes d’utilisation de SSH (notamment au niveau de la sécurité) ?

Les différents modes d'utilisation de SSH sont :
- authentification par mot de passe
- authentification par clé publique / privée

**A retenir** : L’avantage important offert par SSH par rapport à ses prédécesseurs est l’utilisation du cryptage pour assurer le transfert sécurisé d’informations entre l’hôte et le client

### Comprendre différentes techniques de cryptage utilisées par SSH

#### Cryptage symétrique
https://www.it-connect.fr/les-cles-symetriques/

#### Cryptage asymétrique
https://www.it-connect.fr/les-cles-asymetriques/

#### Hashing
voir source

### Comment est établie une connection SSH entre un client et un serveur avec la méthode la plus sécurisé (faites un schéma)

![img.png](img.png)

### Liste de commandes Linux
Source :
https://www.hostinger.fr/tutoriels/commandes-linux

| Catégorie                                                                                                              | Ligne de commande |
|------------------------------------------------------------------------------------------------------------------------|:-----------------:|
| Affiche les fichiers et folders                                                                                        |        ls         |
| Change de répertoire courant                                                                                           |        cd         |
| Trouver le chemin de votre répertoire de travail actuel                                                                |        pwd        |
| Copier des fichiers ou des folders et leur contenu                                                                     |        cp         |
| Créer un folder                                                                                                        |       mkdir       |
| Créer un fichier                                                                                                       |       touch       |
| Déplacer et renommer des fichiers et folders                                                                           |        mv         |
| Affichage et lecture de contenu de fichier                                                                             |        cat        |
| Lire le contenu d'un fichier texte une page à la fois                                                                  |       less        |
| Trouver et gérer des fichier/folders par plusieurs critères (nom, type, extension, taille, autorisations...)           |       find        |
| Trouver un mot en parcourant tous les textes d'un fichier spécifique                                                   |       grep        |
| Transfert et Synchronisation de Fichiers                                                                               |        scp        |
| Transférer et synchroniser des fichiers ou folders entre une<br/> machine locale, un autre hôte, un shell distant etc. |       rsync       |
| Editeur de Texte                                                                                                       |        vim        |
| Editeur de texte                                                                                                       |       nano        |
| Passer en mode super utilisateur                                                                                       |       sudo        |
| Mettre fin manuellement à un programme                                                                                 |       kill        |
|                                                                                                                        |                   |
|                                                                                                                        |                   |
|                                                                                                                        |                   |


## Mise en production d’applications sans conteneurisation

### PHP-FPM et NGINX

#### PHP-FPM
Source : 
- https://www.theory7.net/fr/help/php-fpm/
- https://www.stackscale.com/blog/php-fpm-high-traffic-websites/
- https://geekflare.com/fr/php-fpm-optimization/

PHP-FPM = PHP FastCGI Process Manager

--> Permet d'améliorer les performances des sites web à fort trafic s'ils fonctionnent en PHP.

Comment c'est possible ? <br>
En fait, PHP-FPM offre des fonctionnalités permettant une gestion plus efficace de la mémoire et du processeur, entre autre les ressources du système.
Ces fonctionnalités, on va pouvoir les appliquer à nos processus donc à notre code, à nos scripts ce qui permet d'améliorer les performances et la stabilité du site web.

Voici quelques une des ces fonctionnalités (en anglais psq on parle anglais poto): 
- Advanced management that enables to easily stop/start processes
- Accelerated support for uploads
- Slowlog variable configuration --> to detect which functions take a longer time to execute than usual
- FastCGI improvements --> a special function to stop and download all data while you keep doing a longer process such as video conversions or statistics processing.
- Basic statistics
cf. Source/La Doc pour le reste

En outre, PHP-FPM fournit des stats et journaux détaillés, cela permet de surveiller et d'optimiser les performances des scripts PHP.<br>
Par exemple, si un script utilisent + de ressources ou s'il met trop de temps à fournir une réponse, s'il y a beaucoup de trafic sur le site... PHP-FPM nous le remontera. Cela va donc nous permettre de savoir précisément qui améliorer (améliorer un script, lancer des processus supplémentaires pour répondre au pic de trafic...).

cf.Source pour plus de détails

#### NGINX
Source :
- https://kinsta.com/fr/base-de-connaissances/qu-est-ce-que-nginx/
- https://www.ionos.fr/digitalguide/serveur/configuration/nginx-bases-installation-et-configuration/

NGINX est un des serveurs web open-source les plus populaires et utilisés. <br>
Ce serveur web est en fait souvent utilisé par les sites webs les plus fréquentés ou bien ceux qui pourraient voir leur trafic augmenter, par les sites les plus gourmands en ressources.

Pourquoi ?<br>
En fait, NGINX a été créé pour répondre à un besoin de serveur de haute-performance, pouvant servir simultanément autant de clients Web (donc de requêtes) que possible, et qui ne soit pas trop gourmand en ressources.

NGINX utilise une approche asynchrone et événementielle, lui permettant donc d'exécuter des requêtes client simultanément sans bloquer les autres requêtes, sans devoir lancer un nouveau processus pour chaque requête client, et donc d'économiser de la mémoire vive, des ressources et du temps.

Il faut savoir que NGINX présente une interface modulaire. Cela signifie que différentes fonctions sont proposés sur les modules correspondants, que les administrateurs choisissent d’activer ou non. <br>
Voici quelques une des fonctionnalités proposées : 
- Application Acceleration (accélération de l’application) : permet un chargement plus rapide des contenus
- Reverse Proxying (proxy inverse)
- Chiffrement TLS : permet un échange de données sécurisé
- Gestion de la bande passante : associe la bande passante optimale pour chaque service proposé
- Load Balancing (équilibreur de charge) : répartit les demandes de manière à décharger le serveur principal
- Videostreaming (streaming vidéo) : offre une haute performance pour le streaming de fichiers MP4 et FLV

### Nginx and PHP-FPM: a perfect match
Source : 
- https://www.stackscale.com/blog/php-fpm-high-traffic-websites/

Nginx, as a stable high-performance web server and with a very low consumption of resources, is the perfect match for PHP-FPM. Nginx has an asynchronous architecture that is much more scalable, based on events. Moreover, when using Nginx with PHP-FPM, performance at the level of memory consumption is improved.

PHP runs as a separated service when using PHP-FPM. By using this PHP version as language interpreter, requests are processed through a TCP/IP socket; so that the Nginx web server only handles the HTTP requests and PHP-FPM interprets the PHP code. The fact of having two separate services is key for increasing efficiency.

#### Faites un schéma de l’interaction entre PHP-FPM, Nginx et votre code source quand un utilisateur souhaite accéder à la page d'accueil du site web

![](/home/user/Pictures/php-and-nginx.webp)

Source : https://geekflare.com/fr/php-fpm-optimization/

#### Tuto - Comment installer PHP, PHP-FPM, NGINX et les configurer sur votre serveur et DESACTIVER Apache 
- https://www.rosehosting.com/blog/how-to-install-php-7-4-with-nginx-on-ubuntu-20-04/
- https://www.digitalocean.com/community/tutorials/how-to-install-php-7-4-and-set-up-a-local-development-environment-on-ubuntu-20-04
- https://ubuntu.com/tutorials/install-and-configure-nginx#3-creating-our-own-website
- https://www.cyberciti.biz/faq/star-stop-restart-apache2-webserver/


### Limites de cette approche avec PHP-FPM et NGINX

#### Quelles sont les problématiques qui vont survenir par rapport à la gestion des différents codes source (notamment par rapport à la diversité des technologies) ?

Source : 
- https://chat.openai.com/c/21e00df9-1cce-4e9d-b4e8-349f0bf66751

**Problématique 1 :**
PHP-FPM, utilisé pour les sites fonctionnant sous PHP. Si un autre site fonctionne sous un autre langage, il se peut qu'il ne puisse pas utiliser PHP-FPM.

**Problématique 2 :** <br>
**Isolation des ressources :** Contrairement à la conteneurisation, où vous pouvez isoler les ressources et les dépendances de votre application, le déploiement direct sur un serveur avec PHP-FPM et Nginx ne fournit pas une isolation aussi robuste. Cela signifie que si une application affecte négativement le serveur (par exemple, en utilisant trop de ressources CPU ou mémoire), cela peut affecter d'autres applications s'exécutant sur le même serveur.

**Problématique 3 :** <br>
**Dépendances système :** Vous devrez gérer manuellement les dépendances système de votre application, ce qui peut être fastidieux et peut entraîner des conflits entre les applications si elles ont des exigences différentes en matière de dépendances.