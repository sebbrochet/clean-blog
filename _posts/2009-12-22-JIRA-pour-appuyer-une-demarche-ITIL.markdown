---
layout: post
title: "JIRA pour appuyer une démarche ITIL"
tags: ITIL JIRA OPENSOURCE PME
date:       2009-12-22 7:00:00
author:     "sebbrochet"
comments: true
---

Quand se pose le choix d'un outil pour appuyer la mise en place du référentiel ITIL, plusieurs possibilités se présentent:

1. Utiliser un outil spécialisé et adapté à plusieurs processus ITIL
2. Utiliser un outil plus générique mais configurable

Les logiciels dans le premier cas, sont en général assez coûteux et potentiellement complexes à mettre en œuvre.  

Dans le deuxième cas, les fonctionnalités seront réduites et ne conviendront pas forcément à tous les besoins.  

[JIRA](http://www.atlassian.com/software/jira/)  est un outil connu et utilisé pour la gestion des bugs dans de nombreux projets informatiques.
Sa grand flexibilité et la possibilité de créer des écrans ou des workflows personnalisés permet de l'utiliser dans d'autres contextes telle que la gestion de certains processus ITIL comme nous allons le voir dans ce qui suit.

![JIRA]({{ site.url }}/img/2009/jira_itil.png)

Les explications qui suivent s'adaptent plus à ITIL V2, plutôt axé sur l'opérationnel qu'à ITIL V3 qui porte plus l'accent sur la stratégie.
Nous traiterons donc **principalement des processus de soutient des services** tout en évoquant rapidement les processus liés à la **fourniture de services**.

# Gestion de Configuration

Possible mais pas forcément le mieux intégré à JIRA.
Un CI correspondra à un ticket avec éventuellement quelques champs personnalisés.
Le ticket est unique, peut être référencé et édité.

# Gestion des Incidents

S'intègre très bien à JIRA.
Un incident est plus ou moins équivalent à un bug et suit un workflow similaire.

2 possibilités:

* Incident = type de ticket
* Incident = projet dédié.

Dans le premier cas, un seul projet JIRA contient l'ensemble des tickets. C'est adapté pour un produit ou un service à destination des clients.
Par contre, pour gérer les Incidents relatifs à plusieurs produits, un projet dédié convient mieux.

# Gestion des Problèmes

On suit le même principe que la gestion des Incidents.
Des problèmes peuvent être créés directement à partir d'un Incident dans la version de base de JIRA (fonction clone).  

Il est aussi possible de créer un nouveau ticket pour le problème et référencer les tickets correspondants aux incidents récurrents à l'origine de celui-ci.

# Gestion des Changements

Ce processus requiert un peu plus de configuration.  
On peut se contenter dans un premier temps du workflow de base et créer uniquement une entrée de type RFC (Request For Change).  
Mais la gestion des Changements implique une procédure de validation à plusieurs niveaux qui nécessite un workflow spécifique.  

C'est tout à faut possible en suivant [les instructions décrites dans cette page](http://confluence.atlassian.com/display/CONFEVAL/Using+JIRA+for+Change+Management).  

Des champs personnalisés pourront être ajoutés pour détailler le changement (Description, Impact, Raisons, Risques, Coûts, ...).  

Le contenu de la revue Post-implémentation (P.I.R) pourra se faire sous forme de commentaire dans le ticket de changement.  

# Gestion des Mises en Production

Une Mise en Production correspond à un ticket maître qui référence des sous-tickets. Chaque sous-ticket correspond à un déploiement.  

Dans la mesure où un ticket ne peut être assigné qu'à une personne à la fois, si pour un même déploiement plusieurs tâches doivent se faire en parallèle, il faudra alors créer à chaque fois un ticket spécifique.  

# Gestion des Niveaux de Service

Pour les activité Planifier, Négocier, Signer et Contrôler, JIRA n'apporte pas de plus-value.  

# Gestion de la Capacité

Ce processus nécessite des [métriques sur l'utilisation des infrastructures]({{ site.url }}/2009/12/04/dans-la-supervision-il-y-a-des-cactus/).  
Possibilité de s'appuyer sur les Incidents pour créer des demandes de Changements (ajout d'un serveur, augmentation bande passante, ...).  

# Gestion de la Disponibilité

Ce processus nécessite des [rapports détaillés sur le bon fonctionnement des services]({{ site.url }}/2009/11/27/Le%20champion%20de%20la%20supervision%20open-source/).
JIRA n'apporte pas de réelle plus-value ici.  

**Gestion de la Continuité de Service, Gestion de la Sécurité, Gestion de l'Infrastructure TIC, Gestion financière des Services Informatiques**  

JIRA n'apporte pas de réelle plus-value ici.

# Liens

[Pour un retour détaillé sur une implémentation](http://martinskemme.wordpress.com/2009/02/01/using-jira-to-support-itil-processes/)

# Conclusion

JIRA s'adapte aux processus de soutient des services informatiques. Pour les autres processus, il n'apporte pas vraiment de plus-value.  
Dans le cadre d'une infrastructure avec un nombre réduit de tickets à gérer, c'est un choix qui permet de faire des économies tout en fournissant des gains de productivité réels.  


Avez-vous aussi utilisé des logiciels génériques pour faciliter la mise en place du référentiel ITIL ?  
Quel bilan en tirez-vous ?  