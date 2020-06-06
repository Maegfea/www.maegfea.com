---
layout: post
title: "Présentation du Raspberry Pi et quelques idées d’utilisations"
date: 2017-05-08 0:0:0 +0800
categories: Technologie
tags: raspbian raspberry-pi ssh
#img: /img/raspbian.jpg
permalink: /presentation-raspberry-pi-idees/
---
# Rapsberry Pi l’ordinateur à tout faire

Pour le retour en ligne du site, le premier tuto sera l’installation d’un système d’exploitation sur Raspberry Pi (que je raccourcirais par Pi ou Rpi).

Parce qu’il faut bien commencer quelque part et qu’en ce moment mes projets se basent principalement sur ce micro-ordinateur.

Mais avant d’entrer dans le vif du sujet, une petite présentation de la bête s’impose.

Pour les personnes qui ne seraient pas au courant, la carte Raspberry-Pi (né un 29 Février 2012) est un ordinateur miniature, de la taille d’une carte bancaire qui en a quand même dans le ventre (puisque je te dis que ce n’est pas la taille qui compte Maurice).

Voici ses caractéristiques dans la version actuellement commercialisée (Rpi V3):

comparaison de taille Raspberry Pi vs CB

![image rpi](img/rpi.png)

# Ses caractéristiques :

* CPU 64 bit quad core ARM Cortex-A53 intégré et cadencé à 1,2 GHz
* Contrôleur graphique (GPU) Broadcom Videocore IV
* 1 Go de mémoire vive (RAM)
* 1 port RJ45 Ethernet 10/100M
* 1 lecteur micro SD / SDHC (obligatoire pour l’amorcage)
* 4 prises USB 2.0 (2,5A)
* 1 port HDMI
* 1 audio Jack 3,5 mm
* GPIO 40 broches
* Wifi 802.11 b/g/n
* Bluetooth 4.1 (Bluetooth Classique et LE)

Quand je te dis qu'en a dans le ventre cette petite carte ;)
Tout cela pour une consommation ridicule (compter entre 3€ et 5€ suivant le modèle et les éléments connectés dessus)

# Quelques exemples d’utilisations

Le Rpi est parfait pour tous les « petits » usages, voici les premiers exemples qui me viennent en tête :

* Un NAS en branchant un disque dur USB
* Une box domotique (ex : Gladys,Domoticz,…)
* Une seedbox
* Un media-center (ex : Kodi)
* Une console rétro-gaming (ex : RecalBox)

Comme vous le voyez, la seule limite sera votre imagination.

Du fait de sa faible consommation, aucun souci pour le laisser allumer en permanence (compter moins de 5€ par an), avec ses systèmes d’exploitation serveur, il est donc parfait pour cet usage (de mon point de vue).

Une alimentation électrique d’au moins 2,5A est fortement recommandée pour la version 3 du Pi et 2A pour la 2.

Ce qui veut dire que ton chargeur de tablette sera sûrement trop juste l’ami 😉 (souvent 2A).

Si la carte devait ne pas être suffisamment alimentée un petit logo multicolore apparaîtra en haut à droite de l’écran.
![image alim-faible](img/alim-faible.png)
Pourquoi j’attire votre attention sur ce « détail », vous me direz.

Et bien tout simplement parce qu’un nombre trop important d’accès à la carte µSD avec une tension trop faible pourrait causer sa dégradation prématurée. Et croyez-moi, vous ne voulez pas perdre vos données à cause de ça 😉 (expérience déjà vécue 😥 )

Vu le coût / l’encombrement, cela va nous permettre de monter/tester des projets pour un coût minime et de rendre tout cela un peu plus WAF (Je te vois venir, non c’est pas le bruit du chien, go Wikipedia : https://fr.wikipedia.org/wiki/Facteur_d%27acceptation_f%C3%A9minine).

# Bien commencer

Vous souhaitez vous lancer ? Voici ce que je conseille :

* Raspberry Pi 3
* Alimentation 3A
* Boitier + dissipateurs

Pour un serveur, nous avons tout ce qu’il nous faut car nous ferons l’intégralité des manipulations via Putty.

Pour d’autres utilisations, en plus, il faudra rajouter un écran (en HDMI) et un clavier,

Prochaine étape, l’installation d’un OS sur le Raspberry-Pi.

Nous verrons rapidement quelques systèmes disponibles pour le Pi et dans quel cas les choisir.

J’ai dit des âneries, des informations complémentaires à rajouter ? N’hésitez pas à commenter 😉
