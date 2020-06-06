---
layout: post
title: "Gladys en HTTPS via Let's Encrypt."
date: 2017-10-18 0:0:0 +0800
categories: Domotique
tags: gladys securite https domotique raspberry-pi
img: /img/gladys.jpg
permalink: /gladys-https-disparaitre-avertissement-securite-letsencrypt/
---
Aujourd'hui, nous allons voir comment activer le protocole HTTPS pour Gladys.
Vous allez me dire, mais pourquoi faire cela ?
Et bien ma chère Ginette pour 2 très bonnes raisons.
* 1ere : des connexions non sécurisées c'est mal.
* 2ème : des connexions sécurisées c'est mieux.

Comment ça, je ne réponds pas à la question :D

Plus sérieusement, premièrement cela est nécessaire pour certaines fonctionnalités (la fonction météo intégrée à Gladys, par exemple) ensuite cela évite que quelqu'un puisse intercepter facilement vos échanges avec Gladys.
Le second point n'est pas forcement utile en interne (quoi que maintenant avec certains logiciels espions...), cela est "obligatoire" lorsque votre instance Gladys est disponible depuis l'extérieur de votre maison.
Un exemple simple, un individu scrutant vos échanges avec Gladys (extrêmement facile à faire) sans HTTPS pourrait très facilement reprendre votre identification et contrôler Gladys sans même connaitre vos identifiants.

Pour ce tuto, je pars du principe que vous avez installé Gladys depuis l'image fournie sur le site et que vous êtes au moins en version 3.7.2.
De plus, je considère que vous avez votre propre nom domaine et que vous avez déjà fait une entrée DNS pointant sur votre IP publique et doit accéder à un site valide (dans notre cas Gladys en HTTP pour le moment).

# 1) Activation SSL dans Nginx

Nous allons commencer par activer la configuration avec un certificat auto-signé afin d'avoir les paramètres corrects dans la conf Nginx, si vous accédez déjà à Gladys via HTTPS passez à l’étape numéro 2 :

> sudo ./enable-ssl-gladys.sh

Comptez au moins 30min sur un Rpi3 pour la création du certificat.
Avec cette manipulation, nous allons valider que la configuration Nginx fonctionne correctement.
Pendant que les certificats se génèrent, si cela n'est pas déjà fait, je vous invite à rediriger le port 443 de votre box sur l'IP interne de Gladys (au moins le temps du tuto).

# 2) Mise en place du certificat via Let's Ecncrypt

Si tout fonctionne correctement lorsque vous vous connectez en https sur votre Gladys, nous pouvons passer à la suite :
Nous commençons par dupliquer le git de Let's Encrypt et arrêter le service Nginx pour pouvoir utiliser le port 443 temporairement :

> sudo git clone https://github.com/certbot/certbot /opt/letsencrypt

> sudo service nginx stop

Puis

> cd /opt/letsencrypt

> sudo ./certbot-auto --standalone certonly -d **votre.domaine.com**

Acceptez l'installation des dépendances et remplir vos informations personnelles

Nous allons maintenant commenter les certificats autogénérés et ajouter les nouveaux, en éditant le fichier /etc/nginx/snippets/self-signed.conf :

> sudo nano /etc/nginx/snippets/self-signed.conf

Vous devriez voir apparaitre :

> ssl_certificate /etc/ssl/certs/nginx-selfsigned.crt;
> ssl_certificate_key /etc/ssl/private/nginx-selfsigned.key;

A transformer en :

> #ssl_certificate /etc/ssl/certs/nginx-selfsigned.crt;
> #ssl_certificate_key /etc/ssl/private/nginx-selfsigned.key;
> ssl_certificate` `/etc/letsencrypt/live/**votre.domaine**/fullchain.pem;
> ssl_certificate_key` `/etc/letsencrypt/live/**votre.domaine**/privkey.pem;

Il ne nous reste plus qu'à redémarrer le service Nginx.

> sudo service nginx start

# 3) Automatiser le renouvellement du certificat :

Peut-être que vous ne le savez pas (_ou peut-être que si ;)_ ) mais un certificat n’est valide que pour une période donnée (3mois chez Let’s Encrypt), il faut donc le renouveler régulièrement. L’outil utilisé précédemment permet de faire cela automatiquement sans intervention de notre part.
Pour cela, nous allons créer une tache cron pour l'utilisateur root (d'où le sudo) qui se lance tous les matins à 3h00 :

> sudo crontab -e

Ajouter à la suite (adapter l'heure suivant votre souhait, pour vous aider vous pouvez utiliser : https://crontab.guru/ )

> 0 3 * * * /etc/init.d/nginx stop && /opt/letsencrypt/certbot-auto renew && /etc/init.d/nginx start

**Attention :**

Pensez à modifier la configuration de vos modules (ex : gladys-bluetooth et son fichier config.js), pour ne plus être ennuyé, il est conseillé de mettre http://votreinstancegladys:8080 celle-ci reste toujours accessible après le passage en HTTPS.

Le tuto est terminé, n'hésitez pas à poser des questions où à me faire un retour si quelque chose n'est pas clair ;)
