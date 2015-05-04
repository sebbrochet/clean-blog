---
layout: post
title: "Configuration Management sous Windows"
subtitle:   "mythe ou réalité ?"
tags: DEVOPS WINDOWS
date:       2015-05-04 10:00:00
author:     "sebbrochet"
header-img: 
comments: true
---

### Introduction

Le **Configuration Management** dans un contexte *DevOps* correspond à la *gestion automatisée* de la *configuration des différents composants logiciels* qui sont installés au-dessus d'un système d'exploitation de base. Cette discipline n'est pas nouvelle et il existe de nombreux outils qui facilitent cette gestion. Cependant, historiquement, ces outils ont d'abord ciblé les environnements de type **Unix** (comme linux par ex.). Et ce n'est que récemment que nous avons pu voir des outils et des technologies spécifiques à **Windows** apparaître.

### Les composants à mettre en oeuvre

* un **langage de description** des configurations
* un **gestionnaire de paquets** (package manager)
* des **applications packagées** au bon format et configurables avant l'installation, à partir de switches ou de fichiers de paramètres
* un **système d'orchestration** des changements de configurations

### Des caractéristiques spécifiques à Windows

* Dans un environnement de type **Unix**, l'installation et la configuration des différents composants du système d'exploitation se fait traditionnellement en ligne de commande. Un grand nombre d'outils, fournis avec le système, permettent de modifier certaines valeurs mais il est également possible d'éditer et de modifier directement certains paramètres dans les fichiers de configuration correspondants. Tandis que sous **Windows**, la plupart de ces actions se font via une interface graphique.
* Là où sous **Unix**, ce sont des **fichiers de configuration au format texte** qui sont manipulés, sous **Windows**, une grosse part du paramétrage se fait via la **Registry**.
   * La Registry est une base de données clefs/valeurs stockée au **format binaire** et les modifications de celles-ci se font via une API ou via l'import de fichier au format texte avec l'extension *.reg*.
* Sous **Unix**, chaque distribution propose son système et son format de packages (apt/deb pour Debian, yum/rpm pour RHEL, ...). C'est d'autant plus facile qu'une grosse partie des applications sont opensource et ne nécessitent pas de procédures d'activation ou d'enregistrement spécifiques.
* Sous **Windows**, la majeure partie des applications et des composants qui sont installés, sont propriétaires. Leur installation nécessite, le plus souvent, la saisie de clefs d'activation et/ou d'un enregistrement nécessitant une connexion internet. Ce qui explique qu'il n'existe pas à ce jour de gestionnaire de packages pour Windows contenant l'ensemble des applications propriétaires.

### Des outils communs et spécifiques à la fois

Sous Windows, le langage de scripts qui permet d'interagir avec l'ensemble de l'OS s'appelle **PowerShell**. Il est donc possible d'automatiser l'exécution de certaines tâches avec ce langage. Cependant,  PowerShell est un langage **impératif** qui décrit les tâches à réaliser sans spécialement tenir compte de l'état du système avant leur exécution. Ce qui signifie que si un script PowerShell est exécuté 2 fois de suite, les actions correspondantes seront également exécutées 2 fois, même si la 2ème exécution n'est pas nécessaire car tout a déjà été réalisé lors de la 1ère exécution. Certains langages, spécifiques au Configuration Management, permettent de n'exécuter que les actions qui sont nécessaires pour assurer un **état de configuration donné**. On parle alors de langage **idempotent**.
Ce soucis avec PowerShell n'a bien sûr pas échappé à Microsoft, qui a conçu une technologie spécifique pour répondre à ce besoin: **Desired State Configuration**

#### Desired State Configuration (DSC)

Cette technologie s'appuie sur le Windows Management Framework (WMF), sur des standards ([CIM](http://fr.wikipedia.org/wiki/Common_Information_Model), [WSMAN](http://fr.wikipedia.org/wiki/WS-Management)) et des protocoles spécifiques à Windows ([WMI](http://fr.wikipedia.org/wiki/Windows_Management_Instrumentation), [WinRM](https://msdn.microsoft.com/en-us/library/aa384426%28v=vs.85%29.aspx)).

DSC se compose de 3 éléments:

