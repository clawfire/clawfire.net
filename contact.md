---
title: Contact
permalink: "/contact/"
layout: page
---
J'utilise PGP, ma clé est `AB98FAC4` et j'utilise également [Keybase](https://keybase.io/clawfire). Si vous n'utilisez rien de tout cela mais que vous voulez quand même m'écrire de façon sécurisée, vous pouvez utiliser le formulaire ci dessous qui inclus une version web de GPG qui chifrera votre message avant son envoi.

<form action="" id="contact-form">
  <div class="input-group">
    <label for="nom">Nom</label>
    <input type="text" placeholder="John Doe (obligatoire)" required name="nom">
  </div>
  <div class="input-group">
    <label for="email">Email</label>
    <input type="email" placeholder="john@doe.net (obligatoire)" required name="email">
  </div>
  <div class="input-group">
    <label for="sujet">Sujet</label>
    <input type="text" name="sujet" placeholder="Mon sujet super interessant ici (optionnel)">
  </div>
  <div class="textarea-group">
    <label for="">Message</label>
    <textarea name="message" id="" cols="30" rows="10" required placeholder="Mon super message (obligatoire)"></textarea>
  </div>
  <div class="button-group">
    <button type="submit">🔐 & envoyer</button>
  </div>
</form>
