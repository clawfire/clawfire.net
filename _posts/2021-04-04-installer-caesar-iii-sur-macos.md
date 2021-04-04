---
date: 2021-04-04 17:19:11 +0200
layout: post
title: Installer Caesar III sur macOS
featured_image: "/images/article_images/2021/04/31294caesar3_12.PNG"
tags:
- macOS
- jeu vidéo

---
Pour ceux qui ne le savent pas, Caesar III est disponible en abandonware (ou sur GoG pour ± 5€) mais, même si une version pour ordinateur de la marque à la pomme existait à l’origine, il n’est plus possible de la lancer de nos jours.

En effet, le jeu devais tourner sous carbon, qui nécessitait déjà Rosetta (un logiciel qui permettant de lancer des programmes avec d’anciennes interfaces graphiques sous osX) à l’époque où j’ai commencé à utiliser des Mac. Alors, aujourd’hui, après bien quoi … 2 changements majeurs du moteur de rendu graphique de l’OS, il n’est plus possible de le lancer. 

Pourtant, une version PC existe bien, et on va voir ici comment la lancer facilement sur un Mac, car j’ai eu envie d’y jouer ce weekend.

## Télécharger Caesar III

Deux options: 

1. [Abandonware France](https://www.abandonware-france.org/ltf_abandon/ltf_jeu.php?id=1612) gratuitement

2. [Gog](https://www.gog.com/game/caesar_3) pour 5€ (en promo à 3,29€ à l’heure où j’écris ce billet)

## Télécharger CrossOver

Après avoir longtemps utilisé [boxer](http://boxerapp.com) (gratuit) pendant longtemps (qui en plus fournis plein de trucs trop cool comme une émulation des jeux réalistes avec des synthétiseurs Roland ❤) , la dernière version de macOS ne permet plus de l’utiliser 😭 (64 bits only oblige).

Je me suis donc rabattue vers mon couteau suisse des logiciels Windows, à savoir [CrossOver](https://www.codeweavers.com/?ad=854) (à partir de 38€, mais je recommande la version à 59€ qui vous assure 1 an de mise à jour inclus) pour l’installation. Après, il y a 14 jours de test gratuit si vous voulez juste tenter l’expérience.

::Lien affilié pour CrossOver::

Outre le fait qu’il tourne parfaitement sur macOS en 64 bits, CrossOver arrive a faire tourner des applications 32 bits sans aucun soucis. C’est d’ailleurs encore une exclusivité qui ne devrait pas pouvoir être backporté dans Wine, car cela utilise des licenses propriétaires Microsoft.

Pour faire simple pour les néophytes, dans CrossOver on utiliser un logiciel d’émulation de Windows qui s’appelle Wine. Donc on parle de faire des « bouteilles » pour dire qu’on fait un nouvel environnement d’émulation windows.

CrossOver a une sélection de bouteille toutes faites assez ouf si vous voulez installer des logiciels connus. Il va même jusqu’a les télécharger pour vous si vous n’avez pas l’installer. Mais attention, dans notre cas, cela se révèle contre productif car cela ne marche tout simplement pas.

## Installer .net Framework 4.0

On va commencer par créer une « bouteille »  personnalisée, car celle proposée pour Caesar III ne fonctionne pas bien (en tout cas pas sur macOS Big Sur). 

On commence par cliquer sur « installer une application windows » et chercher .net framework 4.0. On choisis une nouvelle bouteille Windows 7 (attention, pas 64 bits) et on peut nommer la bouteille « Caesar III » pour s’y retrouver plus tard.

L’installation commence. CrossOver va télécharger pour vous .net et les service pack pour que tout soit à jour. Suivez les assistants. Faites toujours « redémarrer ultérieurement », CrossOver simulera un redémarrage pour vous à la fin.

## Installer Caesar III

On va recliquer sur « installer une application windows »et cliquer sur « voir toutes les applications » en bas à gauche de la fenêtre. On sélectionne « Application inconnue » puisqu’on ne veux pas prendre les pré-réglages qui ne fonctionnent pas. On fait suivant et on sélectionne le programme d’installer qu’on a téléchargé. 

Ensuite on passe à l’écran Bouteille et on va sélectionner notre bouteille Caesar III qui contient deja .net 4.0. Ainsi l’installation va se passer tout bien et vous pourrez retrouver Caesar III installé et disponible dans le lanceur de CrossOver 😃 

Bon jeu! 

## Bonus

Une Astuce « cheat » pour le jeu !

Pendant une partie de Caesar 3, rendez-vous près d’un puit si vous possédez moins de 5000 denaris. Appuyez alors sur le bouton droit de la souris puis simultanément sur les touches K et Alt.

Faites ensuite l’une de ces combinaisons : 

- Alt + C : gagner de l’argent

- Alt + V : victoire instantanée