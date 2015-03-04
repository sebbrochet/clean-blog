---
layout: post
title: "Dans la supervision, il y a des cactus"
tags: CACTI OPENSOURCE SUPERVISION 
date:       2009-12-04 7:00:00
author:     "sebbrochet"
comments: true
---

[Nagios est le champion de la supervision open source]({{ site.url }}/2009/11/27/Le%20champion%20de%20la%20supervision%20open-source/). Mais il partage la place avec un autre outil d'exception : **Cacti**.

[Cacti](http://www.cacti.net/) permet de représenter l'évolution de n'importe quel paramètre au cours du temps. Vous pouvez aussi zoomer sur une portion de courbe et exporter les valeurs au format CSV pour un traitement avec un outil externe. C'est particulièrement utile pour déterminer les tendances, anticiper des pannes ou comparer deux états dans le temps.

![Cacti]({{ site.url }}/img/2009/cacti_small.jpg)

Dans le cas d'une infrastructure, on pourra représenter:  

* pour chaque serveur: la charge CPU, la mémoire vive consommée, l'espace disque local utilisé
* pour chaque interface réseau: les débits des flux reçus et envoyés
* pour chaque source d'alimentation: l'intensité délivrée
* pour chaque équipement qui le supporte: la température de fonctionnement
* ...

Il est aussi possible d'utiliser Cacti pour représenter des indicateurs métier:  

* le nombre de visiteurs sur votre site web
* le nombre de commandes par heure sur votre boutique en ligne
* le nombre de tickets ouverts chaque heure à votre service support
* ...

De même, vous pourrez identifiez l'utilisation en interne de vos ressources en représentant:  

* la consommation de bande passante en entrée et en sortie de la plateforme
* le nombre d'utilisateurs sur votre progiciel de gestion de la relation client
* le nombre de mails reçus et envoyés
* ...

**On prêtera particulièrement attention aux variations brusques qui sont souvent le signe d'une anomalie**.  
Et comme faute de ressources, tout ne peut être vérifié avec un outil comme Nagios, c'est un très bon indicateur.

J'espère que cette petite introduction vous a permis de mieux comprendre ce que Cacti peut apporter à votre solution de supervision et voir s'il correspond à vos besoins.


Quels outils utilisez-vous pour anticiper la demande sur votre plateforme ?
Correspondent-ils à vos besoins, en êtes-vous satisfait ?