---
layout: post
title: "20 conseils pour l'implémentation de votre infrastructure"
tags: CONSEILS IMPLEMENTATION INFRASTRUCTURE 
date:       2009-12-01 7:00:00
author:     "sebbrochet"
comments: true
redirect_from:
  - /post/20-conseils-pour-l-implémentation-de-votre-infrastructure
---

Ça y est, [vous avez bouclé la conception]({{ site.url }}/2009/11/24/15-conseils-pour-la-conception-de-votre-infrastructure/) et vient le moment de penser à l'implémentation !  

Voici quelques conseils personnels pour vous aider à éviter certains pièges.  

# Prévoir une étape de prototypage
Théoriquement la pratique et la théorie c'est pareil mais en pratique c'est différent.
Un prototype va permettre de valider certains choix en terme de compatibilité, de performance et globalement d'adéquation aux besoins. Pour limiter les coûts, on pourra éventuellement utiliser des machines virtuelles au début avant de passer plus tard sur des serveurs physiques.

# Sélectionner soigneusement vos partenaires
La réussite tient souvent à la qualité des personnes qui vous entourent. Assurez-vous de sélectionner des partenaires qui connaissent votre métier et ses contraintes de manière à ce qu'ils s'adaptent à vos besoins et non l'inverse.

# Visiter le site d'hébergement
Tous les hébergeurs professionnels ne se valent pas. Il est important de vous faire votre propre idée sur l'emplacement du site, la sécurité des accès, la qualité des infrastructures de climatisation, les raccordements électriques et bande passante, l'autonomie en cas de coupure, les procédures en place pour les interventions sur site, les procédures de maintenance sur les équipements de l'hébergeur, les niveaux de service garantis, la présence si besoin de personnel sur site en 24/7, ...

# Sélectionner un site proche de vous et facile d'accès
Plus le site est proche de vous et plus il sera simple de s'y déplacer pour l'installation des différents équipements. Comme vous serez amené à vous y rendre très souvent c'est autant de temps de gagné.

# Ne pas calculer au plus juste
Certains paramètres sont plus facilement modifiables après coup que d'autres mais il y a toujours un coût induit et un délais de mise en place qui peuvent être problématiques. Ménagez de la marge dans le choix de la taille et le nombre des baies, la fourniture électrique, la bande passante, ...

# Sélectionner des équipements intelligents
Des équipements interrogeables et contrôlables à distance peuvent vous faire économiser beaucoup de temps et d'argent et vous sortir de situations délicates. Il y a un surcoût au départ mais il est rapidement amorti, par exemple dans le choix de bandeaux électriques intelligents ou dans des cartes d'accès distant à insérer dans vos serveurs.

# Sélectionner du matériel standard et évolutif
Choisir du matériel standard, c'est un plus grand choix de composants pour faire jouer la concurrence. Si le matériel est évolutif, il accompagnera plus facilement les changements de votre SI.

# Sélectionner des OS supportés par les constructeurs
Certains systèmes d'exploitation ne sont pas supportés par les constructeurs qui ne fournissent pas les pilotes nécessaires au bon fonctionnement du matériel. Et certains systèmes d'exploitation n'implémentent pas complètement les spécifications des constructeurs. On veillera particulièrement au choix des OS pour exploiter des SAN, des lecteurs de bandes, les nouvelles architecture multi-coeurs, les grandes quantités de mémoire vive, ...

# Redonder les services et les composants
En doublant et en exploitant des composants telles que les alimentations électriques ou les interfaces réseau, on évite les coupures de service en cas de panne et on facilite la maintenance.

# Éviter les disques durs dans les serveurs
Les disques durs et les alimentations sont les composants qui tombent en moyenne en panne le plus souvent. En utilisant le démarrage en réseau (par ex: BOOTP) et le stockage des données à distance on limite le volume des pannes.

# Placer chaque sous-système dans sa propre DMZ
Une DMZ correspond à un sous-réseau dédié sur lequel des paramétrages spécifiques peuvent être réalisés.

# Distinguer les DMZ publiques et privées
Les DMZ publiques qui accèdent à l'extérieur de la plateforme seront les plus vulnérables aux attaques. Elles ne doivent pas héberger de données de valeur pour l'entreprise et doivent avoir des accès limités. Les DMZ privées ont plus de droits et communiquent avec les systèmes hébergeant les données métier. Mais elles ne doivent pas accéder directement à l'extérieur. On utilisera dans ce cas une DMZ publique qui servira de proxy.

# Séparer les flux applicatifs et administratifs
Les flux applicatifs correspondent aux données échangées par les applications métier. Les flux administratifs correspondent aux données échangés par les applications système. En séparant ces deux flux, on évite qu'un des deux influe sur l'autre (meilleure disponibilité), que des données administratives soient accessibles par les applications métier (meilleure confidentialité).

# Utiliser un équipement réseau dédié par type de flux
Ce qui permet en cas de coupure du réseau administratif ne pas avoir en même temps une rupture de service et en cas de coupure du réseau applicatif d'intervenir sur les équipements via le réseau administratif.

# Limiter les échanges entre DMZ
Les échanges entre DMZ doivent être limités aux besoins métier pour le réseau applicatif. Tous les échanges qui ne sont pas nécessaires doivent être désactivés.

# Mettre en place des équipements de répartition de charge
Pour absorber les variations brusques de charge et pour utiliser équitablement tous les équipements afin d'éviter l'usure prématurée d'un équipement spécifique qui serait plus utilisé que les autres. Si les sous-systèmes ont été conçus pour fonctionner en parallèle, cette étape se passe relativement bien.

# Mettre en place des équipements à tolérance de panne
Suite à une panne ou dans le cadre d'une maintenance, un composant peut ne plus être opérationnel. Un équipement à tolérance de panne, détectera la non disponibilité d'un composant et basculera automatique sur le composant disponible prévu à cet effet. Quand les 2 composants sont actifs en même temps, on parle d'actif/actif, quand seulement un des 2 est actif à un moment donné, on parle d'actif/passif.

# Privilégier les fonctions implémentées au niveau matériel plutôt que logiciel
L'industrie électronique produit des composant plus fiables que l'industrie logicielle même si la frontière entre matériel et logiciel est de plus en plus floue dans certains matériels mixtes (ex: équipements réseau avec sous-systèmes virtuels). Les performances sont en général meilleures avec du matériel dédié qu'avec des applications s'exécutant sur des systèmes d'exploitation non spécialisés.

# Faire le choix entre internalisation et externalisation au cas par cas
Il est important de conserver en interne ce qui touche au savoir faire de la société et où les ressources qualifiées sont disponibles. Dans les autres cas, la question peut se poser en se basant sur le niveau de service à rendre et sur les coûts afférents.

# Prévoir un accès VPN pour accéder au réseau d'administration
L'accès au réseau d'administration doit être limité et passer par une liaison cryptée. Un VPN site-à-site entre l'entreprise et la plateforme répond à ce besoin.


Comment s'est passée votre dernière implémentation ?  
Avez-vous aussi des conseils à partager ?