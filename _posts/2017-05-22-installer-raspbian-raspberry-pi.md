---
layout: post
title: "Installer Raspbian sur un Raspberry Pi facilement."
date: 2017-05-22 0:0:0 +0800
categories: Technologie
tags: raspbian raspberry-pi ssh
img: /img/raspbian.jpg
permalink: /installer-raspbian-raspberry-pi/
---

Voici ce que j’estime important de savoir pour bien commencer avec un Raspberry Pi et Raspbian.

# Première installation d’un Raspberry Pi pour les nuls

Sur Raspberry Pi, de nombreux OS (Operating System, système d’exploitation) sont disponibles.
Pour l’exemple, en voici quelques-uns :

* Raspbian (https://www.raspbian.org/)
* Pidora (http://pidora.ca/)
* Ubuntu Mate / Snappy ( https://ubuntu-mate.org/raspberry-pi/ et https://developer.ubuntu.com/core/get-started#snappy-raspi2)
* Win10Iot (https://developer.microsoft.com/fr-fr/windows/iot/Downloads.htm)
* Open Elec (http://openelec.tv/)
* OSMC (https://osmc.tv/)

Ils sont différents, tous avec leur propre philosophie de base.

Je ne suis pas ici pour départager qui de telle distribution ou telle autre est la meilleure.

A chaque fois, je ferais le choix suivant les différents tests que j’aurai pu faire ou avec mes affinités sur PC fixe.

Mais n’hésitez pas à venir partager avec nous dans les commentaires 😉

# Télécharger Raspbian

Pour commencer, nous allons utiliser la distribution de base prévue sur Raspberry Pi, à savoir Raspbian.

![image raspbian](img/raspbian.png)

Il faudra commencer par télécharger l’image de Raspbian.
Suivant le modèle de votre Pi, je vous conseillerais la version lite pour les versions 0 et 1 (A,B,B+):

https://raspbian-france.fr/download/raspbian_lite_latest.zip

Pour les Rpi 2 et 3, la version complète :

https://raspbian-france.fr/download/raspbian_latest.zip

Les 2 versions peuvent aller sur tous les modèles de Raspberry Pi mais la lite n’est pas forcement la plus adaptée pour les versions 2,3 et inversement.

# Installer Raspbian et Win32DiskImager

Pendant que nous récupérons l’image de l’OS nous allons télécharger Win32DiskImager :

https://sourceforge.net/projects/win32diskimager/files/latest/download

L’installation est basique, suivant, suivant, terminé.

Pour commencer, (après avoir branché notre carte µSD) on lance le logiciel et on choisit sur quel périphérique nous souhaitons installer l’image (ici G: ).

Ensuite, on récupère l’image (que l’on aura pris le soin de décompresser avant tout ça, par exemple avec 7-Zip) en cliquant sur l’icône de dossier. Il ne nous reste plus qu’à écrire sur la carte, attention une fois que vous aurez lancé la manipulation TOUTES les données dessus seront perdues.

![image win32diskimager](img/win32diskimager.png)

L’installation est relativement rapide sur une carte de catégorie 4 (compter une dizaine de minutes).

![image horloge](img/horloge.png)

Voilà c’est fini, nous pouvons maintenant insérer la carte dans le Raspberry Pi et le brancher.

Dans le prochain article, nous allons passer à la configuration initiale de Raspbian
