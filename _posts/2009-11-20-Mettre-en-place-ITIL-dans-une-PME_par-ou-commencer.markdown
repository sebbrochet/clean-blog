---
layout: post
title: "Mettre en place ITIL dans une PME, par où commencer ?"
subtitle:   "parce-qu'ITIL n'est pas fait que pour les grosses boîtes."
tags: ITIL PME
date:       2009-11-20 12:00:00
author:     "sebbrochet"
header-img: "img/post-bg-01.jpg"
---

[ITIL](http://www.itil-officialsite.com/) (Information Technology Infrastructure Library) est un référentiel de bonnes pratiques.   

Ce n'est ni un standard ni une norme qu'il faudrait suivre pour être certifié.   

Il conseille sur ce qu'il faut faire pour gérer les systèmes d'informations mais ne dit pas comment le faire.   
ITIL n'est pas réservé aux grands groupes de plusieurs milliers de salariés.   
En fait, quelle que soit sa taille, les bonnes pratiques d'ITIL doivent être adaptées aux spécificités de l'entreprise.   
   
Il se compose de processus mais ne précise pas, volontairement, dans quel ordre les mettre en place.   
   
Voyons ensemble quels processus font le plus de sens dans une petite structure.   
C'est-à-dire ceux qui ne demandent pas un investissement trop conséquent en temps et en argent et qui produisent rapidement des résultats.   
   
Notre petite structure ayant, pour l'exemple, des développements spécifiques au cœur de son métier l'empêchant d'externaliser complètement son SI.   
   
# Gestion de la Configuration
Ce processus permet de connaître les composants du SI et leurs relations au sein de ce qu'on appelle une CMDB (Configuration  Management Database).   
Dans notre cas, il n'est pas utile d'investir dans des outils complexes et un logiciel d'inventaire de parc informatique est un bon début ([OCS-Inventory](http://www.ocsinventory-ng.org/) par exemple).   

# Gestion des Incidents
Ce processus est chargé de traiter tous les événements qui sortent du cadre normal de fonctionnement du SI. L'objectif est de rétablir les conditions normales au plus vite. On prendra soin d'établir un point de contact unique accessible par mail, téléphone ou mieux au travers d'un système de tickets ([JIRA](http://www.atlassian.com/software/jira/) par exemple). La description de l'incident référence les éléments défaillants en utilisant la même nomenclature que celle utilisée dans la CMDB. Le suivi de l'incident est aussi de la responsabilité de ce processus.   

# Gestion des Problèmes
Quand plusieurs incidents identiques se produisent sans que les causes soient connues, ITIL parle de problème. Quand les causes sont établies, le problème devient une erreur connue. Ce processus est chargé de déterminer les causes du problème afin de trouver une solution définitive.   
Même dans le cas d'une structure modeste, on aura tout intérêt à ce qu'une même personne ne gère pas à la fois les Incidents et les Problèmes car les objectifs ne sont pas les mêmes et potentiellement non compatibles.  

# Gestion du Changement
Le changement fait partie du cycle de vie du SI et lui permet de s'aligner sur les besoins métiers. Le changement ou évolution correspond donc à un besoin. Ce besoin peut se traduire par l'application d'un correctif, des réglages de configuration, l'ajout de machines, ...   
Un changement non maîtrisé conduit à un moment ou un autre à des dysfonctionnements. L'objectif de ce processus est donc d'encadrer toute modification du SI, pour cela il faut:   

* définir clairement le changement avant qu'il ne soit ou non accepté. Il faut notamment justifier son intérêt vis-à-vis des besoins métiers   
* évaluer les risques liés à l'application du changement   
* prévoir un plan de test pour qualifier le changement   
* définir un plan de retour arrière si le changement qui a été effectué n'est pas validé   

# Pour résumer
Il faut idéalement 2 personnes minimum au service IT de notre PME. Ces 2 personnes mettront en place ensemble la partie CMDB. Sa mise-à-jour se fera par chacun d'eux dans le cadre des évolutions dont ils sont respectivement chargés dans la gestion des Incidents et des Problèmes. La gestion des Changement pourra être assignée à une autre personne ou bien à celle qui traite des Problèmes.   
 
Pour aller plus loin, je vous recommande vivement la lecture du livre ["ITIL: Pour un système informatique optimal" de Christian Dumont](http://www.amazon.fr/gp/product/2212121024?ie=UTF8&tag=sebbrochet-21&link_code=as3&camp=2522&creative=9474&creativeASIN=2212121024).   

Vous qui travaillez dans des PME, avez-vous mis en place une partie des bonnes pratiques ITIL ?   
Peut-être pratiquez-vous déjà ITIL sans le savoir ? :-)   
