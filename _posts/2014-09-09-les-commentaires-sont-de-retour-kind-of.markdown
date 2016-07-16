---
layout: post
title: Les commentaires sont de retour ( kind of )
date: '2014-09-09 20:19:54'
tags:
- blog
- ghost-tag
- wordpress
- commentaires
- migration
- geek
- code
---

Les commentaires sont de retour \o/ via [Livefyre](http://livefyre.com). Mauvaise nouvelle : les `ids` des posts Wordpress & Ghost ne sont pas les même. J'ai donc essayé d'exporter tout mes articles, modifier les `ids` à la main ( ça m'as pris une bonne heure ) et me reportant aux `ids` utilisés par Livefyre ( en fait ceux que Wordpress lui à donné ) et j'ai ré-injecter le tout dans Ghost.

Mais ça ne marche pas. Lors de l'import Ghost semble renuméroter les posts; ce qui Wordpress ne fait pas et que j'ai toujours considérer comme une connerie. Imaginez pour 91 posts Wordpress a été jusqu'a l'id 789 ! :O Clairement pas optimisé ... Chaque révision d'article est enregistré comme un article à part, d'où ses chiffres astronimiques & la place prise pour rien dans la DB ... bref.

So what's next ?

Je vais modifier [mon thème](https://github.com/clawfire/tepid) pour renuméroter les ids lors de l'appel au JS de Lyvefyre, en essayant de limiter cela aux posts dont la date est antérieure à mon passage sur Ghost. Pourquoi ? Pour lorsque je suis sur le post, disons 43, je charge le post avec l'`id` 275 qui est l'`id` assigné par Wordpress.

Mais cela va poser un soucis dans le futur, la collision avec les articles futurs ... Si certains sont dans les rangs des 600 , ce qui le laisse voir venir, d'autre sont bien plus proches et cela va finir par me poser problème.

Je vais tester quelques trucs, peut être un `id` alphanumérique et non uniquement numérique comme pour Wordpress ... a voir si Livefyre accepte cela.