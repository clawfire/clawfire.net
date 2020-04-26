---
title: Improving out.lu
date: 2020-04-26T20:09:04.865Z
featured_image: /images/article_images/23622461_797773153764309_5261759074080373775_n.png
tags:
  - news
  - LGBT+
layout: post
---
Certain·e·s d'entre vous savent peut être que je bosse sur le projet out.lu depuis que j'ai été élu Mr. Bear Luxembourg en ... 2016 😱 Shit c'est loin tout ça!

Donc [out.lu](https://out.lu/) pour le moment c'était:

* un [Airtable](https://airtable.com/invite/r/zsk98e38) qui permet d'enregistrer les évènement dans une table (un peu comme une feuille excel sous stéroïdes). Ça me fournit aussi [un joli formulaire](https://airtable.com/shrzrP1ELrh9CeL9d) que je peux mettre sur le site pour que les gens puissent ajouter leurs soirées. Avec un compte gratuit j'ai assez d'hébergement pour les flyers donc ça ne me coûte rien et c'est parfait. Enfin ça fournit un widget de vue calendar mensuel que je peux mettre sur la page web. Pour finir, le calendrier viens avec un flux `.ics` 
* une [page web](http://out.lu) toute conne, faites à la main avec [SemanticUI](https://semantic-ui.com/) et une video en background pour faire cool.
* De l'automation qui remercie les gens qui ajoutent des avènements par email et postent sur la page facebook du projet les nouveaux évènement ainsi que les nouveaux organisateurs.

Le soucis c'est que ça a été ainsi pendant un peu trop longtemps.

## Ajout d'un service de ticketing

Après avoir fait tourné pendant 2 ans une plateforme de ticketing pour les ours de Luxembourg, j'ai décidé de migrer sur tickets.out.lu la plateforme et de la rendre accessible à tout ceux qui voudraient l'utiliser. J'utilise un soft open source qui se nomme [Attendize](https://www.attendize.com/). Plutôt complet mais qui nécessite beaucoup de boulot côté intégration et mise en place. La documentation est vraiment pauvre et pas mal de truc sont à faire à la main. Ca mériterais un article complet ici 😃

## Création d'une app mobile

Avoir un site internet c'est cool. Mais comme le widget marchait moyen sur mobile. Et ses derniers mois je me suis lancé dans le développement de petites apps mobiles Android et iOS avec des solutions no-code. [Ca marche plutôt pas mal](http://outluxembourg.glideapp.io/). Bon la pandémie actuelle fait qu'il manque un peu de contenu mais en gros on a:

* Par défault, la liste par vue calendaire des évènements à venir.
* Une vue par Flyers
* Un onglet avec une vue sur les évènements internationaux
* Un hamburger menu avec :

  * Une vue carte des soirées autour de soi (je trouve cela moyen pratique perso)
  * La liste des organisateurs avec une petite fiche descriptive
  * La liste des endroits qui ont des soirées gays, avec aussi une petite fiche descriptive. J'ai l'impression que c'est con mais ca me semble une bonne idée de savoir quels sont les endroits LGBT+ friendly.
  * Une liste des versions de l'app et des modifications. A terme ca devrait aller sur out.lu directement 🤓

Techniquement c'est une PWA donc ça s'installe aussi sur un ordinateur avec un navigateur qui supporte cela comme [Google Chrome](http://chrome.google.com/).

## Automatisation de l'import d'évènements

Tout d'abord, j'ai ajouté dans Airtable des organisateurs et d'un formulaire pour s'enregistrer comme organisateur. Même si cela n'ouvre à rien pour le moment. A part que j'ai toutes les infos sur l'organisateur. 

J'ai utilisé [Zapier](https://zapier.com/) (comme pour les automatisation dont j'ai parlé plus haut) pour copier automatiquement les données de Airtable dans un Google Sheet, qui sert de base à mon app mobile.

Aujourd'hui, j'ai utilisé aussi Zapier encore une fois, mais cette fois ci en utilisant la possibilité de déployer une lambda function chez eux pour aller récupérer automatiquement les évènements de toutes les pages Facebook d'organisateur qui utilisent ma plateforme pour le moment et les injecter dans le Airtable. D'où les autres automations prennent le relais pour faire leur magie.

Du coup j'ai monté un petit [Tinyletter](https://tinyletter.com/Out) (une version basique et gratuite de mailchimp) pour tenir informé les principaux interessés, en attendant de refaire le site.