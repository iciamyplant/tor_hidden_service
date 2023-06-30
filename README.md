# I - Connaissances

## 1. Bien comprendre ce qu'est un Darknet

Réseau = Ensemble d'équipements reliés entre eux pour échanger des informations (Ex : Internet est un réseau informatique mondial accessible au public. Il contient lui-même des réseaux, c'est un réseau de réseaux, à commutation de paquets = technique utilisée pour le transfert de données informatiques) [Fonctionnement technique d'internet](https://github.com/iciamyplant/hack_trojan/tree/main/Reseaux)

|Internet|Darknet| Darkweb|
|----|----|----|
|réseau de réseaux sur lequel circulent des données à travers divers protocoles de communication| reseau overlay (réseau informatique bâti sur un autre réseau, en l'occurence sur internet) qui utilise des protocoles spécifiques intégrant des fonctions d'anonymat. Accessible uniquement avec un logiciel, des configurations ou une autorisation spécifiques| ensemble des sites d’un darknet donné|

|Darknets | Description|
|----|----|
|Retroshare|can be run as a darknet by default to perform anonymous file transfers if DHT and Discovery features are disabled

- service d’e-mail Mailpile
- I2P = overlay network that features a darknet whose sites are called "Eepsites"
- Freenet = popular darknet by default
- GNUnet = is a darknet if the "F2F (network) topology" option is enabled
- Syndie = is software used to publish distributed forums over the anonymous networks of I2P, Tor and Freenet
- OneSwarm = can be run as a darknet for friend-to-friend file-sharing
- Tribler = can be run as a darknet for file-sharing
- Tor = overlay network that features a darknet whose sites are called "hidden services"

### 1.3 Réseau superposé (= de surcouche = overlay)

internet vs darknet = Les différences de protocole de communication utilisés au niveau de la couche transport créent donc la discontinuité entre ces deux types d’espaces

C’est plus particulièrement l’absence de recours au protocole DNS qui distingue les location-hidden services du reste d’Internet en termes d’accessibilité

superposition = méthode permettant de définir des couches d’abstraction de réseau par logiciel pour faire fonctionner plusieurs réseaux distincts et virtualisés au-dessus d’une couche physique

Les réseaux Overlay = construire un réseau virtuel de couche 2 au-dessus d’un réseau de couche 3 : Les paquets du réseau sont encapsulés puis routés à travers l’infrastructure existante. Un des protocoles proposé est le VxLAN (Virtual eXtensible LAN) proposé dans le RFC 7348. Il encapsule les trames Ethernet dans un datagramme UDP.

Un réseau IP utilisant des circuits virtuels ATM, eux-mêmes créés sur des liens SDH, eux-mêmes sur de la fibre noire, donne un exemple de réseau superposé.

- repose sur l'infrastructure d'internet, et le protocole TCP/IP
- protocole spécifique permettant l'instauration d'un réseau superposé

### 1.4 Architecture pair à pair 

|Caractéristique|Darknet|Internet|
|----|----|----|
|Architecture|pair à pair = P2P|client serveur|
|Def architecture|architecture décentralisée, modèle d'échange en réseau où chaque entité est à la fois client et serveur, les entités de ce système sont des "noeuds" (peut être centralisé : une partie de l'échange passe par un serveur central intermédiaire, ou completement décentralisé)|modèle d'échange en réseau centralisé où l'information stockée à un endroit bien précis. Le client envoie des requêtes, le serveur attend les requêtes des clients et y répond |
|Protocole chiffrement|https||


### 1.5 Processus d'anonymisation




## 2. Fonctionnement de tor

Tor est un réseau de surcouche et un logiciel libre de type navigateur, basé sur Firefox. Ce logiciel permet d'accéder au www, ainsi qu'à des hidden services (hidden-services = location-hidden services = onion services = sites exclusivement accessibles via Tor, qui permettent de dissimuler l’identité des hébergeurs de contenu (serveurs), en plus de l'utilisateur.

### 2.1 Routage

des milliers de serveurs mis à disposition par des bénévoles que l’on appelle des nœuds et qui agissent comme des relais pour permettre
l’anonymisation des connexions. Askip la moitié son a la nsa : vrai ou pas ?



Tor repose sur l’utilisation de SOCKS, qui est un protocole standard qui permet de faciliter le routage de paquets entre les applications

le principe du « routage en oignon » : 
Le Transmission Control Protocol (TCP), à savoir le protocole standard régulant le transfert des données entre un client et un serveur sur Internet, requiert de connaître les adresses Internet Protocol (IP) du client comme du serveur pour établir la transmission entre eux. Le protocole de Tor permet d’établir la transmission entre un client utilisant Tor et un serveur classique sans que l’adresse IP du client soit divulguée au serveur : le client Tor transmet sa requête à un premier proxy Tor (le point d’entrée4), qui la transmet à un deuxième proxy ne connaissant lui-même que l’adresse du nœud précédent, et qui le transmet ensuite à un troisième et dernier proxy qui assumera la connexion avec le serveur (on parle de nœud de sortie). Ainsi, le serveur ne connaît que l’adresse IP du nœud de sortie, et les proxys Tor eux-mêmes ne connaissent que l’adresse du maillon qui les précède et de celui qui les suit immédiatement dans la chaîne de transmission

2.2 chiffrement
2.3 

Leur nom de domaine de premier niveau (TLD) est .onion (et non .com, .fr, ou autres domaines plus répandus). Tor a en effet son propre système chiffré de résolution de nom de domaine (DNS)


De 2014 à nos jours, le nombre d’utilisateurs uniques quotidiens de Tor est estimé à environ 2 000 000. Parmi eux, la majeure partie semble utiliser Tor pour se connecter au WWW : le débit total moyen sur le réseau Tor à l’été 2018 est légèrement supérieur à 100 Gbits/s, contre un peu plus de 1 Gbits/s pour le débit total moyen vers ou depuis les services .onion. Il semble donc raisonnable de dire que la connexion au WWW est le principal usage de Tor.


-----------------------------------------------


Comment on assure la sécurisation de la connexion ? Garantie la connexion avec la personne, et que personne d'autre peut récupérer les informations qu'on s'échange

Bases du chiffrement 

chiffrement symétrique
algo standard : AES
on chiffre une phrase a avec un mot de passe b = resultat c
si je déchiffre c avec b je retombe sur a 

quand on a la clé on parle de chiffrer et déchiffrer un message
quand on a pas la clé on parle de décrypter un message (quand on decrypte on essaye toutes les possibilités, ou on essaye de trouver une faille dans l'agorithme)

problème : pour qu'il y ai communication sur internet, il faut que les deux utilisent le meme mot de passe. Sauf qu'ils peuvent pas s'envoyer leur mot de passe en clair


la personne 1 va générer deux clés
- une publique : la donne à la personne 2
- une privé : la garde pour elle

avec ma clé publique je peux chiffrer le message. Par contre il est impossible de déchiffrer le message avec la meme clé, il faut la clé privé pour le faire. Donc la personne 2 va chiffrer les messages avec la clé publique de la personne 1. Comme ca la personne 1 peut déchiffrer le message avec sa clé privée ==> chiffrement asymétrique. 

- pers 2 demande de connexion à pers 1
- pers 1 donne sa clé publique
- pers 2 va créer une clé de chiffrement symétrique
- pers 2 chiffre cette clé de chiffrement symétrique avec la clé publique de la pers 1
- pers 2 envoie la clé de chiffrement symétrique à pers 1
- pers 1 déchiffre la clé de chiffrement symétrique avec sa clé privée
- pers 1 connait desormais la clé de chiffrement symétrique
- ils peuvent désormais communiquer en chiffrement symétrique


On a jamais a créer de clé de chiffrement à la main, c'est l'ordinateur qui le fait tout seul


algos de génération aléatoire

# II - Tor
Tor est un réseau overlay qui comporte un darknet : ses hidden services

# III - Dé-anonymisation
les darknets rendent cette identification sinon impossible, du moins très difficile
anonymat = cacher qui envoie le message
confidentialité = cacher le contenu du message

 La NSA (National Security Agency), l’agence de renseignements américaine,
peut se targuer de nombreuses réussites dans son effort pour affaiblir les logiciels de chiffrement et
d’anonymisation. Sa technique de prédilection est l’installation de portes dérobées dans les logiciels, ce qui lui
permet de contourner les moyens de défense mis en place par l’internaute. 

Programme Bullrun combinaison de superordinateurs, de ruses techniques, pour saper les bases de la confidentialité sur Internet, y compris les réseaux privés virtuels (VPN ) et les protocoles Secure Sockets Layer (SSL) et Transport Layer Security (TLS) largement utilisés.

En 2010, un programme de contre-chiffrement du GCHQ, baptisé Edgehill
https://arstechnica.com/information-technology/2014/01/how-the-nsa-may-have-put-a-backdoor-in-rsas-cryptography-a-technical-primer/

Linus Torvalds approché par le gouvernement des US pour installer backdoors dans Linux

qui valide, diffuse les standards de sécurité de cryptographie


# II - Technique

Côté logiciels, nous aurons besoin de l’accès root des
machines zabeth ou tutur pour installer Tor Browser. L’ajout du nœud se fera sur
une machine virtuelle que nous allons mettre en place sur le serveur Chassiron à
l’aide l’hyperviseur Xen et de l’outil LVM pour la création de volumes. Le service
caché pourra être hébergé sur cette même machine sur laquelle nous aurons aussi
installé un serveur web tels qu’Apache ou Nginx. Concernant la partie analyse et
sécurité, Wireshark ou tcpdump se révéleront être des outils pratiques pour analyser
les paquets reçus sur une interface réseau.


Sources
[Un « Deep / dark web » ? Les métaphores de la profondeur et de l’ombre sur le réseau Tor](https://journals.openedition.org/netcom/3134)
