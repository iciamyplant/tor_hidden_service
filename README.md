# I - Connaissances

## 1. Darknet

Réseau = Ensemble d'équipements reliés entre eux pour échanger des informations (Ex : Internet est un réseau informatique mondial accessible au public. Il contient lui-même des réseaux, c'est un réseau de réseaux, à commutation de paquets = technique utilisée pour le transfert de données informatiques) [Fonctionnement technique d'internet](https://github.com/iciamyplant/hack_trojan/tree/main/Reseaux)

|Internet|Darknet| Darkweb|
|----|----|----|
|réseau de réseaux sur lequel circulent des données à travers divers protocoles de communication| reseau overlay (réseau informatique bâti sur un autre réseau), en l'occurence sur l'infrastructure d'internet et le protocole TCP/IP, et qui utilise des protocoles spécifiques intégrant des fonctions d'anonymat. Accessible uniquement avec un logiciel, des configurations ou une autorisation spécifiques| ensemble des sites d’un darknet donné|


Réseau superposé (= de surcouche = overlay) : c'est une couche virtuelle au-dessus de l'infrastructure physique d'un réseau. Cela peut être aussi simple qu'un réseau local virtuel (VLAN), mais fait généralement référence à des couches virtuelles plus complexes d'un réseau défini par logiciel (SDN) ou d'un réseau étendu défini par logiciel (SD-WAN).

Explication du VLAN :
- LAN = local area network, équipements terminaux qui s'échangent des données dans une zone restrainte, dans un domaine de broadcast
- Domaine brodacast (= domaine de diffusion) = quand un périphérique envoie des broadcasts (=messages)  sur le LAN, tous les périphériques du réseau les reçoivent
- VLAN = virtual LAN. Grâce à un commutateur, il est possible de séparer les périphériques en plusieurs domaines de broadcasts, pour que chaque préiphérique ne recoivent que les broadcasts de son domaine de broadcast. Alors, chaque domaine est un VLAN. Tous les périphériques partagent la même infrastructure, ou le même switch, mais ils agissent comme des réseaux indépendants.
- Commutateur (= switch) = matériel, permet de connnecter les machines entre elles sur un réseau local

Explication du SDN : 
- SDN = software-defined networking
- Les commutateurs et les routeurs programment leurs tables de forwarding localement, ce qui signifie que les périphériques réseau prennent leurs propres décisions en interne sur la meilleure façon d'aiguiller le trafic. Pour fonctionner ensemble, tous les équipements du réseau doivent suivre les règles définies par les standards. Cela laisse peu de place à la créativité ou à des exigences métiers inhabituelles
- plan de contrôle : comment un équipement forwarde le trafic (partie + intelligente de l'équipement)
- plan de données : la partie des commutateurs et routeurs qui assure effectivement le mouvement des données (partie + materielle)
- Dans les SDN, le plan de contrôle est placé dans un contrôleur centralisé qui a une visibilité sur l’ensemble du réseau. Au lieu que chaque équipement s'auto-gère avec une petite partie intelligente (plan de contrôle), je centralise l'intelligence. Au travers d'une interface digitale qui permet de configurer les équipements à distance, je peux même automatiser certaines tâches dessus




|Caractéristique|Darknet|Internet|
|----|----|----|
|Architecture|pair à pair = P2P|client serveur|
|Def architecture|architecture décentralisée, modèle d'échange en réseau où chaque entité est à la fois client et serveur, les entités de ce système sont des "noeuds" (peut être centralisé : une partie de l'échange passe par un serveur central intermédiaire, ou completement décentralisé)|modèle d'échange en réseau centralisé où l'information stockée à un endroit bien précis. Le client envoie des requêtes, le serveur attend les requêtes des clients et y répond |
|Protocole chiffrement|https||






## 2. TOR

Tor est un réseau superposé distribué reposant sur un protocole réseau (ensemble établi de règles qui déterminent comment les données sont transmises entre différents appareils dans le même réseau : comme HTTP ou FTP, ...) qui permet la communication entre les hôtes et possède diverses propriétés. D'où, Tor fonctionne au niveau de la couche application comme HTTP. Chaque protocole est conçu avec certaines propriétés. Voilà les propriétés du protocole de Tor :
- il est censé fonctionner comme un protocole (= de superposition de réseau. Cela signifie qu'il est censé former un réseau de superposition au-dessus du trafic réseau existant qui peut utiliser n'importe quel protocole de couche d'application en dessous (comme HTTP, FTP, SSH, etc.)
- il fonctionne sur un réseau de nœuds et crée des circuits virtuels à travers ce réseau tor qui permettent le routage du trafic à travers les circuits virtuels
- grâce à ses circuits virtuels et à l'utilisation de protocoles cryptographiques, il aide à créer des canaux sécurisés de transmission d'informations qui confèrent au réseau tor l'anonymat. Par conséquent, il est conçu pour le transfert anonyme de données entre le client et l'hôte final

Tor est également un logiciel libre de type navigateur, basé sur Firefox. Ce logiciel permet d'accéder au www, ainsi qu'à des hidden services (hidden-services = location-hidden services = onion services = sites exclusivement accessibles via Tor, qui permettent de dissimuler l’identité des hébergeurs de contenu (serveurs), en plus de l'identité de l'utilisateur.

Tor implique 3 parties :
- Le client Tor = le proxy oignon
- Le Tor Router = Onion Router
- L'hôte = destination finale
  + Le message Tor = Tor Cell

 
### 2.1 Oinion Proxy

C'est le composant qui s'exécute dans le cadre du navigateur Tor. Il permet à tout client de se connecter au dark web et d'accéder au réseau superposé exploité par Tor. Le composant Proxy prend votre vanilla HTTP traffic (par exemple) et l'enveloppe dans le trafic Tor et l'envoie sur le réseau Tor pour une communication anonyme. Pour vous, en tant que client, cela ressemble à une navigation normale.

La raison pour laquelle il est appelé proxy est qu'il se comporte comme un proxy pour votre communication de trafic Web normale. Il s'agit en fait d'un proxy SOCKS et fonctionne au niveau de la couche SOCKS.

Le proxy oignon est également celui qui construit un circuit virtuel pour la communication, configure le circuit et démarre la transmission des données dans les deux sens. Ce circuit virtuel est créé sur le réseau Tor en utilisant le composant suivant dont nous parlerons qui sont les routeurs Tor/onion routers.

### 2.2 Oinion Routers

Cette partie du protocole tor est le cœur du réseau superposé que Tor crée pour la communication. Lorsque vous téléchargez le navigateur Tor, vous avez la possibilité de vous configurer en tant que nœud Tor, qui est précisément le routeur oignon. Le routeur oignon est le processus qui fait que votre machine/hôte agit comme un routeur dans le réseau tor. Si vous avez choisi d'exécuter votre machine en tant que nœud Tor, vous autorisez Tor à utiliser votre machine dans le cadre du réseau de superposition créé par Tor.

Ce que font les routeurs, c'est participer à la création de circuits virtuels qu'un proxy onion quelque part dans le monde a créé. Et ensuite acheminer le trafic à travers eux-mêmes dans les circuits dont ils font partie. Un routeur Onion peut faire partie de plusieurs circuits, il maintient une sorte de table de routage qui lui permet d'acheminer le trafic via les circuits corrects.

Par conséquent, vous pouvez être un proxy ainsi qu'un routeur à tout moment. En outre, il existe un type spécial de nœud appelé nœud de sortie, qui est le dernier nœud du circuit virtuel. Ce nœud est spécial dans le sens où vous pouvez choisir de ne pas être le nœud de sortie car il est directement exposé à Internet extérieur et a de sérieuses implications en matière de sécurité. (Par exemple, si certains clients anonymes achètent des médicaments sur le réseau Tor, il semblera que le nœud de sortie fasse les demandes. Alors méfiez-vous avant de choisir d'être un nœud de sortie)

### 2.3 L'hôte

Hôte réel auquel le client souhaite se connecter. Il peut s'agir d'un simple hôte Internet ou d'un service caché.






Connaître maintenant les principaux composants permet de comprendre comment le protocole fonctionne réellement et comment il crée un canal/circuit anonyme sécurisé à l'aide de la cryptographie et d'autres outils.





### 2.1 Routage

des milliers de serveurs mis à disposition par des bénévoles que l’on appelle des nœuds et qui agissent comme des relais pour permettre
l’anonymisation des connexions. Askip la moitié sont a la nsa : vrai ou pas ?



Tor repose sur l’utilisation de SOCKS, qui est un protocole standard qui permet de faciliter le routage de paquets entre les applications

le principe du « routage en oignon » : 
Le Transmission Control Protocol (TCP), à savoir le protocole standard régulant le transfert des données entre un client et un serveur sur Internet, requiert de connaître les adresses Internet Protocol (IP) du client comme du serveur pour établir la transmission entre eux. Le protocole de Tor permet d’établir la transmission entre un client utilisant Tor et un serveur classique sans que l’adresse IP du client soit divulguée au serveur : le client Tor transmet sa requête à un premier proxy Tor (le point d’entrée4), qui la transmet à un deuxième proxy ne connaissant lui-même que l’adresse du nœud précédent, et qui le transmet ensuite à un troisième et dernier proxy qui assumera la connexion avec le serveur (on parle de nœud de sortie). Ainsi, le serveur ne connaît que l’adresse IP du nœud de sortie, et les proxys Tor eux-mêmes ne connaissent que l’adresse du maillon qui les précède et de celui qui les suit immédiatement dans la chaîne de transmission

un noeud tor = peut être un pc personnel, un serveur ou meme un telephone portable. Conditions : être connecté à internet, et 

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
[Explications techniques](https://ieee.nitk.ac.in/virtual-expo/tor/)

|Darknets | Description|
|----|----|
|Retroshare|can be run as a darknet by default to perform anonymous file transfers if DHT and Discovery features are disabled
|service d’e-mail Mailpile||
|I2P|overlay network that features a darknet whose sites are called "Eepsites"|
| Freenet| popular darknet by default|
|GNUnet|is a darknet if the "F2F (network) topology" option is enabled|
|Syndie|is software used to publish distributed forums over the anonymous networks of I2P, Tor and Freenet|
|OneSwarm|can be run as a darknet for friend-to-friend file-sharing|
| Tribler|can be run as a darknet for file-sharing|
|Tor|overlay network that features a darknet whose sites are called "hidden services"|
