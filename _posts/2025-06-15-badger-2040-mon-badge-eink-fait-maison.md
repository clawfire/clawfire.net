---
title: "Badger 2040: Mon Badge eInk Fait Maison"
description: Découvrez comment j'ai transformé le Badger 2040 en un badge e-ink personnalisé et fonctionnel, alliant créativité et technologie DIY.
date: 2025-06-15T20:27:58.417Z
featured_image: /images/article_images/2025/06/PXL_20250621_114332317.MP~2.jpg
layout: post
subtitle: ""
fmContentType: Post
keywords: []
lastmod: 2025-06-21T12:42:21.528Z
tags:
- Projets
- RaspberryPi
- TDAH
- Tech
- Électronique
categories:
- Santé
- Tech

---
Il y a quelque temps, j’ai acheté un badge électronique appelé [Badger 2040](https://shop.pimoroni.com/products/badger-2040?variant=39752959852627), fabriqué par Pimoroni. C’est un petit écran noir et blanc à encre électronique (e-ink) alimenté par un Raspberry Pi Pico. Il consomme très peu d’énergie, ce qui en fait un excellent support pour des projets simples et autonomes.

Au départ, je l’utilisais comme badge pour des conférences ou des salons — il affichait mon prénom et un QR code. Mais j’avais envie d’aller plus loin : le rendre plus fin, plus joli, et plus pratique à utiliser.

C’est un hackathon récent au **GovTechLab** qui m’a redonné l’envie de m’y remettre, et de terminer ce petit projet une bonne fois pour toutes.

## C’est quoi le Badger 2040 ?

C’est un petit écran e-paper de 2,9 pouces (comme ceux qu’on retrouve sur les liseuses) avec six boutons programmables et un port USB-C pour le programmer. Il permet d’afficher du texte ou des images, et repose sur un Raspberry Pi Pico.

À l’origine, je l’alimentais avec **deux piles AAA**. Ça fonctionnait, mais c’était un peu encombrant. J’ai donc eu l’idée de passer à deux piles bouton CR2032, beaucoup plus plates. Mon objectif : faire tenir le tout dans **une boîte imprimée en 3D** pour créer un badge beaucoup plus fin.

## Une boîte plus fine… avec un souci au départ

J’ai trouvé [un super modèle de boîtier](https://github.com/oneearedrabbit/badger-system-ii/tree/master/case), conçu spécialement pour le Badger 2040 et deux CR2032. Mais il y avait un hic : [le connecteur de batterie que j’avais utilisé](https://www.adafruit.com/product/783) n’était pas dans le bon sens. Les languettes de contact en cuivre ne s’alignaient pas correctement, et je n’ai pas réussi à bidouiller quelque chose de fonctionnel.

Lors de ma première tentative, rien ne tenait bien en place, les piles ne faisaient pas contact — j’ai fini par mettre le projet de côté. Et pour être honnête : **c’est typiquement le genre de schéma que je vis avec mon TDAH**. Je me bute sur un détail, ça me frustre, je perds le fil et je laisse tomber.

C’est pour ça que **le fait d’y revenir et de le finir est un vrai accomplissement pour moi**. Terminer ce genre de projet ne relève pas juste de l’électronique — c’est un boost pour ma motivation, ma confiance, mon estime. Et franchement, ça fait un bien fou.

## Assemblage : patience, étain, et troisième main

J’ai réimprimé la boîte dans un filament spécial anniversaire : le [Prusament Radiant Sky](https://blog.prusa3d.com/fr/prusament-fete-son-6eme-anniversaire-une-nouvelle-edition-limitee-de-prusament-pla-est-la_103248/), brillant, coloré, et magnifique.

J’ai remplacé le connecteur de batterie, utilisé une **troisième main** pour maintenir les fils pendant la soudure, et j’ai bien nettoyé mon fer à souder pour un résultat propre.

J’ai aussi ajouté un petit **interrupteur** pour pouvoir couper l’alimentation manuellement — même si le firmware du badge est déjà optimisé pour consommer très peu d’énergie en veille.

Quelques tests, quelques ajustements… et tout rentre parfaitement dans la boîte imprimée. Quel bonheur !

<div class="gallery" data-columns="3">
  <img src="/images/article_images/2025/06/PXL_20250621_114416960~2.jpg" alt="Badger 2040 assemblé avec piles CR2032"/>
  <img src="/images/article_images/2025/06/PXL_20250621_114346290~2.jpg" alt="Boîtier imprimé en 3D pour le Badger 2040"/>
  <img src="/images/article_images/2025/06/PXL_20250621_114332317.MP~2.jpg" alt="Boîtier imprimé en 3D pour le Badger 2040"/>
</div>

## Améliorations logicielles : support natif des images JPEG

Avant, je devais convertir mes visuels en ligne de commande pour les rendre compatibles avec le badge. C’était loin d’être pratique.

J’ai donc mis à jour le code pour qu’il accepte désormais les **fichiers JPEG**. Il suffit maintenant de glisser une image sur le badge via USB, et elle s’affiche aussitôt.

Le code que j’utilise est basé sur le dépôt officiel disponible ici : [github.com/pimoroni/badger2040](https://github.com/pimoroni/badger2040), et vous trouverez une documentation très claire pour démarrer sur [learn.pimoroni.com](https://learn.pimoroni.com/article/getting-started-with-badger-2040#using-badger-os).

## Le résultat final

Le badge est maintenant complètement fonctionnel, et :

* Ultra plat grâce aux piles CR2032
* Stylé avec sa boîte imprimée sur mesure
* Facile à personnaliser grâce au support JPEG
* Autonome avec son interrupteur d’alimentation

Voici quelques photos du montage terminé, pour mieux visualiser le résultat final.

## Et la suite ?

Voici quelques idées que j’aimerais explorer :

1. Ajouter des QR codes dynamiques en fonction de l’événement (comme mes cartes HiHello, ou les QR codes fournis par les salons pro)
2. Réorganiser les menus pour que les options que j’utilise rarement apparaissent en fin de pagination
3. (Ne pas craquer pour le [Badger 2040W](https://shop.pimoroni.com/products/badger-2040-w?variant=40514062188627), la version Wi-Fi compatible Home Assistant 😍)

C’est un petit projet personnel que j’avais mis de côté trop longtemps — **et si toi aussi tu as un TDAH, tu sais à quel point finir quelque chose comme ça, c’est énorme**. Je suis fier, et ça m’a vraiment remonté le moral.

Si tu t’intéresses aux écrans e-paper ou aux projets DIY du genre, n’hésite pas à partager tes créations !

---

Et non, ce billet **n’est pas sponsorisé par Pimoroni** 😄 — juste un maker qui partage son plaisir ✌🏻 (bon, cela dit, si l’équipe marketing passe par là et veut m’envoyer un kit, je suis preneur 🔥)
