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

## Mise en production d'application avec conteneurisation
cf. livrables sur le drive + md

### Comprendre Docker
Source : 
- https://datascientest.com/docker-guide-complet
- https://ledatascientist.com/comprendre-docker-et-les-conteneurs/
- https://course.valentinflgt.fr/#/c/2023/docker/1.-introduction
- https://www.youtube.com/watch?v=GVogBCqrXck&list=PLn6POgpklwWq0iz59-px2z-qjDdZKEvWd --> Xavki crack en Système & Réseau
- Kit 4 sur le drive

### Faites une recherche sur les différents avantages qu’apporte la conteneurisation et essayé d’expliquer les grands principes avec vos mots

**Isolation** <br>
La conteneurisation permet d'isoler les différentes applications déployées/tournant/fonctionnant sur une même machine MAIS dans un environnement "isolé" de notre environnement local.

Chaque application possède sa propre configuration, ses propres dépendances, librairies et packages. Si elles tournaient toutes sur le même environnement sans être isolées, cela créerait des conflits entre elles. <br>
Par exemple, si deux applications du même environnement fonctionnent sous PHP 7.4 mais que chacune utilisent une librairie (ou autre) différentes (librairie A, librairie B) et bien il y aura des conflits et l'environnement ne saura pas laquelle exécutée. <br>

Alors qu'avec la conteneurisation, comme les applications sont déployées dans un environnement dit "isolé", il sera possible de les exécuter. La conteneurisation évite ce problème, l’application ne dépend plus de l’hôte sur lequel il est déployé (ou développé) mais du conteneur dans lequel il est packagé, on dit qu'elle fonctionne de manière isolée sur le système hôte.

**Portabilité** <br>
Le fait que les applications ne dépendent plus que de leur conteneur permet de les déployer dans n'importe quel environnement (n'importe quel machines, serveurs...).<br> 
**!!!** Elles fonctionnent de manières isolées sur le système hôte

**Reproductibilité**<br>
Ce point rejoint le précédent, une application (code source, dépendances, ...) packagée dans un conteneur permet de partager/fournir ce même conteneur, donc la même configuration, à différents environnements (machines, serveurs...)

**Efficace**<br>
La conteneurisation est en fait très efficace, rapide et permet de meilleures performances que les méthodes traditionnelles (machines virtuelles, déploiement manuel).<br>
Par exemple, un déploiement via machine virtuelle requiert d'allouer des ressources de notre propre machine. Une machine virtuelle possède son propre système d'exploitation, ça prend donc du temps à la démarrer et l'arrêter. <br>
A l'instar, un conteneur délivre uniquement les ressources nécessaires à une application. Il est donc beaucoup léger et simple ce qui permet de meilleures performances.

**Scalable** <br>
La conteneurisation permet de scaler, donc d'accroître l'ampleur/le volume de l'application en fonction des besoins.<br>
Donc si on veut déployer une application sur d'autres environnements, on aura juste à utiliser son conteneur. C'est très rapide et simple.

### Comment mapper un port dans Docker ?

https://www.nicelydev.com/docker/mapper-port-reseau-docker 

**ATTENTION :** <br>
Utiliser la commande --> "sudo docker run -d -p 8080:80 nginx" au lieu de "sudo docker run --rm -p 8080:80 nginx" car "--rm" dit que l'on souhaite supprimer automatiquement le conteneur Docker du système une fois qu'il a terminé son exécution.

### Quelle est la différence entre une image Docker et un conteneur ?
Une image Docker peut être considérée comme une description du conteneur. En fait, c'est un modèle immuable utilisé pour créer un conteneur. Elle contient le code source de l'application, les bibliothèques, les dépendances et autres fichiers nécessaires à l'exécution de l'application.

Un conteneur est juste une instance de l'image Docker, dans laquelle cette dernière est exécutée. Il s'agit d'une encapsulation légère d'une application et de son environnement d'exécution, fonctionnant de manière isolée sur le système hôte.

Le Docker File contenant les instructions concernant l'image Docker, permet d'instancier l'image Docker dans un conteneur.

### Que fait Docker si l'image demandée n'est pas présente localement ?
Dans ce cas, il ne peut pas instancier l'image Docker. Il faut d'abord pull l'image Docker via sa registry

### Est-ce que vos données sont encore présentes (sans volume persistant) ?
Non les données ne sont plus présentes

### How to create a Docker Volume 

