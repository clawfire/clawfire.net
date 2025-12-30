---
title: Faire revivre un iMac 27" de 2010
description: Découvrez comment redonner vie à votre ancien iMac 27" de 2010 avec quelques nettoyages et mises à jour simples. Cet article couvre le processus de nettoyage de l'extérieur et de l'intérieur de l'iMac, l'installation des mises à jour de sécurité disponibles, et même la mise à niveau du système d'exploitation au-delà du support officiel d'Apple en utilisant OpenCore Legacy Patcher. Apprenez comment donner une nouvelle vie à votre ancien iMac et profiter de fonctionnalités modernes. Parfait pour ceux qui cherchent à raviver de vieux Mac ou à économiser de l'argent sur un nouvel ordinateur.
date: 2025-01-12T12:10:06.003Z
featured_image: /images/article_images/2025/01/iMac 27" de face.jpg
layout: post
subtitle: ""
fmContentType: Post
keywords:
  - Mises à jour de sécurité
  - OpenCore Legacy Patcher
  - iMac 27 pouces 2010
slug: faire-revivre-imac-27-pouce-2010
tags:
- MacOS
- Tech
categories:
- Culture
- Tech

---
TL;DR : Le Mac fonctionne toujours aussi bien dès sa sortie de la boîte. Branchez-le, profitez-en. Ahah.

Récemment, j'ai un ami dont le laptop est décédé et qui n'a pas les finances lui permettant de s'en acheter un nouveau. Même si des options existent autour de 100 € avec le nouveau Raspberry Pi 5 en version intégrée dans un clavier + trackpad et avec l'écran officiel, cela reste pas mal de contraintes et de concessions pour une personne lambda d'utiliser ce genre de matériel.

Du coup, comme j'avais un vieil iMac 27 pouces de mi-2010 à la cave, je me suis dit que je pouvais toujours le dépoussiérer et voir ce que je pouvais en faire. Je vous emmène avec moi dans l'aventure, peut-être que vous apprendrez quelques trucs au passage 😉.

## Le nettoyage

Malgré que j'aie entreposé le Mac dans sa boîte d'origine, avec le papier protecteur sur l'écran et un sachet d'anti-humidité, passer presque 7 ans dans un carton à la cave laisse quelques traces. Donc un petit nettoyage s'impose :

