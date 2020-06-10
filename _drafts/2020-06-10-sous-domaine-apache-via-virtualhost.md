---
#layout: post
title: "Utiliser un sous-domaine avec Apache 2 via un virtualhost"
date: 2020-06-30 10:00:00
categories: Technologie
tags:
permalink: /sous-domaine-apache-virtualhost/
---
Aujourd'hui, petit article pour partager la façon d'utiliser un sous domaine avec Apache2.

Creer un fichier sans extension dans le dossier : /etc/apache2/sites-available/ ex : greg pour le nom de domaine greg.idrame.fr

Dans le fichier mettre :

>	<VirtualHost *:80>
>    ServerName greg.idrame.fr
>		ServerAlias *.greg.idrame.fr
>		ServerAlias greg.idrame.eu
>		ServerAlias *.greg.idrame.eu
>    DocumentRoot /var/www/ProFolio
>	</VirtualHost>

ln -s

Activer le site dans available il faut taper : a2ensite lenomdusitefichier

Relancer le serveur apache via :
> /etc/init.d/apache2 reload
