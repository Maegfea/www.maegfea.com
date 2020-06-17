---
#layout: post
title: "Utiliser un sous-domaine avec Apache 2 via un virtualhost"
date: 2020-06-18 16:00:00
categories: Technologie
tags: apache virtualhost domaine
permalink: /sous-domaine-apache-virtualhost/
---
Aujourd'hui, petit article pour partager la façon d'utiliser un sous domaine avec Apache2.

Créer un fichier sans extension dans le dossier /etc/apache2/sites-available/

ex : www pour le nom de domaine www.maegfea.com donne :

`nano /etc/apache2/sites-available/www`

Dans le fichier mettre ceci :

```
<VirtualHost *:80>
  ServerName www.maegfea.com
  ServerAlias *.www.maegfea.com
  DocumentRoot /var/www/VotreSite
</VirtualHost>
```

Nous allons maintenant créer un lien symbolique de notre dossier sites-available vers site-enable avec :

`ln -s /etc/apache2/sites-available/www /etc/apache2/sites-enable/`

Maintenant il faut dire à Apache d'activer le site dans enable.
Pour cela utiliser la commande suivante :

`a2ensite lenomdusitefichier`

Il ne reste plus qu'à recharger la configuration du serveur apache via :

`/etc/init.d/apache2 reload`