1. Nettoyez la poussière avec un chiffon, une microfibre, un plumeau. Peu importe. C'est juste pour enlever le plus gros afin d'éviter, comme moi, d'avoir des couches de poussière et de salir encore plus l'aluminium avec une lingette désinfectante humide.
2. Nettoyez l'aluminium, le clavier, la souris avec [de l'alcool isopropylique](https://amzn.to/3We8Gpo). J'utilise celui à 99,9 % que j'ai pour l'impression 3D. L'avantage de l'alcool, c'est qu'il s'évapore et ne provoque pas de corrosion des connecteurs, des composants électroniques, etc.
3. Nettoyez la vitre du Mac avec un produit pour vitre / miroir. Je sais qu'on déconseille de nettoyer un écran avec ce genre de produit, mais l'iMac de cette époque a une vitre entre l'écran et l'utilisateur. Donc allez faire reluire tout cela.

### Nettoyer l'intérieur de la vitre 👷

![Photo de l'écran en gros planc, avec des traces de poussières sous le verre protecteur. Des flèches rouges ont été ajoutée numériquement pour pointer vers les tout petits amats de poussières.](/images/article_images/2025/01/Traces%20de%20poussières%20sous%20le%20verre.jpeg)

Comme il y a une vitre entre l'écran et l'utilisateur, il y a aussi de l'espace entre l'écran et la vitre. Et cet espace peut voir du dépôt de micro-poussière s'accumuler (après tout, l'iMac de cette époque avait un puissant flux de ventilation pour pousser la chaleur de l'écran en dehors. Genre à vous chauffer la pièce gratuitement en hiver). Il est donc conseillé, de temps en temps, de nettoyer l'intérieur de la vitre. J'avoue ne l'avoir jamais fait, mais après 7 ans à la cave, j'avais des petits dépôts visibles sur la vitre.

{% youtube "https://youtu.be/ONCdGHe0Uxs" %}

[Une rapide recherche sur Youtube](https://youtu.be/ONCdGHe0Uxs?si=roP_iz21XwVzlY54) m'a montré que c'était super facile à ouvrir puisque c'est maintenu par des aimants. Tout simplement. Donc clairement conçu pour être facilement opéré pour l'entretien. Le temps béni des Mac super modulables aussi... Mais passons. Donc, je n'avais pas de ventouse comme dans la vidéo, mais j'ai glissé des cartes en plastique entre la vitre et le châssis en métal. Une de chaque côté dans les coins supérieurs, puis j'ai fait levier et hop ! La vitre s'est dégagée.

Elle est équipée de tout un tas d'encoches et de poinçons qui vous aideront à la repositionner super facilement après, pas d'inquiétude.

On nettoie la vitre, face intérieure, avec du produit à vitre, et l'écran **avec un chiffon doux humide uniquement. Attention !**

## Les mises à jour

De manière assez surprenante, bien que le système ne soit plus supporté (il était sous Snow Leopard), les mises à jour de sécurité de l'époque sont toujours disponibles sur les serveurs d'Apple. Même si vous allez devoir vous y reprendre à plusieurs reprises car il n'y a pas (plus ?) de mise à jour combinée disponible, c'est assez simple. On démarre. On se connecte à son compte utilisateur. On lance la recherche de mise à jour. On attend. On redémarre. Dans mon cas, j'ai dû répéter cela 4-5 fois à coup de 2 à 3 mises à jour à la fois.

### Mettre à jour l'OS au-delà de sa limite de prise en charge par Apple

Un projet que mon ami [Biou](https://mas.to/@biou) m'a partagé, nommé [OpenCore Legacy Patcher](https://dortania.github.io/OpenCore-Legacy-Patcher/), permet d'installer des OS non supportés sur d'anciens Mac. Une équipe de bénévoles travaille sur l'injection de dépendances à la volée pour supporter du matériel. Tout cela fonctionne avec plus ou moins de succès, mais d'après leur matrice de compatibilité, je pouvais espérer faire tourner macOS Ventura sans aucun souci. J'aurais pu pousser un peu plus loin mais, encore une fois, comme c'est pour un ami qui n'est pas trop versé dans la tech expérimentale, on va s'en tenir à une valeur sûre.

Bon, je vous passe le moment où je télécharge le mauvais binaire et où je me prends la tête. **RTFM** comme on dit 😅. En gros il faut télécharger le `OpenCore-Patcher.pkg` et pas un autre fichier. Vous l'installez sur un mac, n'importe lequel, et vous le lancez. Ensuite, le menu est un peu déroutant car... en gros les items ne sont pas dans l'ordre:

![](/images/article_images/2025/01/OpenCore%20Legacy%20Patcher%20Menu.jpg)

#### D'abord, vous devez [créer l'installateur](https://dortania.github.io/OpenCore-Legacy-Patcher/INSTALLER.html#downloading-the-installer)

Cette partie se fait en deux temps :

1. Télécharger un installateur depuis les serveurs d'Apple.
2. Créer une clé USB / une carte SD bootable avec l'installateur.

#### Ensuite, vous [construisez un EFI custom bootable](https://dortania.github.io/OpenCore-Legacy-Patcher/BUILD.html) :

1. D'abord, vous allez choisir le modèle cible dans les `Settings`. Dans mon cas, l'iMac 27" mi-2010 est le 11,3. Vous pouvez trouver la référence dans Menu  > À propos de ce Mac > (En savoir plus >) Rapport système. Là, vous trouverez l'identifiant du modèle.
2. Ensuite, vous allez cliquer sur `Build and Install OpenCore`. Une fois compilé, l'outil vous demandera de sélectionner la clé / la carte SD, puis la partition dessus.

#### [On boote ensuite sur la clé / carte SD sur OpenCore](https://dortania.github.io/OpenCore-Legacy-Patcher/BOOT.html)

En maintenant la touche `Option` enfoncée. L'opération est assez rapide, puis un autre menu s'affiche. On sélectionne `install macOS NOM_VERSION` (dans mon cas Ventura). Le processus d'installation est assez classique. Long mais classique. Comptez 50 min et 2-3 redémarrages.

## Étapes post-installation

Comme on n'est pas _vraiment_ sur une version supportée du hardware, il y a [quelques étapes encore à faire pour que ce soit pérenne](https://dortania.github.io/OpenCore-Legacy-Patcher/POST-INSTALL.html). Avant toute chose, vous allez devoir installer OpenCore Legacy Patcher sur le Mac fraîchement mis à jour. Comme application résidente. Cela va permettre de continuellement monitorer le Mac et, en cas de mise à jour, pouvoir ré-appliquer les patchs. Car oui, les mises à jour d'Apple effacent les patchs <3. Mais pas de panique, OpenCore Legacy Patcher a un démon qui tourne pour surveiller cela.

### Installer l'EFI modifié sur le disque pour ne pas avoir besoin de la clé USB / carte SD

C'est d'ailleurs une opération que OpenCore Legacy Patcher devrait vous proposer au lancement. C'est la première chose que j'ai faite pour me débarrasser de la carte SD insérée dans le Mac. En bonus, vous pouvez même régler pour qu'il passe automatiquement le choix du boot lors de la séquence de démarrage, afin d'avoir une expérience la plus transparente possible. Pour cela, décochez `Show OpenCore Boot Picker` comme indiqué sur la capture d'écran ci-après.

![](/images/article_images/2025/01/Show%20OpenCore%20Boot%20Picker.png)

### Patcher pour le support du hardware

Attendez, on ne l'avait pas fait lors de l'installation de l'OS ? Eh bien, si, mais uniquement les éléments essentiels comme le driver vidéo de base et la carte ethernet / wifi. Pour le support un peu plus avancé permettant de faire des jolis effets de transparence qui vont faire fondre notre tout petit GPU, il faut installer des patchs qui sont téléchargés d'internet (d'où le besoin du support wifi / ethernet).

Rendez-vous dans la section 3 "Post-Install Root Patch". Là, l'outil va scanner votre système, se connecter aux dépôts de code distant, et faire ses courses. Il vous proposera d'installer ce qui est manquant, ou vous indiquera que tout est en ordre. Dans mon cas, un driver graphique et une prise en charge de processeurs plus récents, il me semble. Comme tout est construit sur votre machine, cela peut être **LONG**. Cela a dû me prendre 45 minutes avec les pauvres 4 Go de RAM d'origine, avec le disque qui swap non-stop.

## Mettre à jour la RAM

Bon, on ne va pas se mentir, une des raisons pour lesquelles ça m'a pris un temps fou, c'est aussi parce que l'OS n'arrêtait pas de swapper sur le disque (qui n'est pas un SSD qui plus est) car mes pauvres 4 petits Go de RAM arrivaient à peine à faire tourner l'OS. Mais, ce qu'il faut savoir, c'est que le design de l'époque des iMac était super modulaire. Comme on a pu le voir précédemment dans cet article, c'est tout à fait possible de démonter et d'entretenir le Mac et c'est fait pour. Mettre à jour la RAM fait partie de cela.

L'iMac 27 pouces de 2010 dispose de 4 emplacements de RAM, pouvant accueillir au maximum des barrettes de 4 Go de RAM DDR[REDACTED]Mhz. J'ai acheté [ce modèle sur Amazon](https://amzn.to/3BVVE9n) pour 14€ les 2 x 4 Go. Livré en 24h chrono qui plus est. Le prix m'a fait halluciner car je me rappelle que c'était hors de prix quand j'ai eu le Mac 😅.

<div class="gallery" data-columns="2">
  <img src="/images/article_images/2025/01/Capot%20de%20compartiment%20de%20RAM%20plein%20de%20poussiere.jpg" alt="Capot de compartiment de RAM plein de poussière, posé sur une tablette en bois. Un set de tournevis de précision est visible à côté."/>
  <img src="/images/article_images/2025/01/Logement%20Ram%20iMac%20poussierreux.jpg" alt="Logement RAM iMac poussiéreux, vue du dessous de l'écran / unité."/>
</div>

Une fois reçu, il y a une petite trappe en dessous de l'écran. Vous débranchez l'alimentation, un petit coup de tournevis Phillips sur les 3 vis et vous accédez à la trappe des RAM. Vous avez deux languettes sur lesquelles vous pouvez tirer (fort, n'ayez pas peur de les casser) pour éjecter la RAM présente dans chaque compartiment (gauche et droit, deux barrettes par compartiment max). Il vous suffit de glisser les nouvelles barrettes dans les logements en appuyant bien fort, et de tout refermer, puis redémarrer votre iMac pour constater le changement.

P.S : pensez à donner un petit coup d'aspirateur 😉.

---

Avec pas mal d'huile de coude et l'aide de projets open-source, j'ai réussi à transformer cet ancien iMac qui prenait la poussière dans ma cave en une machine pleinement fonctionnelle. Non seulement cela m'a permis de renouer avec le plaisir de bidouiller des appareils, mais j'ai surtout pu aider un ami en difficulté en lui offrant une solution pratique. C'est gratifiant de voir qu'avec un peu de patience et de bricolage, on peut donner une seconde vie à une vieille machine et, par la même occasion, donner un coup de main à quelqu'un qui en a besoin. C'était une aventure enrichissante que je conseille à chacun, pour peu que vous ayez un weekend à y consacrer 😅
