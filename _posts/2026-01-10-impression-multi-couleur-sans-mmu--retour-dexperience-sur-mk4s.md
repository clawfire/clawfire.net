---
title: "Impression multi-couleur sans MMU : retour d'expérience sur MK4S"
tags:
  - impression-3d
  - prusa
  - mk4s
  - multi-filament
  - retour-experience
description: Comment j'ai réussi à imprimer en multi-couleur sur une même couche avec ma Prusa MK4S, sans MMU — après quelques échecs instructifs.
date: 2026-01-10T14:58:23.498Z
featured_image: /images/article_images/2026/01/education-1.avif
layout: post
subtitle: ""
fmContentType: Post
lastmod: 2026-01-11T00:59:51.386Z
---

## Pourquoi faire du multi-couleur sans MMU ?

J'ai déjà pas mal d'expérience en impression multi-filament, surtout pour du multi-couleur basique : une couleur par couche, des changements manuels espacés, rien de très sorcier. Mais récemment, j'ai voulu pousser le concept un peu plus loin : **imprimer plusieurs couleurs dans la même couche, sur plusieurs couches consécutives**.

Le projet ? Une boîte de rangement pour un jeu de tarot destinée à un ami. Deux demi-boîtes, 10 couches avec deux couleurs chacune. Soit **20 changements de filament manuels** au total. C'est encore jouable sans devenir fou — mais ça demande une config solide et prévisible.

Je n'ai pas de MMU, et même si j'ai très envie d'en acheter un, je veux d'abord tester les limites de mon setup actuel. L'argent ne tombe pas du ciel, tout ça tout ça. Donc j'ai décidé de voir jusqu'où je pouvais aller avec un **extrudeur unique et des changements de filament bien placés**. Spoiler : ça marche, mais pas sans quelques détours.

---

## Échec n°1 : Activer le multi-matériau... et tout imprimer dans la même couleur

**Contexte :** Je configure PrusaSlicer en mode "Single Extruder Multi Material" (sans MMU), je mets deux extrudeurs virutels, je leur assigne une couleur chacun, je "peint" mes différentes pièces pour leur assigner l'extrudeur correspondant. Je vérifie que tout est bien configuré, je lance l'impression, et... rien. Aucun changement de filament. Tout sort dans la couleur déjà chargée.

**Pourquoi ?**
Parce que le mode "Multi Material" dans PrusaSlicer est conçu pour piloter un MMU qui change automatiquement les filaments via un code de "changement d'outil". Sans MMU branché, le code ne déclenche pas un changement de filament, aucun `M600`.

Résultat : une boîte monochrome. Pas terrible pour un projet censé être multicolore. 😅

**Leçon retenue :**
Il faut forcer manuellement les pauses de changement de filament avec le G-code `M600`.

---

## Échec n°2 : Ajouter du M600, mais garder la wipe tower... et tout boucher

**Contexte :** J'ajoute un `M600` dans le G-code de changement d'outil pour forcer le déchargement/chargement manuel. J'ai fait cela dans les réglages du slicer, comme ça il l'insère au bon endroit dans le G-code. Ça devrait fonctionner. Sauf que j'ai laissé la **wipe tower activée**, avec un flow de 200% pour accélérer la purge.

**Résultat ?**
Des gros pâtés de filament qui s'accumulent sur la tour de purge. Au bout de quelques couches, ça finit par boucher l'extrudeur au niveau de l'idler. L'impression s'arrête, et je me retrouve avec un bouchon coincé juste à l'entrée de la buse.

![](/images/article_images/2026/01/IMG_20260108_220811949.jpg)

### 🛠️ Comment déboucher un extrudeur obstrué à l'idler

Si tu te retrouves dans cette situation, voici comment j'ai procédé :