* Local Configuration Manager (LCM)
  * Ce module correspond à l'*agent* qui s'exécute sous la forme d'un service et qui vérifie régulièrement la cohérence de la configuration de la machine
  * Une configuration DSC peut soit être *poussée* (push) vers la machine cible ou *récupérée* (pull) à partir de la machine cible si un *gestionnaire de téléchargement* est disponible
* DSC Resources
   * Implémentées en **PowerShell**, ces éléments correspondent à des *configurations* qui peuvent  être appliquées, enlevées ou testées.
* Configuration DSL
   * Cet élément correspond à des extensions de langage au-dessus de **PowerShell**

#### OneGet - Un gestionnaire de paquets (pour les commander tous)

[OneGet](https://github.com/OneGet/oneget) est un gestionnaire de paquets **unifié**. Unifié, au sens où il encapsule l'accès à différents gestionnaires de paquets:

* [NuGet](https://www.nuget.org/)
   * Fournit des librairies de **code source** et s'intègre à Visual Studio
* [Chocolatey](https://chocolatey.org/)
   * Basé sur la technologie **NuGet**, fonctionne de manière décentralisé et regroupe les différentes sources de téléchargements de composants logiciels au **format binaire**
* [PowerShellGet](http://blogs.msdn.com/b/mvpawardprogram/archive/2014/10/06/package-management-for-powershell-modules-with-powershellget.aspx)
   * Fournit des composants **PowerShell** et des commandes pour gérer les modules au-dessus de **OneGet**

![powershellget](/img/2015/powershellget.png)

#### Les outils de Configuration Management "classiques"

Ce sont les outils déjà connus et utilisés dans le monde Unix qui, peu à peu, prennent en charge l'environnement Windows.

Par ordre d'ancienneté:

* CFEngine
* Puppet
* Chef
* Ansible
* Saltstack

##### CFEngine

CFEngine fournit des primitives pour gérer:

* les **services** Windows
* la **Registry**
* l'ajout de **rôles**

Mais il ne supporte pas directement la technologie **DSC**.

##### Puppet

Depuis décembre 2014, Puppet fournit un [module officiel](https://forge.puppetlabs.com/puppetlabs/windows) avec des primitives spécifiques à Windows:

* gestion de la **Registry**
* exécution de scripts **PowerShell**
* Redémarrage de la machine
* gestion des **permissions**
* ajout des **rôles**
* activation de **sites web avec IIS**

Cependant il faut utiliser un [module opensource](https://forge.puppetlabs.com/msutter/dsc) disponible sur la Forge de Puppet pour gérer la technologie **DSC**.
 
##### Chef

Chef a travaillé en partenariat avec Microsoft pour intégrer la technologie DSC dans son produit. Dans la dernière version de Chef, il est possible d'utiliser directement dans une recette Chef les **DSC Resources** disponibles au niveau de l'OS. Le [travail n'est pas totalement finalisé](https://www.chef.io/solutions/windows/) mais est sur la bonne voie.

##### Ansible

Ansible ne s'exécute pas sous Windows mais contient des modules spécifiques à cet environnement:

* Utilisation du package manager **chocolatey**
* ajout de **rôles**
* gestion des **utilisateurs**
* gestion des **groupes**
* installation d'installeurs au format *MSI*
* gestion des **services**
* gestion des **mises-à-jours de sécurité**

Le support de la technologie DSC est fourni par un [module opensource](http://hindenes.com/trondsworking/2015/02/20/dsc-ansible/).

##### Saltstack

Seulement une partie des composants de Saltstack s'exécute sous Windows. Il s'agit uniquement de l'agent (*salt minion*) en charge de vérifier régulièrement l'état de la machine et de récupérer et installer les modifications à partir du serveur maître (*salt master*).

Saltstack permet de stocker les applications à installer dans un [espace dédié](http://docs.saltstack.com/en/latest/topics/windows/windows-package-manager.html) et joue le rôle de gestionnaire de paquets.

#### Conclusion

Le Configuration Management ne se fait pas encore avec le même confort sous Unix et Windows. Mais depuis quelques mois, de plus en plus d'outils prennent en charge les spécificités de l'environnement Windows et Microsoft [met les bouchées doubles](http://blogs.msdn.com/b/powershell/archive/2014/12/10/wmf-5-0-preview-defining-quot-experimental-designs-quot-and-quot-stable-designs-quot.aspx). Gageons que d'ici la fin de l'année, ce support se sera étoffé. Rendez-vous est donc pris pour en reparler à ce moment là !