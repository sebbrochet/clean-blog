---
layout: post
title: "4 acteurs majeurs du Cloud Computing"
tags: AMAZON CLOUD_COMPUTING GOOGLE MICROSOFT SALESFORCE
date:       2010-01-12 7:00:00
author:     "sebbrochet"
comments: true
redirect_from:
  - /post/4-acteurs-majeurs-du-Cloud-Computing/
---

Le **Cloud Computing** (ou nuage de calcul) correspond à la fourniture de ressources informatiques à la demande sous forme d'un service facturé selon le volume consommé.
Voyons ensemble quelques acteurs majeurs et les caractéristiques principales de leurs offres.

# Plusieurs type de services

* IaaS (Infrastructure-as-a-Service) : fourniture du matériel (Firewall, routeur, serveurs, NAS/SAN)
* PaaS (Platform-as-a-Service) : Iaas + système d'exploitation et serveur d'applications
* SaaS (Software-as-a-Service) : Paas + applications
* Staas (Storage-as-a-Service) : Offre de stockage et/ou de fourniture de contenu à la demande (CDN).

#Les acteurs majeurs

![SalesForce]({{ site.url }}/img/2010/salesforce.png)

## [Salesforce - Force.com](http://www.salesforce.com/platform/)

* Le plus ancien, propose des offres depuis 2003 (API SForce).
* Cloud public uniquement.
* Eco-système d'applications [AppExchange](http://sites.force.com/appexchange/home) (800)
* Offre gratuite assez limitée
* Datacenters à l'étranger
* Vise essentiellement les Grands Comptes.

### Service de type PaaS

* Développement rapide à la souris pour assembler différentes briques.
* 2 langages sont proposés: [Apex](http://www.salesforce.com/fr/platform/application-development/apex-programming-language/) (java-like) et [Visualforce](http://www.salesforce.com/fr/platform/application-development/visualforce/) (xml-like).

### Service de type SaaS

* Logiciel pour gérer la relation client (GRC)
* SLA disponible mais variable selon les clients

### Base de données

* Intégrée à l'environnement de développement
* Gestion des tables et de leurs relations WYSIWYG


![AWS]({{ site.url }}/img/2010/amazon_web_services.png)

## [Amazon - Web Services (AWS)](http://aws.amazon.com/)

* Lancé en version complète en 2006 et mise à jour régulière depuis.
* Cloud public, aussi disponible en cloud privé.
* SLA disponible
* Basé sur [Xen](http://www.xen.org/).

### Service de type IaaS

* [Elastic Compute Cloud (EC2)](http://aws.amazon.com/ec2/) : intégration de machines virtuelles, existantes ou nouvellement créées via AWS

### Service de type PaaS

* [Elastic MapReduce](http://aws.amazon.com/elasticmapreduce/) : même calcul en parallèle sur de grosses quantité de données
* [Simple Queue Service (SQS)](http://aws.amazon.com/sqs/) : système de messagerie entre applications

### Service de type StaaS

* [Simple Storage Service (S3)](http://aws.amazon.com/s3/) : écriture et lecture de flux de données
* [Elastic Block Storage (EBS)](http://aws.amazon.com/ebs/) : disque dur privé pour la partie EC2
* [CloudFront](http://aws.amazon.com/cloudfront/) : offre CDN qui repose sur du contenu stocké sur S3

### Base de données

* [SimpleDB](http://aws.amazon.com/simpledb/) : services de base d'indexation et de recherche par clef
* [Relational Database Service](http://aws.amazon.com/rds/) : compatible MySQL

![GAE]({{ site.url }}/img/2010/google_app_engine.png)

## [Google - App Engine](http://code.google.com/appengine/)

* Lancé en avril 2008, mis à jour en avril 2009
* Cloud public uniquement.
* Offre gratuite conséquente (plusieurs millions de requêtes par mois)
* Orienté services web
* Pas de SLA, support via un forum public
* Beta (comme beaucoup de produits Google)
* Plus pour les startup que les Grands Comptes

### Service de type Paas

* 2 langages supportés: [java](http://www.java.com/fr/) et [python](http://python.org/)
* Beaucoup de limitations (durée des requêtes, restriction sur les API)

### Service de type SaaS

* [GMail](http://mail.google.com/mail?hl=fr)
* [Google Documents](http://docs.google.com/)

### Base de données

* Datastore (technologie propriétaire [BigTable](http://labs.google.com/papers/bigtable.html))
* Langage de requête SQL-like ([GQL](http://code.google.com/intl/fr/appengine/docs/python/datastore/gqlreference.html))

![AZURE]({{ site.url }}/img/2010/windows_azure.png)

## [Microsoft - Windows Azure](http://www.microsoft.com/windowsazure/)

* Le dernier sur les rangs, l'offre doit être disponible fin janvier 2010.
* Cloud public uniquement.
* Orienté services web ou traitement long
* Datacenter en Europe (Dublin et Amsterdam)
* SLA disponible, variable selon les services
* Eco-système d'applications avec une nouvelle version de Pinpoint

### Service de type PaaS

* Code .NET tournant au-dessus de Windows Server 2008 R2 uniquement
* Langages supportés (CLR, Java SDK, Ruby SDK)
* [AppFabric](http://msdn.microsoft.com/en-us/windowsserver/ee695849.aspx): connectivité et gestion d'identités
* Système de messagerie inter applications

### Service de type SaaS

* [Office Web Apps](http://windowslivewire.spaces.live.com/Blog/cns%212F7EB29B42641D59%2141451.entry?sa=294125608)

### Service de type StaaS

* [Blob Service](http://msdn.microsoft.com/en-us/library/dd135733.aspx) : stockage de texte et de données binaire.

### Base de données:

* [SQL Azure](http://www.microsoft.com/windowsazure/sqlazure/) : SGBDR, compatible SQL Server

# Conclusion

Comme nous pouvons le voir, chaque acteur fait évoluer son offre et l'amène à maturité.  
2010 devrait donc être l'année du Cloud, à condition que les réserves sur la sécurité (disponibilité et confidentialité notamment) soient levées.  

Avez-vous déjà utilisé les services fournis par ces différents acteurs ?  
Quel bilan en tirez-vous ?  