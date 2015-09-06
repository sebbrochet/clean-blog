---
layout: post
title: "VMware et les conteneurs"
subtitle:   "Ca s'annonce plutôt bien"
tags: VMWARE CONTENEURS DOCKER
date:       2015-09-06 17:00:00
author:     "sebbrochet"
header-img: "img/2015/vmworld_2015.jpg"
comments: true
---


### Introduction

Reconnaissons-le, **Docker** est *génial*. Il a démocratisé l'usage des **conteneurs** en fournissant un ensemble d'outils très simples et intégrés pour créer, stocker et exécuter des applications sous forme de conteneurs.

Un autre outil a aussi révolutionné en son temps la création, le stockage et l'exécution de **machines virtuelles**. Cet outil, c'est **vSphere** de VMware.

### La fin des machines virtuelles ?

On a enterré un peu vite le vieux lion en commençant par prédire le remplacement des VM, **jugées trop lourdes**, par des conteneurs. La prophétie aurait pu se réaliser si les conteneurs proposaient le même niveau d'étanchéité qu'une machine virtuelle. Mais même en [utilisant plusieurs techniques](https://docs.docker.com/articles/security/) (AppArmor, SELinux, GRSEC, capabilities ...) ce n'est toujours pas le cas et c’est nettement [plus complexe](https://benchmarks.cisecurity.org/tools2/docker/CIS_Docker_1.6_Benchmark_v1.0.0.pdf) à mettre en oeuvre. Et au final, il n'est pas possible de faire du multi-tenant en toute sérénité.

Les [outils de gestion des conteneurs](http://panamax.io/) restent assez basiques si on les compare à vCenter:

* Il manque encore un système fiable de **migration à chaud** d'un conteneur entre 2 hosts différents ( => **vMotion**)
* Un équilibrage **dynamique** des conteneurs sur différents hosts en fonction de la charge CPU et mémoire serait bien aussi (=> **DRS**).  

Tous ces points cantonnent souvent **l'usage des conteneurs aux phases de développement et de tests**.

### La réponse de VMware

C'est pourquoi j'ai suivi avec beaucoup d'intérêt la réaction de VMware à la menace <del>fantôme</del> posée par les conteneurs. VMware a répondu il y a quelques mois de manière plutôt subtile sous la forme du [projet **Bonneville**](https://blogs.vmware.com/cloudnative/introducing-project-bonneville/). Ce projet permet d'intégrer **nativement** un conteneur au sein de l'architecture vSphere/ESX, tout en obtenant des temps de démarrage et une empreinte mémoire très faibles et en conservant les facilités (vMotion, DRS, ...) auxquelles nous sommes habitués avec les VM.

Le [dernier salon VMWorld](http://venturebeat.com/2015/08/31/vmware-launches-vsphere-integrated-containers-and-the-photon-platform/) a vu la poursuite et l'intégration de cet effort sous la forme de 2 plateformes, **pour le moment au stade de *Technology Previews***, à même de gérer les conteneurs:

* vSphere Integrated Containers: pour l'utilisation ponctuelle de conteneurs au milieu de VM classiques
* Photon Platform: pour exécuter spécifiquement un grand nombre de conteneurs.

### Le cloud (privé) dans tout ça ?

C'est très prometteur pour faciliter l'adoption des conteneurs en production dans le cadre d'un cloud **privé**:

* Les équipes Ops conservent le produit qu'elles connaissent bien et apprécient (vCenter)
* Les investissements (licences, serveurs, SAN, ...) conséquents et déjà réalisés sont valorisés
* On a un standard partagé entre les Dev et les Ops pour **packager** une application **et ses composants**.

### Un petit mot sur le cloud public

[Amazon](https://aws.amazon.com/fr/documentation/ecs/), [Google](https://cloud.google.com/container-engine/) et plusieurs autres ne pouvaient pas laisser passer le train des conteneurs sans réagir. Chacun d'eux propose ainsi sa déclinaison du *cloud à base de conteneurs*, avec des outils plus ou moins standards qu'ils tentent d'imposer. Cependant les limitations évoquées plus haut restent d'actualité.

Il est aussi intéressant de constater qu'au niveau de la tarification, il n'y a  pas d'innovation:

* Le coût d'utilisation des conteneurs correspond aux **coût des machines virtuelles associées à leur exécution** !

### Conclusion

VMware n'a pas encore annoncé de date définitive pour la disponibilité de ces évolutions au grand public. On peut toutefois tabler sur une sortie dans le courant de l'année 2016.

Ce qui laisse donc encore quelques mois aux équipes Dev et Ops pour [se préparer et travailler ensemble](http://blog.sebbrochet.com/2015/05/01/BBL-DevOps-chez-vous/) sur une usine logicielle complète à base de conteneurs !