1. **Arrête l'impression** et refroidis la buse..
2. **Retire la vis de tension de l'idler** pour accéder au chemin du filament.
3. **Tire doucement le filament** vers l'extérieur. Dans mon cas c'était plutôt vers le cas / de travers. J'ai récupéré la partie encore droite et dure du filament coincé.
4. **Retire la buse complètement** et profite en pour la nettoyer (tant qu'on y est ...)
5. **Insère une clé Allen de 2,5mm** dans le trou de purge de la buse pour extraire le filament coincé en le poussant vers le haut. Attrape le paté par l'idler et tire-le vers toi.
6. **Remonte la buse** en prenant soin de ne pas coincer les connecteurs.
7. **Lance plusieurs tirage à froid** pour dégager tout les restes de filaments qui peuvent se trouver dans la buse. Si tu as une MK4S comme moi, tu peux utiliser le mode de tirage à froid automatique. Lance 3-4 cycles. Jusqu'à ce qu'il n'y ai plus de débris.

---

## Échec n°3 : Baisser le flow de la wipe tower... mais toujours trop

**Contexte :** Je baisse le flow de la tour de purge à 100% au lieu de 200%, en espérant éviter les amas.

**Résultat ?**
Toujours des pâtés. Moins gros, mais suffisamment pour provoquer des collisions et des décrochages de couche. La wipe tower reste un problème structurel dans ce contexte.

![](/images/article_images/2026/01/2026-01-11%2001.22.17.jpg)

**Leçon retenue :**
La wipe tower n'a pas de sens quand tu changes manuellement de filament. Autant s'en passer complètement.

---

## Ce qui fonctionne enfin : M600 + aucune wipe tower

Après ces échecs, j'ai trouvé la config qui marche de manière fiable :

### Principe

- **Pas de wipe tower** : elle ne sert à rien puisque tu purges déjà manuellement lors du chargement du nouveau filament.
- **M600 dans le G-code de changement d'outil** : force une pause, décharge l'ancien filament, attend que tu charges le nouveau, puis purge automatiquement.
- **Purge manuelle légère** si tu utilises des filaments blended (comme le _Oh My Gold_ de Prusament) : ils ont tendance à se mélanger un peu plus, donc lors de la purge de changement, n'hésite pas à dire qu'il faut un peu plus de purge 😉.

### Configuration dans PrusaSlicer

#### 1. Active le MMU à extrudeur unique

Dans l'onglet **Printer Settings > General > Functionalities** :

- Saisie le nombre d'extrudeurs (ici 2) dans le champ **"Number of extruders"**
- Coche **"Use MMU2S as a single extruder"**

![](/images/article_images/2026/01/Screenshot-2026-01-11-00.03.29.jpg)

Dans l'onglet **Printer Settings > Extruder X** :

- Assigne une couleur à chaque extrudeur (ici, extrudeur 0 = noir, extrudeur 1 = or)

![](/images/article_images/2026/01/Screenshot-2026-01-11-00.04.15.jpg)

#### 2. Désactiver les perimètres croisés (optionnel mais vivement recommandé)

Dans l'onglet **Print Settings > Layer and perimeters > Quality** :

- Active **"Avoid crossing perimeters"** pour éviter les changements de couleur dans les parois.

![](/images/article_images/2026/01/Screenshot-2026-01-11-00.05.03.jpg)

#### 3. Désactiver la wipe tower

Dans l'onglet **Print Settings > Multiple Extruders** :
- Décoche **"Wipe tower"**

![](/images/article_images/2026/01/Screenshot-2026-01-11-00.05.48.jpg)

#### 4. Ajouter le M600 dans le G-code de changement d'outil

Dans l'onglet **Printer Settings > Custom G-code** :
- Va dans la section **"Tool change G-code"**
- Ajoute cette ligne :

```
M600 ; Pause pour changement de filament
```

![](/images/article_images/2026/01/Screenshot-2026-01-11-00.06.43.jpg)

#### 5. Assigner les couleurs aux objets

Dans l'interface 3D de PrusaSlicer, tu as importé ton modèle 3D et tu as déjà séparé les parties en couleurs.

- Sélectionne un objet (ou plusieurs pour gagner du temps)
- Assigne l'extrudeur (= une couleur) correspondant.

![](/images/article_images/2026/01/Screenshot-2026-01-11-00.07.26.jpg)

---

## Résultat final et enseignements

Avec cette config, j'ai pu imprimer ma boîte de tarot sans aucun souci. Les 20 changements de filament se sont déroulés proprement, sans clog, sans pâté, sans bavure.

{% include video.html src_mp4="/images/article_images/2026/01/VID_20260110_182239_327.mp4" poster="/images/article_images/2026/01/poster.jpg" desc="Petit rendu final de la boite" %}

### Points clés à retenir

- **La wipe tower n'a pas de sens en changement manuel** : elle est conçue pour les MMU qui ont besoin de purger rapidement entre chaque couleur.
- **Le M600 fait déjà une purge** : pas besoin d'en rajouter sauf si tu utilises des filaments qui se mélangent facilement.
- **Les clogs viennent souvent d'un excès de matière** : si tu purges trop ou trop vite, tu crées des amas qui finissent par boucher.

### Bonus : ça marche aussi sur Prusa Mini

Si vous avez une Prusa Mini, la méthode est la même. Ca sera sans doute un peu plus fastidieu car je ne suis pas sur de la position parking pour le changement du filament (et les petits poops de filament lors de la purge) mais c'est gérable.

---

## Télécharger le profil de réglage

Pour te faciliter la vie, voici un export de mes réglages PrusaSlicer :

→ [Télécharger le profil d'imprimante MK4s (.ini)](/images/article_images/2026/01/Original%20Prusa%20MK4S%20HF0.4%20nozzle%20-%20MM%20Extrudeur%20Unique.ini)<br>
→ [Télécharger le profil de réglages d'impressions (.ini 0,4mm nozzle)](/images/article_images/2026/01/Original%20Prusa%20MK4S%20HF0.4%20nozzle%20-%20MM%20Extrudeur%20Unique.ini)]

*(Ces fichiers sont compatibles avec PrusaSlicer 2.7.0 et supérieurs.)*

---

## Conclusion : multi-couleur accessible, même sans MMU

Si tu as une Prusa MK4S (ou Mini) et que tu veux te lancer dans l'impression multi-couleur sans investir dans un MMU, c'est totalement faisable. Ça demande juste un peu de rigueur dans la config et de la patience pendant les changements.

Les échecs font partie du processus — mais une fois que tu as trouvé la bonne config, ça roule tout seul.

---

### Envie de te lancer ?

Si cet article t'a donné envie de tester (ou de craquer pour une imprimante Prusa), tu peux utiliser mon lien parrain :

→ [Imprimante Prusa MK4s assemblée](https://www.prusa3d.com/product/original-prusa-mk4s-3d-printer/?p2p=%40clawfire)<br>
→ [Imprimante Prusa MK4s en kit](https://www.prusa3d.com/product/original-prusa-mk4s-3d-printer-kit/?p2p=%40clawfire)<br>
→ [Imprimante Prusa Mini+ semi assemblée](https://www.prusa3d.com/product/original-prusa-mini-semi-assembled-3d-printer-enclosure-bundle-5/?p2p=%40clawfire)<br>
→ [Imprimante Prusa Mini+ en kit](https://www.prusa3d.com/product/original-prusa-mini-kit-enclosure-bundle-5/?p2p=%40clawfire)

ça me donne des points que je convertis en filament et tu en gagnera to aussi au passage, donc merci d'avance si tu passes par là. 🙏<br>
_(Note : c'est un lien sponsorisé, mais je ne touche pas de commission en euros — juste des crédits pour du consommable.)_

---

**Et toi, tu as déjà tenté le multi-filament manuel ?** Raconte-moi tes galères (ou tes réussites) en commentaire ou sur [Mastodon](https://m.thibau.lt/@clawfire).
