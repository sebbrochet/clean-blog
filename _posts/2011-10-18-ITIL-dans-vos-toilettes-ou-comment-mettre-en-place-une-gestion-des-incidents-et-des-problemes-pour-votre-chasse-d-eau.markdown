---
layout: post
title: "ITIL dans vos toilettes..."
tags: BRICOLAGE HUMOUR ITIL
date:       2011-10-18 7:00:00
author:     "sebbrochet"
comments: true
---

...ou comment mettre en place une **gestion des incidents et des problèmes** pour votre chasse d'eau !  

Comme chacun le sait, la chasse d'eau est le centre de contrôle des toilettes. La **disponibilité** de cet élément est primordiale et doit être garantie à tout prix sous peine de **graves répercutions sur les utilisateurs**. Que faire quand un **incident** survient ? appliquer ITIL bien sûr ! ...  

![Chasse d'eau]({{ site.url }}/img/2011/chasse_d_eau_-_low.JPG)

Tout a commencé par un **rapport utilisateur** faisant état de fuites d'eau le long de l'évacuation de la cuvette des toilettes. Le service support a créé un **rapport d'incident** et fixé sa **priorité** en concertation avec l'utilisateur:  

* Un seul système de toilettes est touché et les toilettes restent malgré tout fonctionnelles. L'**impact** est donc relativement limité.
* Le débit est faible, il s'agit d'un filet d'eau. L'**urgence** est donc basse.

La **priorité** de résolution de cet **incident** est donc également basse. Le service support a tout de même noté la consommation supérieure à la normale en eau. L'équipe en charge de la gestion des incidents constate rapidement l'incident de visu.  

**L'incident est confirmé**. Le technicien dépêché sur place décide de **réinitialiser plusieurs fois le système**. Et après quelques utilisations de la chasse d'eau, la fuite d'eau disparait.  

Cependant, quelque temps plus tard, des rapports utilisateurs signalent un **incident du même type sur le même équipement**. Après consultation des procédures préconisées par le constructeur, le service incident décide de planifier une **opération de maintenance**.  
Les toilettes étant **redondées sur deux niveaux différents (actif/actif)**, le risque d'**impact sur la production** est jugé relativement faible. L'opération est tout de même réalisée pendant un **creux d'activité** pour être sûr de **supporter la charge** avec un seul système de toilettes en service.  

Le réservoir des toilettes est séparé de la cuvette et le joint qui assure l'étanchéité entre les deux est débarrassé du calcaire qui l'entoure. Malheureusement, **cette opération ne résout pas l'incident** qui est de nouveau rapporté très rapidement après.  

Le département Finance s"inquiète des **conséquences financières** et demande une **résolution rapide**.  

Le service incident **monopolise de nouvelles ressources et recoupe les différents éléments en sa possession**. Un élément attire leur attention: un bruit de remplissage d'eau se fait entendre de manière quasi-permanente même quand le réservoir est plein.  
Heureusement un **mécanisme de coupure** de l'arrivée d'eau a été mis en place par le constructeur du système de toilettes.  

![Robinet arrêt]({{ site.url }}/img/2011/robinet_d_arret_-_low.jpg)

Mais en verrouillant le robinet d'arrêt, **un autre incident survient**: le robinet laisse perler régulièrement une goutte d'eau en position fermée. Cette **solution de contournement** est vite écartée.  

Le service incident décide alors de procéder à de **nouveaux tests** pour mieux **identifier le ou les composants défectueux**.  
Le technicien en charge des tests remplit manuellement le réservoir jusqu'au-dessus du niveau de trop plein et constate le même type de fuite que celle remontée dans le rapport d'incident !  

Pour une **raison non encore identifiée**, le réservoir se remplit lentement jusqu'à ce que le niveau d'eau atteigne celui du trop plein et provoque un écoulement d'eau dans l'évacuation des toilettes.   

Après **analyse des dépendances entre les différents composants**, le **composant défectueux est identifié**. Il s'agit du robinet flotteur qui ne semble plus assurer sa fonction (verrouillage en position haute). Le responsable de la gestion des incidents décide de **faire un remplacement**. Le modèle d'origine n'est pas ou plus disponible, c'est un **modèle compatible** qui est installé rapidement, toujours pendant un creux d'activité.  

![Nouveau flotteur compatible]({{ site.url }}/img/2011/nouveau_flotteur_compatible_-_low.jpg)

**L'incident semble résolu**, aucun bruit de remplissage d'eau ne se fait plus entendre et l'écoulement d'eau n'est plus constaté.  

Le responsable de la **gestion des problèmes** est globalement satisfait, il a **une erreur connue**. Il souhaite néanmoins **identifier la cause première** car d'**autres systèmes du même type sont en production** et des **actions préventives** sont peut-être possibles.  
Le robinet flotteur d'origine est entièrement démonté, toutes les pièces montrent des zones avec des dépôts de calcaire.  

![Démontage robinet flotteur d'origine]({{ site.url }}/img/2011/demontage_robinet_flotteur_origine_-_low.jpg)

Mais la **cause du dysfonctionnement** n'est pas là. Après examen poussée de la pièce centrale, il s'avère que le soufflet qui assure l'étanchéité du robinet est déchiré. La répétition des ouvertures/fermetures aura eu raison de lui. C'est une **conséquence due à l'usure** et ce n'est pas réparable et visiblement pas évitable.  

![Souflet déchiré]({{ site.url }}/img/2011/souflet_dechire_-_low.JPG)

L'information est consignée, la **procédure d'échange de robinet flotteur est documentée** pour les prochains incidents du même type qui pourraient avoir lieu.  
Après **confirmation par l'utilisateur** à l'origine du rapport d'incident que l'incident ne se produit plus, **le rapport est clos**.  

Comme vous avez pu le constater, l'utilisation d'ITIL ne se limite pas aux infrastructures informatiques !  
Avez-vous eu également l'occasion de mettre en place ITIL dans un environnement "hors-norme" ?  