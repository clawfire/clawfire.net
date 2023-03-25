---
layout: post
title: "Installer Google Drive Stream File sur macOS"
date: "2018-05-03 11:38:23 +0200"
tags:
  - Astuce
  - Nerdz
featured_image: https://unsplash.com/photos/2wFRkQFDxS0/download
---
J'ai récemment eu un nouveau mac pour le taf, et bien que j'utilise homebrew pour tout installer rapidement sur mon mac, en plus qu'un petit dépot de code avec mes dotfiles, j'ai eu un petit soucis quand il est venu le temps de lancer l'outil de synchronisation Google Drive : Google Drive Stream File.

Celui ci demande à utiliser des fonction d'accessibilité avancée pour faire la synchronisation en tache de fond, ce qui est normal, et macOS bloque par défaut ce genre d'autorisations. Vous devez explicitement donner au logiciel des droits pour manipuler vos fichier. Normal.

Cependant il doit y avoir un bug dans le processus de la version actuelle de Google Drive Stream File qui fait qu'il plante lorsqu'on clique sur le bouton du message qu'il nous explique pourquoi il faut donner les droits. Du coup l'app ne tourne plus et impossible de l'autoriser dans le panneau de préférence Sécurité de macOS.

Voici donc le workaround que j'ai trouvé :

1. Lancez Google Drive Stream File
2. Lorsque le message (buggué en français d'ailleurs) de l'app s'affiche, ne cliquez pas sur le bouton mais lancez  > Préférences Système > Sécurité
3. Là vous devriez voir un bouton `Autoriser` en bas de la fenêtre avec le non de Google à gauche. Cliquez dessus.
4. Revenez au message de l'app Google Drive Stream File, cliquez sur le bouton, l'app plante.
5. Allez quitter l'app via l'icône dans la barre macOS en haut puis relancez l'app. Ca marche !

Laborieux mais ça fonctionne ;)
