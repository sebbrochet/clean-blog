---
layout: post
title: "Une histoire (vécue) de botnet et de Spam où les bons gagnent à la fin"
tags: BOTNET FIREWALL SYSLOG
date:       2009-09-06 12:00:00
author:     "sebbrochet"
comments: true
---

Tout a commencé par un utilisateur qui se plaignait qu'il ne recevait pas les mails de notification de ses traitements automatiques. Plus précisément, il rapportait que les mails en question étaient considérés comme Spam et renvoyés à l'émetteur. L'analyse de ses "bounces" montre alors très clairement la raison du retour: l'adresse IP d'émission du mail fait partie de la liste CBL de Spamhaus...

Spamhaus est une organisation à but non lucratif qui gère différentes listes d'adresses IP qui sont considérées comme la source d'envois massif de mails non sollicités.

La liste CBL (Composite Block List) liste en particulier les adresses IP qui ont été source d'envoi massif de mails par l'intermédiaire de robots. Cette liste est utilisée par de nombreux serveurs mails pour valider la reception d'un mail.

Pour dépanner rapidement l'utilisateur, l'adresse du serveur SMTP est modifiée. Il se trouvait que l'adresse utilisée était aussi l'adresse sortante pour tous les autres flux (web, ftp, ssh, ...). Ce qui est à la fois une bonne chose car c'est ce qui a permis d'identifier l'infection et une mauvaise chose car le trafic utilisateur peut aussi, volontairement ou non, être la cause d'un blacklistage de la part de certains sites spécialisés.

Une fois le choc passé, la lecture du détail du diagnostic pour l'adresse IP en question (http://cbl.abuseat.org/lookup.cgi?ip=x.x.x.x) explique la marche à suivre.



Elle précise par exemple la nature du code malveillant qui officie derrière cette adresse IP et indique comment la détection a été réalisée. Ainsi 2 adresses IP publiques sont listées avec le dernier accès vers celles-ci et l'heure précise où il a été réalisé, en provenance de l'IP qui est maintenant listée dans la CBL.

Comme dans de nombreuses entreprises et de plus en plus chez les particuliers, les IP internes sont nattés sur une IP publique. Il n'est ainsi pas possible de remonter directement à la machine source qui utilise l'adresse IP sortante. Il faut identifier le port utilisé au moment de la connexion vers les adresses IP fournies par Spamhaus et faire ensuite le lien avec l'utilisation de ce port avec une adresse IP privée.

La solution à mettre en place pour y parvenir est relativement simple si différents éléments sont déjà présents. A savoir un pare-feu qui peut être paramétré pour générer des messages syslog détaillés avec les caractéristiques de toutes les connexions et un serveur syslog pour enregistrer toutes ces données. Le serveur syslog évite de passer son temps devant l'écran à attendre que la machine infectée se connecte !

Certains pare-feu (comme les ASA) ont une fonction de type Packet Capture qui, comme son nom l'indique, permet de capturer tous les packets à destination d'une adresse IP donnée. Dans notre cas, ça ne suffit pas car il nous faut également capturer la connexion interne correspondante et sans connaître à l'avance le port qui sera utilisé, ce n'est pas possible.

Dans le cas qui est rapporté ici, la page Spamhaus montre que la machine infectée fait des connexions pratiquement toutes les 4H. A partir du serveur syslog et en faisant une recherche sur les addresses IP communiquées par Spamhaus, un résultat apparaît.



Le jour et l'heure concordent avec l'information donnée par Spamhaus, nous tenons notre machine indélicate !

Ensuite, une nouvelle recherche avec l'adresse IP blacklistée et le port utilisé (39519) par cette connexion remonte le nom de la machine infectée avec son adresse IP.



Cette machine est configurée en DHCP et utilise donc une adresse IP dynamique. De manière à l'isoler du réseau, à distance comme dans mon cas, 2 actions sont nécessaires:

Réserver l'adresse IP actuelle de la machine et l'associer à l'adresse MAC de cette machine. Ce qui nous assure qu'une autre machine ne récupérera pas l'IP par la suite
Puis agir sur le pare-feu pour bloquer tout le trafic sortant à partir de l'adresse IP de la machine. Sur un matériel CISCO, la commande [shun IP] permet de le faire directement. Les connexions entrantes à destination de l'adresse IP restent toutefois possibles, ce qui permet d'examiner la machine, même à distance.
Il reste ensuite à essayer de désinfecter la machine ou plus probablement de la réinstaller à partir d'une image système saine.

Pour aller plus loin et automatiser la détection des indésirables sur votre réseau, un module additionnel pour ASA, Botnet Traffic Filter prend en charge cette partie.
Ce qui fera peut-être l'objet d'un nouveau post !
