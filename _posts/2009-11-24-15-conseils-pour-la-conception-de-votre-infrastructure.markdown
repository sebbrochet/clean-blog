---
layout: post
title: "15 conseils pour la conception de votre infrastructure"
tags: CONCEPTION CONSEILS INFRASTRUCTURE 
date:       2009-11-24 7:00:00
author:     "sebbrochet"
comments: true
redirect_from:
  - /post/15-conseils-pour-la-conception-de-votre-infrastructure
---

La conception d'une infrastructure équilibrée et conforme aux besoins demande un peu de préparation.

Je vous livre ici quelques conseils issus de mes lectures, de mes discussions avec mes collégues et de mon expérience parfois douloureuse ;-)

# Bien identifier et dimensionner les besoins métiers
La raison d'être d'une infrastructure est de répondre aux besoins fonctionnels.
En identifiant bien en amont les besoins et en les dimensionnant correctement, on limite les surcoûts et on augmente la satisfaction client.

# Répartir et équilibrer les fonctions sur plusieurs sous-systèmes
L'adage nous dit qu'il ne faut pas mettre tous ses œufs dans le même panier. Dans notre cas, cela permet de ne pas perdre tous les services en même temps en cas de panne et assure une utilisation plus cohérente des différentes ressources.

# Limiter le nombre de configurations distinctes
Chaque configuration a un coût en conception, déploiement et exploitation. En limitant le nombre de configurations différentes on réduit ces coûts et on simplifie le travail d'exploitation ce qui est bénéfique pour la réduction des pannes.

# Inclure un sous-système dédié aux développements
Les développeurs ont besoin d'un environnement qui se rapproche de l'environnement de production. Dans la mesure où les applications ne sont pas stables, il est préférable que cet environnement n'interfère pas avec la production.

# Inclure un sous-système dédié aux tests
L'assurance qualité se fait aussi dans un environnement proche de la production mais avec des applications qui sont quasi stables. Un environnement dédié permet de ne pas ralentir les développements et ne pas interférer avec la production.

# Intégrer un système de sauvegarde
Une sauvegarde régulière permet de se prémunir d'une perte de données. Il faut bien identifier les données à sauvegarder, le dimensionnement de la zone de stockage et la fréquence des sauvegardes. Attention aussi aux systèmes qui ne peuvent pas être arrêtés et qui doivent donc être sauvegardés à chaud.

# Intégrer un système d'archivage
Un système d'archivage permet de conserver plusieurs sauvegardes. Certaines d'entre elles doivent sortir régulièrement de la plateforme pour servir en cas de sinistre majeur.

# Sélectionner ou concevoir des applications qui montent facilement en charge
Les besoins évoluent dans le temps et le SI doit pouvoir suivre ces besoins sans remettre en cause toute l'architecture. L'ajout de nouvelles ressources (mémoire, disques durs, serveurs, bande passante, ...) doit permettre aux applications de s'adapter à des demandes plus importantes.

# Privilégier les solutions sur étagère plutôt que les développements internes
Une solution sur étagère est en général plus mature qu'une solution développée en interne. Elle est moins coûteuse à mettre en oeuvre si elle répond en grande partie aux besoins et si elle est un minimum configurable.

# Mettre en place un watchdog pour vos applications
Les applications ne sont pas exemptes de défauts. Pour qu'un défaut ne soit pas synonyme de rupture de service, un système appelé watchdog peut surveiller l'état des applications et les relancer quand leur comportement sort des limites autorisées.

# Limiter l'utilisation des bases de données relationnelles
Les bases de données relationnelles sont très utiles pour stocker de gros volume de données liées entre elles. Par contre, la lecture et surtout l'écriture de ces données sont très lentes comparées à un accès en mémoire vive. Pour avoir de meilleurs performances, il faut utiliser d'autres moyens de stockage (cache en mémoire vive, [cache en réseau](http://memcached.org/), [bases de données non relationnelles](http://fr.wikipedia.org/wiki/NoSQL), ...)

# Utiliser des protocoles de communication standards et ouverts
L'utilisation de protocoles tels que TCP, HTTP ou [SOAP](http://www.w3.org/TR/soap12/)  réduit les problèmes d'interopérabilité, tout en autorisant l'échange de données structurées.  Cela permet aussi d'avoir plus de choix dans la sélection du matériel et des logiciels.

# Eviter les points uniques de défaillance (SPOF)
Un point unique de défaillance implique une rupture de service en cas de panne. S'il ne peut être éviter, il faut mitiger son effet par la mise en place d'équipements de secours.

# Eviter les flux cryptés externes qui traversent les équipements réseaux
Un flux crypté externe qui traverse un équipement réseau ne peut pas être analysé par ce même équipement. Une connexion HTTPS entre un client externe et un serveur web ne doit pas, par exemple, être terminée sur le serveur web mais plutôt sur l'équipement réseau en entrée de plateforme.

# Faire faire une revue de la conception par ses pairs :-)
Il est très facile de passer à côté d'un élément important. C'est souvent en présentant et en expliquant les raisons qui ont conduit à faire certains choix que l'on s'aperçoit que des alternatives moins onéreuses existent.

Avez-vous aussi des conseils à partager ?
Avec le recul et si c'était à refaire, qu'auriez-vous conçu différemment et comment ?

