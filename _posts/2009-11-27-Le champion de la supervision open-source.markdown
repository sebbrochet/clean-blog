---
layout: post
title: "Le champion de la supervision open-source"
tags: NAGIOS NAGIOSCHECKER NAGVIS OPENSOURCE SUPERVISION
date:       2009-11-27 12:00:00
author:     "sebbrochet"
comments: true
redirect_from:
  - /post/Le-champion-de-la-supervision-open-source
---

Quand on parle de supervision, un nom de logiciel vient tout de suite à l'esprit.  
Ce logiciel, c'est [Nagios](http://www.nagios.org/).

Nagios est utilisé par les plus grands pour superviser des parcs de plusieurs milliers de machines. Allié à des outils comme [Nagios Checker](http://code.google.com/p/nagioschecker/) et [NagVis](http://www.nagvis.org/), il offre une grande visibilité sur votre infrastructure.

**Vous êtes assuré d'être averti dans les plus bref délais en cas d'anomalie**.

Nagios est accessible au travers d'une interface web qui permet de voir l'état des paramètres vitaux de votre plate-forme. Les forces principales de Nagios sont son ouverture et sa grande souplesse de configuration.

Chaque test qu'il réalise correspond à l'appel d'un script. De nombreux scripts sont déjà fournis en standard mais rien ne vous empêche d'écrire vous même un script spécifique dans le langage de votre choix.

Nagios est par ailleurs livré pré-installé dans des distributions comme [FAN](http://fannagioscd.sourceforge.net/drupal/) (Fully Automated Nagios) ou des outils comme [Centreon](http://www.centreon.com/).

![nagios]({{ site.url }}/img/2009/nagios-screenshot.png)

[Nagios Checker](http://code.google.com/p/nagioschecker/) est un greffon pour Firefox. Il affiche en permanence, en bas de la fenêtre principale du navigateur, l'état de vos services.  
**Il change de couleur et produit un son en cas de changement d'état**, ce qui ne manquera pas d'attirer votre attention pour vous permettre d'intervenir très rapidement.

![nagios]({{ site.url }}/img/2009/nagios-checker.png)

[NagVis](http://www.nagvis.org/) est un greffon à Nagios **pour représenter les états des services au-dessus d'une image de son choix**.  
Cela permet de se rendre compte d'un seul coup d'œil de l'état général de votre plateforme et ce sera du plus bel effet sur un écran haute définition accroché au mur.

![nagios]({{ site.url }}/img/2009/nagvis.jpg)

# Conclusion
Nous n'avons fait qu'effleurer les possibilités de Nagios et les moyens de l'étendre. Pour allez plus loin, vous pouvez vous rendre sur le site [NagiosExchange](http://www.nagiosexchange.org/), dédié aux  greffons pour Nagios.

Pour finir, je vous conseille la lecture de ["Nagios - Au coeur de la supervision Open Source"](http://www.amazon.fr/gp/product/2746046032?ie=UTF8&tag=sebbrochet-21&link_code=as3&camp=2522&creative=9474&creativeASIN=2746046032) d'Olivier Jan. Ce livre très concret et facile d'accès vous permettra d'appréhender tout ce que Nagios peut vous apporter. Il vous indiquera aussi comment l'intégrer à d'autres outils que vous avez déjà installés ou prévoyez d'installer.

Quelle solution de supervision utilisez-vous pour votre plateforme ?
En êtes-vous satisfait ?
