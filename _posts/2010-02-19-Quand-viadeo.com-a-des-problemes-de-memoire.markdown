---
layout: post
title: "Quand viadeo.com a des problèmes de mémoire"
tags: EXPLOITATION INFRASTRUCTURE ITIL OPENSOURCE SUPERVISION
date:       2010-02-19 7:00:00
author:     "sebbrochet"
comments: true
---

C'était un soir comme tous les autres. J'étais face à mon ordinateur à surfer sur internet.  

J'active l'onglet [contenant mon tableau de bord viadeo](http://www.viadeo.com/tableaudebord/accueil/), je raffraichis machinalement la page quand soudain j'obtiens une page d'erreur **HTTP 500 et un message Out of Memory !**

![VIADEO]({{ site.url }}/img/2010/viadeo_out_of_memory_stack_trace.png)

A y regarder de plus près, nous avons là une longue pile d'exécution qui pour des personnes comme moi se lit tel un roman ;-) Je retrouve les "usual suspects" (**apache, tomcat, memcache, ...**) et c'est plus que révélateur sur la nature de l'architecture qui propulse le réseau social viadeo !  

La société Viadeo n'a pas pour habitude de communiquer sur les caractéristiques de son infrastructure. A peine peut-on lire après d'âpres recherches que la [société utilise le CDN de Cotendo pour accélérer l'accès aux pages du site](http://www.marketwire.com/press-release/Viadeo-Chooses-Cotendo-Provide-CDN-Infrastructure-Global-Business-Social-Network-1028484.htm). Mais rien de plus précis.  

Les pages sont générées, en partie du moins, par du code Java qui s'exécute sur le [serveur web Apache/Tomcat 5.5.12](http://tomcat.apache.org/).

Après quelques rafraichissements de page et en vidant le cache, j'obtiens toujours le même résultat.

[Je m'en émeus sur twitter](http://twitter.com/sebbrochet/statuses/9254458981) mais bizarrement mon tweet n'est pas relayé :

![Tweet Video down]({{ site.url }}/img/2010/tweet_viadeo_down.png)

En fait, en testant avec un autre navigateur et via un proxy web public, [la page d'accueil de viadeo fonctionne très bien](http://twitter.com/sebbrochet/status/9255167375) :  

![Tweet Video accueil OK]({{ site.url }}/img/2010/tweet_viadeo_accueil_ok.png)

**Le problème est donc lié à mon compte utilisateur** et comme nous allons le voir, **plus précisément à ma session**.  

J'affiche les [cookies](http://fr.wikipedia.org/wiki/Cookie_%28informatique%29) liés au site viadeo.com (sous Firefox 3.5, menu outils|options|vie privée|supprimer des cookies spécifiques):

![Video cookies]({{ site.url }}/img/2010/viadeo_cookies.png)

Une ligne attire mon attention : **coyote-2-a0000c8**  

**Coyote**, c'est le nom du [connecteur HTTP de Tomcat](http://tomcat.apache.org/tomcat-4.1-doc/config/coyote.html).

J'ai l'impression que **ma session est liée d'une manière ou d'une autre à un serveur précis**.  

Quand la partie front-end analyse mes cookies, elle redirige ma requête vers ce serveur. Mais ce serveur qui fait tourner une machine virtuelle Java (JVM), à priori la version [JRockit d'Oracle](http://www.oracle.com/technology/products/jrockit/index.html) vue l'erreur assez caractéristique retournée ([(1)](http://javamonamour.blogspot.com/2009/09/javalangoutofmemoryerror.html), [(2)](http://mail.openjdk.java.net/pipermail/hotspot-gc-use/2008-May/000146.html), [(3)](http://www.coderanch.com/t/202946/Performance/java/Out-Memory-BEA-JRockit-R%5D)), n'a plus de mémoire disponible.  

Ma requête échoue donc en me retournant la pile d'exécution vue plus haut.  

Je supprime ce paramètre de mon cookie et recharge la page d'accueil, ouf tout est OK et [viadeo se rappelle encore de moi](http://twitter.com/sebbrochet/status/9255775848) :-)

![Tweet Video OK]({{ site.url }}/img/2010/tweet_viadeo_ok.png)

En recherchant sur twitter, il s'avère que nous étions [au moins deux dans le même cas](http://twitter.com/bzhgames/statuses/9263683612) mais à plusieurs heures d'intervalle !

![Tweet Video manque de mémoire]({{ site.url }}/img/2010/tweet_viadeo_manque_de_memoire.png)

# Qu'est-ce que cela nous apprend/rappelle en terme de Sécurité ?

* **Le fonctionnement d'un serveur web en mode debug est susceptible de donner des informations précieuses à un attaquant**. Les types de serveurs, les composants mis en œuvre et leurs versions sont autant d'indicateurs pour rechercher les failles connues ou analyser le code, surtout si comme c'est le cas ici, les produits sont [opensource](http://fr.wikipedia.org/wiki/Open_source).
* **La répartition de charge mis en place sur le site viadeo.com, attribue le temps d'une session une JVM dédiée par utilisateur**. Des données liées à l'utilisateur sont vraisemblablement stockées dans la mémoire de la JVM et pas seulement en base de données. L'utilisation d'un système de cache distribué comme [memcache](http://memcached.org/) permet logiquement d'éviter ce couplage fort.
* L'affectation à une JVM ou une autre est conditionnée par un paramètre dans le cookie. **A moins que le cookie ne soit signé, il semble possible de le modifier pour tenter la sélection d'une autre JVM**.
* **Le répartiteur de charge ne semble pas sonder régulièrement la santé des JVM de la ferme**. On peut imaginer que seule la santé de l'hôte est vérifiée ou bien que plusieurs JVM cohabitent sur un même serveur physique si des techniques de virtualisation sont mises en œuvre.
* **Il n'y a pas  de mécanisme de reprise et de sélection d'une autre JVM si la JVM référencée n'est plus disponible**. Nous avons donc un [SPOF](http://fr.wikipedia.org/wiki/Point_individuel_de_d%C3%A9faillance), qui n'affecte cependant pas tous les utilisateurs du service.
* **Est-ce que cet incident a été détecté par les équipes de [supervision]({{ site.url }}/2009/11/27/Le%20champion%20de%20la%20supervision%20open-source/) de viadeo** ? Le remède contre ce type d'incident est le redémarrage pur et simple de la JVM incriminée. Un [système de watchdog logiciel](http://fr.wikipedia.org/wiki/Chien_de_garde_%28informatique%29) est même en mesure de le faire automatiquement.

# Questions

Avez-vous plus d'infos sur ce type d'erreur ?  
L'avez-vous aussi rencontrée sur vos infrastructures ?  
Les technologies mises en oeuvre vous ont-elles permis de rectifier le tir facilement ?  

