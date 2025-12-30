---
title: Des stats respectueuses des lecteurs
date: 2020-01-12T16:29:00.000Z
layout: post
tags:
- Actualité
- ViePrivée
categories:
- Société
- Personnel

---
Alors que j'avais complètement abandonné l'idée de mettre des outils de stats sur mon blog, principalement pour éviter de participer au tracking mondial par une poignée d'acteurs (Google, Facebook, Snapchat...) j'ai vu passer plusieurs solutions de statistiques qui ne fliquent pas les utilisateurs. Alors j'ai décidé d'essayer.

Historiquement, il y avait un gros concurrent de Google Analytics et c'était Piwik. Piwik offrait les mêmes fonctions que Google Analytics mais vous pouviez l'héberger sur votre propre serveur. Autant dire que c'était plutôt sexy. Mais voila, les années passant et avec un grand retour de la centralisation d'internet, héberger sa propre solution de stat c'est avéré être chiant. Piwik est devenu [Matomo](https://matomo.org/why-matomo/), qui a ensuite changé de modèle économique pour proposer une solution en SaaS (donc hébergée par eux) avec des fonctions très restreintes et un modèle payant obligatoire pour avoir toutes les fonctions d'un Google Analytics ☹️

Autant dire que ça craint du boudin.

J'avais donc laissé tombé, en essayant quand même le pixel de tracking Snapchat sur [bears.lu](https://bears.lu) qui ne donne que les visites et visites uniques. Mais on sait pas trop ce qui est fait des données ensuite 😞.

Et récemment j'ai découvert [Simple Analytics](https://referral.simpleanalytics.com/clawfire). C'est un service qui ne calcule aucune empreinte unique pour les internautes, qui ne sauvegarde aucune données personnelles ou identifiantes. Il ne me donne accès qu'à des choses très basiques mais totalement suffisante comme : 

* le nombre de visiteurs et de visiteurs uniques par pages
* la tendance concernant les pays des visiteurs
* la tendance concernant la résolution d'écran des visiteurs et leur navigateur (ce qui permet de faire des choix de design et d'accessibilité)
* l'origine du traffic (le nom de domaine comme google.com ou twitter.com mais pas la requête tapée dans Google pour venir)

Et c'est tout. Pas de tunnel, pas de conversion, pas d'infos sur quels mots clés vous avez tapés ou quels autres sites vous avez visité. Rien de tout cela.

Cerise sur le gateau, il respecte le DNT (Do Not Track) de votre navigateur. Donc si vous indiquez ne pas vouloir être suivi (ce qu'il ne fait pas), vous n'apparaitrez même pas dans les stats. 

La transparence ne s'arrête pas là puisque vous pouvez rendre publique vos stats, par site, et embarquer dans vos pages vos graphs de vos stats.

Dernier petit truc, il permet de faire un truc que plein de régies font pour contourner vos ad-blockers: configurer un sous domaine pour servir le pixel de tracking. C'est assez pratique pour contrer les ad-blocker trop agressif qui catégorisent (à juste titre) cela comme du tracking et bloque en masse alors que le service est respectueux de la vie privée de l'internaute.

P.S: Si vous voulez essayez, [en utilisant ce lien](https://referral.simpleanalytics.com/clawfire) vous pourrez avoir 1 mois gratuit contre seulement 7 jours. Et si vous décidez de continuer au-dela de votre test, c'est moi qui recevrais un mois gratuit. 

