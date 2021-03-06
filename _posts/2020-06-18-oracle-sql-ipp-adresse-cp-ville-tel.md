---
#layout: post
title: "Oracle SQL - Recuperer les informations suivant nom prenom date de naissance et sexe"
date: 2020-06-19 11:00:00
categories: Oracle SQL
tags: oracle sql ipp adresse code postal ville telephone
permalink: /oracle-sql-ipp-adresse-cp-ville-tel/
---
Récupération des informations pour une personne suivant sa date de naissance.

Recherche sur nom de naissance car pas de nom d'usage pour les hommes (il est vide dans la table pour les hommes).

```sql
SELECT
  PAT.IDENTITE.IDP IPP,
  PAT.IDENTITE_ADRESSE.RUE AD1,
  PAT.IDENTITE_ADRESSE.PREMIERELIGNE AD2,
  PAT.IDENTITE_ADRESSE.CODEPOSTAL CP,
  PAT.IDENTITE_ADRESSE.VILLE VILLE,
  PAT.IDENTITE_TRAITS_COMPL.TELEPHONE_DOMICILE DOM,
  PAT.IDENTITE_TRAITS_COMPL.TELEPHONE_PORTABLE MOB
FROM
  PAT.IDENTITE,
  PAT.IDENTITE_ADRESSE,
  PAT.IDENTITE_TRAITS_COMPL
WHERE
  ( PAT.IDENTITE_ADRESSE.IDDI(+) = PAT.IDENTITE.IDDI and PAT.IDENTITE_ADRESSE.IDP(+) = PAT.IDENTITE.IDP and PAT.IDENTITE_ADRESSE.TYPEADRESSE(+) = 'H'  )
  AND  ( PAT.IDENTITE.IDDI = PAT.IDENTITE_TRAITS_COMPL.IDDI(+) and PAT.IDENTITE.IDP = PAT.IDENTITE_TRAITS_COMPL.IDP(+)  )
  AND
  (
   TRUNC(PAT.IDENTITE.DATENAIS)  =  to_date ('$Date;','YYYYMMDD')
   AND
   PAT.IDENTITE.NOMNAIS  =  '$Nom;'
   AND
   PAT.IDENTITE.PRENOMUSAGE  =  '$Prenom;'
   AND
   PAT.IDENTITE.SEXE  IN  ( 'M' )
  )
```

Requête identique pour les femmes non mariées car le nom d'usage est vide comme les hommes

```sql
SELECT
  PAT.IDENTITE.IDP IPP,
  PAT.IDENTITE_ADRESSE.RUE AD1,
  PAT.IDENTITE_ADRESSE.PREMIERELIGNE AD2,
  PAT.IDENTITE_ADRESSE.CODEPOSTAL CP,
  PAT.IDENTITE_ADRESSE.VILLE VILLE,
  PAT.IDENTITE_TRAITS_COMPL.TELEPHONE_DOMICILE DOM,
  PAT.IDENTITE_TRAITS_COMPL.TELEPHONE_PORTABLE MOB
FROM
  PAT.IDENTITE,
  PAT.IDENTITE_ADRESSE,
  PAT.IDENTITE_TRAITS_COMPL
WHERE
  ( PAT.IDENTITE_ADRESSE.IDDI(+) = PAT.IDENTITE.IDDI and PAT.IDENTITE_ADRESSE.IDP(+) = PAT.IDENTITE.IDP and PAT.IDENTITE_ADRESSE.TYPEADRESSE(+) = 'H'  )
  AND  ( PAT.IDENTITE.IDDI = PAT.IDENTITE_TRAITS_COMPL.IDDI(+) and PAT.IDENTITE.IDP = PAT.IDENTITE_TRAITS_COMPL.IDP(+)  )
  AND
  (
   TRUNC(PAT.IDENTITE.DATENAIS)  =  to_date ('$Date;','YYYYMMDD')
   AND
   PAT.IDENTITE.NOMNAIS  =  '$Nom;'
   AND
   PAT.IDENTITE.PRENOMUSAGE  =  '$Prenom;'
   AND
   PAT.IDENTITE.SEXE  IN  ( 'F' )
  )
```

Ici on utilise 'nomusage' car les femmes ont leurs noms de mariées de renseignés

```sql
SELECT
   PAT.IDENTITE.IDP IPP,
   PAT.IDENTITE_ADRESSE.RUE AD1,
   PAT.IDENTITE_ADRESSE.PREMIERELIGNE AD2,
   PAT.IDENTITE_ADRESSE.CODEPOSTAL CP,
   PAT.IDENTITE_ADRESSE.VILLE VILLE,
   PAT.IDENTITE_TRAITS_COMPL.TELEPHONE_DOMICILE DOM,
   PAT.IDENTITE_TRAITS_COMPL.TELEPHONE_PORTABLE MOB
FROM
   PAT.IDENTITE,
   PAT.IDENTITE_ADRESSE,
   PAT.IDENTITE_TRAITS_COMPL
WHERE
   ( PAT.IDENTITE_ADRESSE.IDDI(+) = PAT.IDENTITE.IDDI and PAT.IDENTITE_ADRESSE.IDP(+) = PAT.IDENTITE.IDP and PAT.IDENTITE_ADRESSE.TYPEADRESSE(+) = 'H'  )
   AND  ( PAT.IDENTITE.IDDI = PAT.IDENTITE_TRAITS_COMPL.IDDI(+) and PAT.IDENTITE.IDP = PAT.IDENTITE_TRAITS_COMPL.IDP(+)  )
   AND
   (
    TRUNC(PAT.IDENTITE.DATENAIS)  =  to_date ('$Date;','YYYYMMDD')
   AND
   PAT.IDENTITE.NOMUSAGE  =  '$Nom;'
   AND
   PAT.IDENTITE.PRENOMUSAGE  =  '$Prenom;'
   AND
   PAT.IDENTITE.SEXE  IN  ( 'F' )
  )
  ```
