---
#layout: post
title: "Configuration initiale et 1ere connexion sur le Raspberry Pi."
date: 2017-05-26 0:0:0 +0800
categories: Technologie
tags: raspbian raspberry-pi ssh
img: /assets/images/raspbian.jpg
permalink: /configuration-initiale-1ere-connexion-raspberry-pi/
---
Nous allons faire les premières configurations de notre Pi pour une première utilisation en tant que serveur.

# Activer SSH

Avant de continuer, il faudra avoir installé Raspbian sur votre carte SD (voir ici : Article Précédent)
Pour commencer nous allons réactiver le ssh afin de pouvoir faire toute l’administration à distance. (Je pars du principe que nous partons sur une configuration de type serveur).
La fondation derrière Raspbian a décidé de désactiver par défaut le serveur SSH à cause des récentes attaques perpétrées grâce aux objets IoT non protégés (ex: camera avec mot de passe par défaut), vous pouvez voir une news ici : https://www.raspberrypi.org/blog/a-security-update-for-raspbian-pixel/.

Si vous souhaitez en savoir un peu plus sur cette attaque, voici un article fait par NextImpact : https://www.nextinpact.com/news/101871-dyn-on-fait-point-sur-attaque-ddos-qui-a-impactee-nombreux-sites.htm

Revenons-en à nos moutons.

![image mouton](/assets/images/mouton.jpg)

Nous allons créer un fichier ssh à la racine de la partition boot.
Pas besoin d’écrire quoi que ce soit dans le fichier, un simple fichier nommé ssh vide suffira, j’attire votre attention sur le fait que le fichier ne doit pas avoir d’extension.
arborescence boot

# Trouver le Raspberry Pi sur son réseau

Pour nous connecter, une fois branché en Ethernet (câble carré à connecter sur votre box), il faudra déjà connaitre l’adresse IP de notre Raspberry Pi.

Pour cela, j’utilise un utilitaire qui scan mon réseau (AngryIpScanner : https://github.com/angryziber/ipscan/releases).

Normalement, le logiciel doit être déjà configuré pour votre plage d’adresse IP (il la détecte automatiquement suivant vos paramètres réseaux), on lance le scan en cliquant sur Start et magie tous nos équipements connectés apparaissent dans la liste.

Maintenant à vous de trouver l’adresse de votre Raspberry Pi dans le listing.

![image angry](/assets/images/angry.png)

Conseil de Sioux, si votre liste devait ne rien afficher et que le logiciel était déjà installé, faites sa mise à jour 😉

# Se connecter depuis votre ordinateur sur votre framboise

Maintenant que nous avons récupéré l’adresse IP, nous allons nous connecter en SSH via le logiciel Putty sur Windows (Lien : https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html) ou via un terminal sur MAC/Unix avec la commande suivante ssh :

`utilisateur@adresseipdevtrepi -p lennumerodeportssh`

Pour Putty, il suffit de rentrer le champ Hostname (Or Address IP).

![image putty](/assets/images/putty.png)

Pour la première connexion, le nom d’utilisateur sera pi et le mot de passe raspberry (tout en minuscule).

Une fois connecté, nous allons commencer par étendre la partition afin de pouvoir utiliser toute la carte SD.

Pour cela, il faut utiliser la commande ci-dessous et faire Expand FileSystem :

`sudo raspi-config`

Une fois cela fait, nous allons quitter l’utilitaire et accepter le redémarrage pour appliquer la modification sur la carte µSD.

Dans l’article suivant, nous verrons comment faire les premières configurations et comment faire un début de sécurisation sur Raspbian.
