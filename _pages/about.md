---
title: About
permalink: /about/
layout: page
fmContentType: Page
slug: ""
---

J'ai <span id="myAge">environ 30</span> ans.

Je suis [Mr. Ours Luxebourg 2016][mr bear 2016 fb], je participe activement à la [communauté ours au Luxembourg][bear dukes fb], j'ai co-organisé la [première Bear Pride de Luxembourg](https://www.facebook.com/events/1544314182538244/) et j'organise les soirées [Woof Men-only Party], des soirées bears & Fetish. Je fait parti du collectif [WR] qui regroupe les organisateurs de soirées LGBT+ au Luxembourg dans des actions caritatives.

J'ai eu une société, mais ça c'est mal passé avec mon associé qui a fini par fermer salement la société lorsque j'ai voulu arréter notre collaboration. Depuis j'ai un job, qui consiste principalement dans l'élaboration d'interface utilisateur pour des applications web, ainsi que la conception de toute l'expérience d'utilisation de ses dernières.

J'ai pas mal de passions, que je partage un peu ici, je suis ce qu'on pourrait appeler un geek/nerd concernant l'informatique, mais c'est uniquement parceque des gens trouvent fou ce que je trouve juste normal :) Tout dépends de votre notion de la normalité.

J'aborde aussi les thématiques liées à l'homosexualité, les MST, en particulier le VIH, la tolérance, l'ouverture d'esprit, ... J'ai été pendant 4 ans avec un mec qui était séropo et je n'en suis pas mort ni n'ai contracté de MST.

J'ai des affinités avec le Parti Pirate (France - Section Expat) mais je n'ai malheureusement pas assez de temps à leur consacrer pour être un membre actif. Le reste de mes activités et de mes passions me prends tout mon temps, sans compter les nombreux déplacements dans l'Europe tout au long de l'année.

J'utilise PGP, ma clé est `AB98FAC4`. Si vous n'utilisez rien de tout cela mais que vous voulez quand même m'écrire de façon sécurisée, vous pouvez utiliser le [formulaire de contact](/contact/) qui inclus une version web de GPG qui chifrera votre message avant son envoi.

J'utilise [FontAwesome] pour les icons de ce site, ma photo principale est de [Hellgy] et les fonts du projet [Google Fonts][google fonts] (désolé si cela leur permet de vous suivre en ligne).

Je track le moins de choses possibles sur vous, c'est pour cela que je n'ai pas de service d'analytics. Malheuresement, les polices de caractères fournies par Google leur permettent de vous tracer. J'espère pouvoir résoudre cela un jour.

<script type="text/javascript">
function calculateAge(birthDate) {
  const now = new Date();
  const birth = new Date(birthDate);
  const diff = now - birth;
  const years = diff / (1000 * 60 * 60 * 24 * 365.25);
  return years.toFixed(10);
}

function updateAge() {
  const birthDate = '1988-08-02'; // YYYY-MM-DD format
  const age = calculateAge(birthDate);
  document.getElementById('myAge').textContent = age;
}

// Update age immediately and then every 0.2 seconds
updateAge();
setInterval(updateAge, 100);
</script>

[mr bear 2016 fb]: https://www.facebook.com/mr.bear.luxembourg/

[bear dukes fb]: https://www.facebook.com/luxembourgbears/

[woof men-only party]: https://woofmenonly.com

[hellgy]: https://www.redisdead.net/

[google fonts]: https://fonts.google.com/

[fontawesome]: https://fontawesome.com/

[wr]: https://weare.lu
