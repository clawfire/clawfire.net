---
layout: post
title: Un an plus tard ( part 2 )
date: '2014-08-26 08:03:17'
tags:
- blog
- hebergement
- ghost-tag
---

Nous avons donc vu précédemment comment ce blog est tombé à l'abandon, voyons voir comment il a résucité sur un presque coup de pied au cul.

## La solution retenue
Je vous au donc parlé de Ghost. Après avoir pendant un temps pensé à utiliser Jekyll (solution que je me garde de coté, sait on jamais) j'ai eu envie d'aller de l'avant, avec un truc pas parfait, mais qui fait le job. Vous vous souvenez ? _It just work_.

J'utilise donc Ghost, en mode service, via [Ghost.io](http://ghost.io), plateforme un peu à la wordpress.com qui fournis une solution clé en main moyennant quelques euros ( 4€/mois, le prix d'une instance que je devrais maintenir moi même chez les fournisseurs les moins chers ...).

J'ai quelques limitations en nombre de visites mais, soyons réalistes, avant qu'on les explose il y a de la marge.

J'ai donc pris une instance, installé le [plugin d'export pour wordpress](http://wordpress.org/plugins/ghost/) qui a bien évolué soit dit en passant et hop. J'obtien un fichier JSON. Je me connecte à l'admin, envoit le fichier et boom, le contenu est là. Tout ? Non. Il n'y a pas les photos. Bon et bien on réfléchira à plus tard à comment faire cela :) Les tags sont là, les URL aussi ( normalement ) mais bon je fais pas d'optimisation de référencement sur ce blog alors je m'en care un peu :p

Je parcoure quelques thèmes sur Github pour trouver celui ci, [Tepid](https://github.com/wcs/tepid) que je fork pour pouvoir le modifier ultérieurement. J'upload une photo pour le header, mets un titre et roulez jeunesse, mon blog est près.

Plus qu'a écrire un post et change les DNS pour faire pointer le nom de domaine ici. Merci [CloudFlare](http://cloudflare.com) au passage qui m'as permis d'avoir une propagation instantanné sur la plupart des DNS performants comme [Google Public DNS](https://developers.google.com/speed/public-dns/) ou [OpenDNS](https://www.opendns.com/) et surtout, de faire un `CNAME` sur un `@` ce qu'on apelle un `Root domain CNAME` ce que peux de fournisseurs permettent de faire bien que ce soit valide d'après la RFC.

## Les trucs à changer

Rien n'est parfait, c'est le concept. Donc il y a pleins de trucs qui ne me conviennent pas pour le moment

1. Les photos précédement utilisés ne sont plus là
2. Les tags sont à nettoyer et normaliser , beaucoup de majuscule / minuscules, ils sont maintenant sensible à la casse ce qui n'était pas le cas avec Wordpress.
3. ~~Virer les commentaires Google+. C'est une imperfection du thème actuel, bien que plein de monde trouve cela cool.~~ Remplacé par livefyre avec [plein de magie](https://github.com/clawfire/tepid/blob/master/post.hbs#L72-L114) pour supporter les anciens commentaires
4. Retravailler la photo du Header qui n'est pas dans les bonnes proportions
5. ~~Aller remplacer le markup propriétaire de Wordpress ( les [Shortcode](http://codex.wordpress.org/Shortcode_API) ) par du code HTML qui va bien pour afficher les bons embed tiers ( Soundcloud, youtube, flickr, etc ... )~~ Done

## Les commentaires

Juste pour faire un apparté sur les commentaires :

Pour le moment ils sont proposé via Google+ parceque le thème inclus cette fonctionalité par défaut. Cela ne relève pas de ce que je souhaite avoir ici. Ils vont donc bientôt être remplacé par mon ancienne solution de commentaire qui aura l'intéret de ne pas vous obliger à utiliser de service tiers pour commenter si vous ne le souhaitez pas et de faire revenir tout les commentaires déjà existant.

Je n'importerais pas les commentaires Google+ vers ce système. C'est impossible techniquement. Je ne peux même pas injecter à la main les commentaires dans mon système ... Vous êtes donc prévenu :)

##Et Sinon Ghost ?

J'aime beaucoup. J'adore écrire en markdown. C'est super pratique. Le WYSIWYG c'est vraiment une plaie énorme de l'internet.

L'interface est légère est rapide. Je n'ai pas à me plaindre. C'est en plus bien adapté à la tablette alors je peux écrire tranquillement dans le train, le bus, ... les transports en commun quoi.

La documentation est bien fournie, le support est vraiment sympa & même si j'ai perdu mon 1er post écris sur cette plateforme suite à la non prise en compte d'un cas d'utilisation ( écrire un post sur un temps assez long pour que la session soit fermée, sans avoir jamais sauvegarder, et que l'identification ne conserve pas le post que tu essaie de sauvegarder), c'est maintenant corrigé dans la version 0.5 de Ghost.

Pour ceux qui se demandent si je vais rester sur la plateforme SaS, je ne sais pas encore, je ne suis pas fan de cette idée, elle a des contraintes comme des avantages. Mais je préfèrerais rester maitre des données et du serveur donc ... je migrerais sans doute vers une solution hébergée par mon ami le canard :)