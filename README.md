# I - 

### I.1 Définitions

|Internet|Darknet| Darkweb|
|----|----|----|
|réseau de réseaux sur lequel circulent des données à travers divers protocoles de communication| reseau overlay (réseau informatique bâti sur un autre réseau, en l'occurence sur internet) qui utilise des protocoles spécifiques intégrant des fonctions d'anonymat. Accessible uniquement avec un logiciel, des configurations ou une autorisation spécifiques| ensemble des sites d’un darknet donné|

Darknets : 
- Retroshare = can be run as a darknet by default to perform anonymous file transfers if DHT and Discovery features are disabled
- service d’e-mail Mailpile
- I2P = overlay network that features a darknet whose sites are called "Eepsites"
- Freenet = popular darknet by default
- GNUnet = is a darknet if the "F2F (network) topology" option is enabled
- Syndie = is software used to publish distributed forums over the anonymous networks of I2P, Tor and Freenet
- OneSwarm = can be run as a darknet for friend-to-friend file-sharing
- Tribler = can be run as a darknet for file-sharing
- Tor = overlay network that features a darknet whose sites are called "hidden services"

### I.2 Fonctionnement technique Internet et Darknets

Caractéristiques d'un darknet :
- repose sur l'infrastructure d'internet, et le protocole TCP/IP
- protocole spécifique permettant l'instauration d'un réseau superposé
- architecture décentralisée de type pair à pair
- integration de processus d'anonymisation

|Caractéristique|Internet|Darknet|
|----|----|----|
|Architecture|pair à pair = P2P|client serveur|
|Def architecture|modèle d'échange en réseau où chaque entité est à la fois client et serveur, les entités de ce système sont des "noeuds" (peut être centralisé : une partie de l'échange passe par un serveur central intermédiaire, ou completement décentralisé)|modèle d'échange en réseau centralisé où l'information stockée à un endroit bien précis. Le client envoie des requêtes, le serveur attend les requêtes des clients et y répond |
|Protocole chiffrement|https||


Comment on assure la sécurisation de la connexion ? Garantie la connexion avec la personne, et que personne d'autre peut récupérer les informations qu'on s'échange

Bases du chiffrement 

chiffrmeent symétrique
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
