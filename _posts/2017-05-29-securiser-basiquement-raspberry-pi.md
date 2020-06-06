---
layout: post
title: "Sécuriser basiquement Raspbian."
date: 2017-05-29 0:0:0 +0800
categories: Technologie
tags: raspbian raspberry-pi
img: /img/raspbian.jpg
permalink: /securiser-basiquement-raspbian/
---
Nous allons maintenant voir comment sécuriser basiquement notre Raspbian et faire nos premières configurations.
Pour commencer, je partirai du principe que vous avez suivi les étapes du tuto précèdent et donc que vous êtes connecté en SSH sur votre Raspberry Pi (Article Précédent).

# Mise à jour matériel et logicielle

Une fois que votre Raspberry Pi a redémarré sur sa carte maintenant pleinement utilisable, nous nous reconnectons et nous commençons par mettre à jour le firmware de notre Pi.

`sudo rpi-update && sudo reboot`

Cela peut mettre quelques secondes/minutes suivant votre connexion internet, votre Raspberry Pi redémarrera automatiquement à la fin de la procédure.

![image horloge](img/horloge.png)

Maintenant que notre matériel est correctement mis à jour, nous allons passer à celle du système Raspbian pour cela :

`sudo apt-get update && sudo apt-get dist-upgrade –y`

Avec la première commande nous allons mettre à jour les dépôts afin d’avoir une liste des packages les plus récent, avec la seconde nous allons mettre à jour Raspbian ainsi que les différents packages déjà installés.
Encore une fois, cela peut mettre un certain temps en fonction de votre connexion internet ainsi que suivant le nombre de package à mettre à jour.

![image horloge](img/horloge.png)

# Configuration basique

Nous allons maintenant réutiliser la fonction intégrée pour changer le mot de passe l’utilisateur pi et faire quelques autres réglages (je vous conseille d’utiliser tous ceux que je vous présente)

`sudo raspi-config`

La première ligne (une fois l’Expand FileSystem effectué) sert à changer le mot de passe de l’utilisateur pi, ce que nous allons faire IMMÉDIATEMENT. Je vous invite à choisir un mot de passe de minimum 8 caractères avec au moins 1 caractère de chaque type (majuscule/minuscule/caractère spécial).
La fonction numéro 2 sert à modifier le nom affiché de notre Raspberry Pi sur le réseau.
L’option numéro 3 nous permet de choisir sur quel mode le Rpi démarre, choisir le premier B1 puis les nouvelles options apparaîtront :
* B1 pour avoir l’interface en ligne de commande au démarrage (Conseillé pour un serveur)
* B2 pour avoir l’interface en ligne de commande directement connecté avec l’utilisateur Pi
* B3 pour avoir l’interface GUI (conseillé pour un pc desktop)
* B4 pour avoir l’interface GUI connecté directement avec l’utilisateur pi (peut être utile pour un lancer automatiquement un mediacenter par exemple)

L’option 4 pour changer les paramètres régionaux
* I1 pour changer les « locales », l’équivalent du pack de langue sur Windows. Cela permettra de passer le système dans la langue que vous souhaitez. Personnellement je laisse l’interface en Anglais (mais choisir fr_FR.UTF8 UTF8 et enlever en_GB.UTF8 UTF8 pour passer Raspbian en Français).
* I2 pour changer notre TimeZone et ainsi avoir la bonne heure pour les logs/crons

L’option 6 est là pour vous permettre d’overclocker votre Raspberry Pi, cela rendra votre Pi un peu plus rapide (non dispo de base sur Rpi 2 et 3). Attention, cette manipulation peut réduire la durée de vie de votre Raspberry Pi et créer quelques instabilités. A utiliser en votre âme et conscience.

L’option 7 pour choisir des options un peu plus poussées. A faire en sachant ce que vous faites.
* A2 si vous avez des barres noirs anormales qui apparaissent sur votre écran.
* A3 pour changer la quantité de mémoire alloué au GPU, à mettre au minimum (16) pour utilisation serveur, à augmenter si vous ressentez des saccades en utilisation sur une interface graphique (ex : pendant la lecture de média sur Kodi).
* A4 pour forcer l’audio en HDMI ou sur le port jack 3.5mm (peut être utile pour un serveur MPD)

Il ne nous reste plus qu’à quitter l’utilitaire et à redémarrer (sudo reboot)
Lors du prochain tuto, nous allons voir comment alléger notre système d’exploitation (Raspbian).
