---
#layout: post
title: "Récupérer les derniers caractères d'une chaine XML via XPATH"
date: 2020-10-05 16:00:00
categories: Technologie
tags: XML XPATH
permalink: /xpath-dernier-caractere-chaine/
---

Aujourd'hui petit nota-bene pour retrouver les X premier caracteres d'une chaine XML via une requete XPATH :

    substring('VotreChaine', 1, X)

Exemple pour recuperer les 9 derniers caractères :

    substring('VotreChaine', 1, 9)

En esperant que cela pourra vous aider :)