https://docs.docker.com/storage/volumes/
https://phoenixnap.com/kb/docker-volumes#:~:text=To%20mount%20a%20data%20volume,produced%20inside%20the%20virtual%20environment.&text=Replace%20%5Bpath_in_container%5D%20with%20the%20path,data%20volume%20in%20the%20container.

### Est-ce que vos données sont encore présentes (avec volume persistant) ?
Oui les données sont encore présentes !!!

### Comprendre le principe de volume docker

Définition : Les volumes sont utilisés pour persister les données et partager des fichiers entre le conteneur et l'hôte. Ils sont essentiels pour éviter la perte de données lorsque les conteneurs sont arrêtés ou supprimés.

### Créer un volume Docker
Source : 
- https://docs.docker.com/storage/volumes/ 

Pour créer un volume Docker, il y a 2 façons de faire :
- -v ou --volume
- --mount

On va tout d'abord traiter la première façon : -v

La notation complète ressemble à ça : <br>
**-v myvolume:/directory/directory/...**

Décortiquons cette notation : 
- myvolume --> c'est le nom du volume mais pas que ! c'est également le chemin sur lequel sera monté le volume sur la machine hôte
- : --> permet de séparer le chemin (directory) dans lequel le volume sera monté sur la machine hôte et sur le conteneur
- /directory/directory/... --> directory dans laquelle sera monté le volume dans le conteneur, où l'image Docker choisie écrira par défaut ses fichiers de données <br>
Cette directory est propre à chaque l'image Docker qu'on a choisi, par exemple si on choisit l'image Docker MariaDB, il faudra écrire ceci : **-v myvolume:/var/lib/mysql** <br>
Bien évidemment, si on choisit une autre image Docker on écrira autre chose. On retrouve ce qu'il faut écrire sur le DockerHub de l'image à la section **"Caveats - Where to Store Data"**

### Quelle est la différence entre une application statefull et stateless ?
Source : 
- https://www.redhat.com/en/topics/cloud-native-apps/stateful-vs-stateless --> anglais
- https://renovacloud.com/stateful-vs-stateless-architecture-overview/?lang=en#:~:text=The%20key%20difference%20between%20stateful,that%20will%20survive%20service%20restarts. --> anglais
- https://www.redhat.com/fr/topics/cloud-native-apps/stateful-vs-stateless#:~:text=Un%20processus%20ou%20une%20application,c'%C3%A9tait%20la%20premi%C3%A8re%20fois. --> français

**Application Stateless :** <br>
Une application stateless ne stocke pas les données, ne fait référence à aucune transaction passée. En fait, chaque transaction est effectuée comme si c'était la première fois qu'on l'effectuait. Les applications stateless fournissent un service ou une fonction et utilisent un réseau de diffusion de contenu, le web ou des serveurs d'impression pour traiter ces requêtes à court terme. 

Par exemple, une recherche en ligne pour répondre à une question quelconque est une transaction stateless. Vous tapez votre question dans le moteur de recherche et appuyez sur Entrée. Si votre transaction est accidentellement interrompue ou fermée, vous devez en démarrer une nouvelle. Les transactions stateless sont comparables à des distributeurs automatiques : une seule requête et une seule réponse.

**Application Stateful :** <br>
Une application stateful, quant à elle, stocke les données. Les transactions précédentes sont prises en compte et peuvent affecter la transaction actuelle.

Si une transaction stateful est interrompue, le contexte et l'historique sont stockés et vous pouvez ainsi reprendre là où vous en étiez. Les applications stateful gardent une trace de divers éléments, comme l'URL de la page, les paramètres de préférence et l'activité récente. Les transactions stateful sont comparables à une conversation continue et périodique avec la même personne. Les plateformes bancaires en ligne et les messageries en sont deux exemples.

C'est pour cela que les applications stateful utilisent les mêmes serveurs chaque fois qu'elles traitent une requête d'un utilisateur.

Aujourd'hui, la majorité des applications que l'on utilise sont stateful.

### Lancer une application multi conteneur (avec docker-compose)

Source : 
- https://openclassrooms.com/fr/courses/2035766-optimisez-votre-deploiement-en-creant-des-conteneurs-avec-docker/6211677-creez-un-fichier-docker-compose-pour-orchestrer-vos-conteneurs
- DockerHub --> sur la page de l'image Docker que l'on souhaite utiliser, tout est détaillé plus bas
- https://www.techrepublic.com/article/how-to-build-a-docker-compose-file/