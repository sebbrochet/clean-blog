---
layout: post
title: "Evaluation de OneCMDB, une CMDB opensource"
tags: CMDB ITIL  ONECMDB OPENSOURCE
date:       2009-12-15 7:00:00
author:     "sebbrochet"
comments: true
redirect_from:
  - /post/Evaluation-de-OneCMDB,-une-CMDB-opensource
---

[OneCMDB](http://www.onecmdb.org/), édité par la société Lokomo, est un des logiciels de CMDB opensource les plus aboutis. La version 2.01 est sortie en septembre dernier. C'est l'occasion d'évaluer plus en détails les caractéristiques de cette nouvelle version.

La version 2.01 est une version qui n'apporte pas de nouvelles fonctionnalités par rapport à la version 2.0 sortie en juin de cette année mais qui corrige tout de même environ 20 bugs.  

La version précédente, 1.4, était sortie en octobre 2007 et montrait déjà le potentiel de ce produit, même si l'IHM était plutôt rudimentaire:

![OneCMDB 1.4]({{ site.url }}/img/2009/onecmdb_1_4.png)

On pourrait presque dire que cette nouvelle version pêche par l'excès inverse. En effet, nous avons maintenant droit à des représentations graphiques des différents items de configuration avec leurs relations et la possibilité de zoomer/dézoomer.

![OneCMDB 2.0 Table view]({{ site.url }}/img/2009/onecmdb_2_0_table_view.png)

![OneCMDB 2.0 Model view]({{ site.url }}/img/2009/onecmdb_2_0_model_view.png)

Malheureusement, ce dynamisme dans la représentation a un prix et la réactivité de toute l'application s'en ressent. La version 1.4 n'était déjà pas très réactive, cette nouvelle version enfonce le clou.

Une mention particulière sur la détection automatique des différents items de configuration qui marche plutôt bien. Elle était déjà présente dans la version 1.4 mais intégrée très superficiellement. Il est maintenant possible de sélectionner graphiquement le modèle de données à remplir à partir des données recueillies par NMap.

Plusieurs modèles de données sont livrés en standard mais il vous faudra sûrement les modifier pour les adapter à votre infrastructure.

# Points positifs

* Gratuite
* Configurable
* Assez bien documentée
* Interface moderne
* Riche en fonctionnalités

# Points négatifs

* Lente
* Complexe à configurer
* Pas de compatibilité des modèles entre la version 1.4 et 2.01
* Bureau avec menu démarrer dans une fenêtre de navigateur

# En conclusion
OneCMDB a du potentiel et possède un ensemble de fonctionnalités tout à fait acceptable. Il faudrait maintenant que Lokomo investisse des ressources dans l'amélioration des performances pour en faire un outil exploitable pour des infrastructures moyennes.
