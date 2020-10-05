---
#layout: post
title: "Récupérer les derniers caractères d'une chaine XML via XPATH"
date: 2020-10-05 16:00:00
categories: Technologie
tags: XML XPATH
permalink: /xpath-dernier-caractere-chaine/
---

Aujourd'hui petit nota-bene pour retrouver les X derniers caracteres d'une chaine XML via une requete XPATH :

    substring('VotreChaine', string-length('VotreChaine')-X)

Exemple pour recuperer les 10 derniers caractères :

    substring('VotreChaine', string-length('VotreChaine')-9)

On peut voir dans l'exemple qu'il commence à compter à partir de 0 donc mettre 9 pour 10 etc

En esperant que cela pourra vous aider :)