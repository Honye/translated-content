---
title: Fondamentaux du texte HTML
slug: Learn/HTML/Introduction_to_HTML/HTML_text_fundamentals
tags:
  - Apprendre
  - Débutant
  - Guide
  - HTML
  - Introduction à l'HTML
  - Listes
  - Paragraphes
  - Texte
  - Titres
  - sémantique
translation_of: Learn/HTML/Introduction_to_HTML/HTML_text_fundamentals
original_slug: Apprendre/HTML/Introduction_à_HTML/HTML_text_fundamentals
---
<div>{{LearnSidebar}}</div>

<div>{{PreviousMenuNext("Learn/HTML/Introduction_to_HTML/The_head_metadata_in_HTML", "Learn/HTML/Introduction_to_HTML/Creating_hyperlinks", "Learn/HTML/Introduction_to_HTML")}}</div>

<p>L'un des principaux buts de HTML est de structurer du texte et lui donner du sens (ce que l'on appelle la {{glossary("sémantique")}}) afin que le navigateur puisse l'afficher correctement. Cet article explique comment {{glossary("HTML")}} peut être utilisé pour structurer une page en ajoutant des titres et des paragraphes, en marquant des emphases, en créant des listes, et bien plus encore.</p>

<table class="standard-table">
 <tbody>
  <tr>
   <th scope="row">Pré-requis:</th>
   <td>
    <p>Connaître les bases du langage HTML, telles que traitées à la page <a href="/fr/docs/Apprendre/HTML/Introduction_%C3%A0_HTML/Getting_started">Commencer avec le HTML</a>.</p>
   </td>
  </tr>
  <tr>
   <th scope="row">Objectif:</th>
   <td>
    <p>Apprendre comment ajouter des balises dans une page de texte simple pour la structurer et lui donner du sens — en incluant des paragraphes, des titres, des listes, des emphases et des citations.</p>
   </td>
  </tr>
 </tbody>
</table>

<h2 id="Les_bases_titres_et_paragraphes">Les bases : titres et paragraphes</h2>

<p>La plupart des textes structurés comprennent des titres et des paragraphes, que ce soit dans les romans, les journaux, les livres scolaires, les magazines, etc.</p>

<p><img alt="An example of a newspaper front cover, showing use of a top level heading, subheadings and paragraphs." src="newspaper_small.jpg"></p>

<p>Le contenu structuré facilite la lecture et la rend plus agréable.</p>

<p>En HTML, les paragraphes doivent être contenus dans un élément {{htmlelement("p")}}, comme ceci :</p>

<pre class="brush: html">&lt;p&gt;Je suis un paragraphe, oh oui je le suis.&lt;/p&gt;</pre>

<p>Chaque titre doit être contenu dans un élément titre :</p>

<pre class="brush: html">&lt;h1&gt;Je suis le titre de l'histoire.&lt;/h1&gt;</pre>

<p>Il y a 6 éléments de titre — {{htmlelement("h1")}}, {{htmlelement("h2")}}, {{htmlelement("h3")}}, {{htmlelement("h4")}}, {{htmlelement("h5")}}, et {{htmlelement("h6")}}. Chaque élément représente un niveau de titre différent ; <code>&lt;h1&gt;</code> représente le titre principal, <code>&lt;h2&gt;</code> représente un sous-titre, <code>&lt;h3&gt;</code> représente un sous-sous-titre, et ainsi de suite jusqu'au niveau de titre le plus bas qui correspond à <code>&lt;h6&gt;</code>.</p>

<h3 id="Implémentation_de_la_hiérarchie_structurale">Implémentation de la hiérarchie structurale</h3>

<p>Dans une histoire, la balise <code>&lt;h1&gt;</code> représenterait le titre de l'histoire, les balises <code>&lt;h2&gt;</code> représenteraient les titres des chapitres, les balises <code>&lt;h3&gt;</code> les sous-sections des chapitres, en poursuivant ainsi jusqu'à la balise <code>&lt;h6&gt;</code>.</p>

<pre class="brush: html">&lt;h1&gt;L'ennui mortel&lt;/h1&gt;

&lt;p&gt;par Chris Mills&lt;/p&gt;

&lt;h2&gt;Chapitre I : La nuit noire&lt;/h2&gt;

&lt;p&gt;Il faisait nuit noire. Quelque part une chouette ululait. La pluie tombait sur ...&lt;/p&gt;

&lt;h2&gt;Chapitre II : Le silence éternel&lt;/h2&gt;

&lt;p&gt;Notre protagoniste ne pouvait même pas murmurer à l'ombre de la silhouette...&lt;/p&gt;

&lt;h3&gt;Le spectre parle&lt;/h3&gt;

&lt;p&gt;Plusieurs heures s'étaient écoulées, quand soudain le spectre assis se releva et s'exclama : « S'il vous plaît, ayez pitié de mon âme ! »...&lt;/p&gt;</pre>

<p>C'est vous qui décidez ce que représentent les éléments utilisés tant que la hiérarchie a du sens. Vous devez cependant garder à l'esprit quelques bonnes pratiques lorsque vous créez de telles structures :</p>

<ul>
 <li>Il est préférable de n'utiliser qu'un seul <code>&lt;h1&gt;</code> par page — c'est le niveau principal, et tous les autres devraient être de niveau inférieur.</li>
 <li>Assurez-vous d'utiliser les balise de titre dans l'ordre correct et logique : <code>&lt;h1&gt;</code> puis <code>&lt;h2&gt;</code>, puis <code>&lt;h3&gt;</code> et ainsi de suite.</li>
 <li>Bien qu'il y ait 6 niveaux de titre (de <code>&lt;h1&gt;</code> à <code>&lt;h6&gt;</code>), Il est déconseillé d'utiliser plus de trois niveaux dans une page. Les documents avec beaucoup de niveaux deviennent complexes et difficiles à parcourir. Dans ce cas, il est préférable de partager le contenu sur plusieurs pages.</li>
</ul>

<h3 id="Pourquoi_faut-il_structurer_un_document">Pourquoi faut-il structurer un document ?</h3>

<p>Pour répondre à cette question, regardons la page <a href="https://github.com/mdn/learning-area/blob/master/html/introduction-to-html/html-text-formatting/text-start.html">text-start.html</a> — le point de départ de l'exemple que nous allons utiliser dans cet article (une recette). Enregistrez une copie de ce fichier sur votre ordinateur car vous en aurez besoin pour les exercices qui vont suivre. Le corps de ce document contient plusieurs parties sans aucune balise ; elles sont seulement séparées par des retours chariots (obtenus en pressant la touche <kbd>Entrée</kbd> ou <kbd>⏎</kbd>)</p>

<p>Cependant, si l'on ouvre ce document dans un navigateur, il sera affiché sous forme d'un gros bloc de texte !</p>

<p><img alt="Une page Web qui montre un mur de texte non formaté, parce qu'il n'y a pas d'éléments sur la page pour la structurer." src="recette.png"></p>

<p>Ceci est dû au fait qu'il n'y a aucun élément indiquant la structure du contenu, et donc le navigateur ne sait pas différencier ce qui est un titre d'un paragraphe. De plus :</p>

<ul>
 <li>Les visiteurs d'une page web la parcourent pour trouver le contenu pertinent. Par conséquent, ils ne lisentsouvent que les titres (généralement <a href="http://www.nngroup.com/articles/how-long-do-users-stay-on-web-pages/">nous ne passons que très peu de temps sur une page web</a>). S'ils ne trouvent pas le contenu souhaité en quelques secondes, ils seront probablement déçus et chercheront l'information souhaitée ailleurs.</li>
 <li>Les moteurs de recherche, lorsqu'ils indexent votre page, prennent en considération les titres en tant que mots‑clés ce qui influe sur le classement de la page lors d'une recherche. Sans titre, une page aura un faible référencement (voir {{glossary("SEO")}} (Search Engine Optimization).</li>
 <li>Les personnes malvoyantes ne pouvant lire votre page peuvent utiliser des <a href="https://fr.wikipedia.org/wiki/Lecteur_d%27%C3%A9cran">lecteurs d'écran</a>. Ces logiciels permettent d'accéder rapidement à une partie du texte. Pour cela, ils lisent les titres de votre document aux utilisateurs, leur permettant ainsi de trouver rapidement l'information dont ils ont besoin. Si les titres ne sont pas disponibles, les lecteurs d'écran lisent tout le document, le rendant peu accessible aux personnes avec un handicap visuel.</li>
 <li>Pour composer un style de contenu avec le {{glossary("CSS")}} ou réaliser des choses intéressantes avec le {{glossary("JavaScript")}}, vous devez avoir des éléments enveloppant les contenus pertinents, ce qui permet ensuite de les cibler avec CSS/JavaScript.</li>
</ul>

<p>Il est donc nécessaire d'ajouter des balises de structuration du contenu.</p>

<h3 id="Apprentissage_actif_structurer_le_contenu">Apprentissage actif : structurer le contenu</h3>

<p>Dans l'exemple ci-dessous, ajoutez des balises dans le texte de la zone Code modifiable afin qu'il fasse apparaître un titre et deux paragraphes dans le champ <em>Sortie directe</em>.</p>

<p>Si vous faites une erreur, vous pouvez recommencer en appuyant sur le bouton <em>Réinitialiser</em>. Si vous êtes bloqués, appuyez sur le bouton <em>Voir la solution</em> pour afficher la réponse.</p>

<pre class="brush: html hidden">&lt;h2&gt;Sortie directe&lt;/h2&gt;

&lt;div class="output" style="min-height: 50px;"&gt;
&lt;/div&gt;

&lt;h2&gt;Code modifiable&lt;/h2&gt;
&lt;p class="a11y-label"&gt;Pressez Esc pour sortir le focus de la zone de code (Tab insère une tabulation).&lt;/p&gt;

&lt;textarea id="code" class="input" style="min-height: 100px; width: 95%"&gt;Ma courte histoire : je suis une policière et mon nom est Trish.

Mes jambes sont en carton et je suis mariée à un poisson.&lt;/textarea&gt;

&lt;div class="playable-buttons"&gt;
  &lt;input id="reset" type="button" value="Réinitialiser"&gt;
  &lt;input id="solution" type="button" value="Voir la solution"&gt;
&lt;/div&gt;</pre>

<pre class="brush: css hidden">html {
  font-family: sans-serif;
}

h2 {
  font-size: 16px;
}

.a11y-label {
  margin: 0;
  text-align: right;
  font-size: 0.7rem;
  width: 98%;
}

body {
  margin: 10px;
  background: #f5f9fa;
}</pre>

<pre class="brush: js hidden">var textarea = document.getElementById('code');
var reset = document.getElementById('reset');
var solution = document.getElementById('solution');
var output = document.querySelector('.output');
var code = textarea.value;
var userEntry = textarea.value;

function updateCode() {
  output.innerHTML = textarea.value;
}

reset.addEventListener('click', function() {
  textarea.value = code;
  userEntry = textarea.value;
  solutionEntry = htmlSolution;
  solution.value = 'Voir la solution';
  updateCode();
});

solution.addEventListener('click', function() {
  if(solution.value === 'Voir la solution') {
    textarea.value = solutionEntry;
    solution.value = 'Cacher la solution';
  } else {
    textarea.value = userEntry;
    solution.value = 'Voir la solution';
  }
  updateCode();
});

var htmlSolution = '&lt;h1&gt;Ma courte histoire&lt;/h1&gt;\n&lt;p&gt;Je suis une policière et mon nom est Trish.&lt;/p&gt;\n&lt;p&gt;Mes jambes sont en carton et je suis mariée à un poisson.&lt;/p&gt;';
var solutionEntry = htmlSolution;

textarea.addEventListener('input', updateCode);
window.addEventListener('load', updateCode);

// bloquer le déplacement du focus hors de la zone texte avec la touche Tab
// faire en sorte que la touche Tab mette une tabulation à la position du curseur

textarea.onkeydown = function(e){
  if (e.keyCode === 9) {
    e.preventDefault();
    insertAtCaret('\t');
  }

  if (e.keyCode === 27) {
    textarea.blur();
  }
};

function insertAtCaret(text) {
  var scrollPos = textarea.scrollTop;
  var caretPos = textarea.selectionStart;

  var front = (textarea.value).substring(0, caretPos);
  var back = (textarea.value).substring(textarea.selectionEnd, textarea.value.length);
  textarea.value = front + text + back;
  caretPos = caretPos + text.length;
  textarea.selectionStart = caretPos;
  textarea.selectionEnd = caretPos;
  textarea.focus();
  textarea.scrollTop = scrollPos;
}

// Mettre à jour le code utilisateur enregistré chaque fois que l'utilisateur
// met à jour le texte du code

textarea.onkeyup = function(){
  // nous souhaitons uniquement enregistrer l'état quand le code utilisateur est montré,
  // non la solution, donc elle n'est pas enregistrée sur le code utilisateur
  if(solution.value === 'Voir la solution') {
    userEntry = textarea.value;
  } else {
    solutionEntry = textarea.value;
  }

  updateCode();
};</pre>

<p>{{ EmbedLiveSample('Apprentissage_actif_structurer_le_contenu', 700, 370) }}</p>

<h3 id="Pourquoi_a-t-on_besoin_de_sémantique">Pourquoi a-t-on besoin de sémantique ?</h3>

<p>La sémantique est utilisée partout autour de nous — on se fie à nos précédentes experiences pour savoir à quoi servent les objets du quotidien; quand on voit quelque chose, on sait à quoi cela sert. Par exemple, on s'attend à ce qu'un feu rouge de signalisation signifie « Stop » et qu'un feu vert signifie « Avancez ». Les choses peuvent vite devenir plus compliquées si de mauvaises sémantiques sont appliquées (existe-t-il un pays dans lequel un feu rouge signifie que l'on peut passer ? Je ne l'espère pas.)</p>

<p>Dans la même optique, il faut s'assurer que l'on utilise les bons élements et que l'on donne la bonne signification, la bonne fonction et la bonne apparence à notre contenu. Dans ce contexte, l'élément {{htmlelement("h1")}} est aussi un élement sémantique. Il donne au texte auquel il s'applique la fonction (ou la signification) de « titre principal de la page ».</p>

<pre class="brush: html">&lt;h1&gt;Ceci est un titre principal&lt;/h1&gt;</pre>

<p>Par défaut, le navigateur l'affiche avec une police de caractères de grande taille pour qu'il ait l'apparence d'un titre (même si vous pourriez lui donner l'apparence de n'importe quel élément avec le CSS). Plus important encore, sa valeur sémantique est utilisée de différentes manières, notamment par les moteurs de recherche ou les lecteurs d'écran (comme expliqué plus haut).</p>

<p>D'autre part, vous pouvez faire ressembler n'importe quel élément à un titre principal. Par exemple :</p>

<pre class="brush: html">&lt;span style="font-size: 32px; margin: 21px 0;"&gt;Est-ce un titre principal?&lt;/span&gt;</pre>

<p>C'est un élément {{htmlelement("span")}}. Il n'a pas de valeur sémantique. Il s'utilise autour d'un contenu auquel vous souhaitez appliquer un style CSS (ou le modifier avec du JavaScript) sans lui donner une signification supplémentaire (vous en apprendrez plus à ce propos plus loin dans ce cours). Nous lui avons appliqué du CSS pour qu'il ressemble à un titre principal, mais comme il n'a pas de valeur sémantique, il ne bénéficie d'aucune des valeurs sémantiques décrites plus haut. Il est conseillé d'utiliser des éléments HTML adaptés à leur rôle.</p>

<h2 id="Listes">Listes</h2>

<p>Intéressons-nous maintenant aux listes. Il y a des listes partout dans la vie — de la liste de courses à la liste de directions que vous suivez inconsciemment pour rentrer chez vous tous les jours, sans oublier la liste des instructions que vous suivez dans ce tutoriel ! Les listes sont aussi très répandues sur le Web, nous allons nous intéresser aux trois différents types de liste.</p>

<h3 id="Listes_non-ordonnées">Listes non-ordonnées</h3>

<p>Les listes non-ordonnées sont utilisées pour représenter des listes d'éléments pour lesquelles l'ordre n'a pas d'importance. Prenons par exemple une liste de courses :</p>

<pre>lait
œufs
pain
houmous</pre>

<p>Les listes non-ordonnées débutent par un élément {{htmlelement("ul")}} (<em><strong>u</strong>norderd <strong>l</strong>ist</em>) qui enveloppe tous les éléments de la liste:</p>

<pre class="brush: html">&lt;ul&gt;
lait
œufs
pain
houmous
&lt;/ul&gt;</pre>

<p>Chaque item est contenu dans un élément {{htmlelement("li")}} (<em><strong>l</strong>ist <strong>i</strong>tem</em>):</p>

<pre class="brush: html">&lt;ul&gt;
  &lt;li&gt;lait&lt;/li&gt;
  &lt;li&gt;œufs&lt;/li&gt;
  &lt;li&gt;pain&lt;/li&gt;
  &lt;li&gt;houmous&lt;/li&gt;
&lt;/ul&gt;</pre>

<h4 id="Apprentissage_actif_mettre_des_balises_à_une_liste_non-ordonnée">Apprentissage actif : mettre des balises à une liste non-ordonnée</h4>

<p>Modifiez l'exemple ci-dessous pour créer votre propre liste HTML non-ordonnée.</p>

<pre class="brush: html hidden">&lt;h2&gt;Live output&lt;/h2&gt;

&lt;div class="output" style="min-height: 50px;"&gt;
&lt;/div&gt;

&lt;h2&gt;Code modifiable&lt;/h2&gt;
&lt;p class="a11y-label"&gt;Pressez Esc pour sortir le focus de la zone de code (Tab insère une tabulation).&lt;/p&gt;

&lt;textarea id="code" class="input" style="min-height: 100px; width: 95%"&gt;lait
œufs
pain
houmous&lt;/textarea&gt;

&lt;div class="playable-buttons"&gt;
  &lt;input id="reset" type="button" value="Réinitialiser"&gt;
  &lt;input id="solution" type="button" value="Voir la solution"&gt;
&lt;/div&gt;</pre>

<pre class="brush: css hidden">html {
  font-family: sans-serif;
}

h2 {
  font-size: 16px;
}

.a11y-label {
  margin: 0;
  text-align: right;
  font-size: 0.7rem;
  width: 98%;
}

body {
  margin: 10px;
  background: #f5f9fa;
}</pre>

<pre class="brush: js hidden">var textarea = document.getElementById('code');
var reset = document.getElementById('reset');
var solution = document.getElementById('solution');
var output = document.querySelector('.output');
var code = textarea.value;
var userEntry = textarea.value;

function updateCode() {
  output.innerHTML = textarea.value;
}

reset.addEventListener('click', function() {
  textarea.value = code;
  userEntry = textarea.value;
  solutionEntry = htmlSolution;
  solution.value = 'Voir la solution';
  updateCode();
});

solution.addEventListener('click', function() {
  if(solution.value === 'Voir la solution') {
    textarea.value = solutionEntry;
    solution.value = 'Cacher la solution';
  } else {
    textarea.value = userEntry;
    solution.value = 'Voir la solution';
  }
  updateCode();
});

var htmlSolution = '&lt;ul&gt;\n&lt;li&gt;lait&lt;/li&gt;\n&lt;li&gt;œufs&lt;/li&gt;\n&lt;li&gt;pain&lt;/li&gt;\n&lt;li&gt;houmous&lt;/li&gt;\n&lt;/ul&gt;';
var solutionEntry = htmlSolution;

textarea.addEventListener('input', updateCode);
window.addEventListener('load', updateCode);

// bloquer le déplacement du focus hors de la zone texte avec la touche Tab
// faire en sorte que la touche Tab mette une tabulation à la position du curseur

textarea.onkeydown = function(e){
  if (e.keyCode === 9) {
    e.preventDefault();
    insertAtCaret('\t');
  }

  if (e.keyCode === 27) {
    textarea.blur();
  }
};

function insertAtCaret(text) {
  var scrollPos = textarea.scrollTop;
  var caretPos = textarea.selectionStart;

  var front = (textarea.value).substring(0, caretPos);
  var back = (textarea.value).substring(textarea.selectionEnd, textarea.value.length);
  textarea.value = front + text + back;
  caretPos = caretPos + text.length;
  textarea.selectionStart = caretPos;
  textarea.selectionEnd = caretPos;
  textarea.focus();
  textarea.scrollTop = scrollPos;
}

// Mettre à jour le code utilisateur enregistré chaque fois que l'utilisateur
// met à jour le texte du code

textarea.onkeyup = function(){
  // nous souhaitons uniquement enregistrer l'état quand le code utilisateur est montré,
  // non la solution, donc elle n'est pas enregistrée sur le code utilisateur
  if(solution.value === 'Voir la solution') {
    userEntry = textarea.value;
  } else {
    solutionEntry = textarea.value;
  }

  updateCode();
};</pre>

<p>{{ EmbedLiveSample('Apprentissage_actif_mettre_des_balises_à_une_liste_non-ordonnée', 700, 400) }}</p>

<h3 id="Listes_ordonnées">Listes ordonnées</h3>

<p>Les listes ordonnées permettent de représenter des listes dans lesquelles l'ordre des éléments a de l'importance — prenons par exemple une série de directions à suivre:</p>

<pre>Roulez jusqu'au bout de la route
Tournez à droite
Allez tout droit aux deux premiers ronds-points
Tournez à gauche au troisième rond-point
Roulez sur 300 mètres, l'école est sur votre droite</pre>

<p>Les balises suivent la même structure que pour les listes ordonnées, à cela près que la liste est contenue dans l'élément {{htmlelement("ol")}} (<em><strong>o</strong>rdered <strong>l</strong>ist</em>), et non dans <code>&lt;ul&gt;</code>:</p>

<pre class="brush: html">&lt;ol&gt;
  &lt;li&gt;Roulez jusqu'au bout de la route&lt;/li&gt;
  &lt;li&gt;Tournez à droite&lt;/li&gt;
  &lt;li&gt;Allez tout droit aux deux premiers ronds-points&lt;/li&gt;
  &lt;li&gt;Tournez à gauche au troisième rond-point&lt;/li&gt;
  &lt;li&gt;Roulez sur 300 mètres, l'école est sur votre droite&lt;/li&gt;
&lt;/ol&gt;</pre>

<h4 id="Apprentissage_actif_baliser_une_liste_ordonnée">Apprentissage actif : baliser une liste ordonnée</h4>

<p>Modifiez l'exemple ci‑dessous pour créer votre propre liste HTML ordonnée.</p>

<pre class="brush: html hidden">&lt;h2&gt;Sortie directe&lt;/h2&gt;

&lt;div class="output" style="min-height: 50px;"&gt;
&lt;/div&gt;

&lt;h2&gt;Code modifiable&lt;/h2&gt;
&lt;p class="a11y-label"&gt;Pressez Esc pour sortir le focus de la zone de code (Tab insère une tabulation).&lt;/p&gt;

&lt;textarea id="code" class="input" style="min-height: 200px; width: 95%"&gt;Roulez jusqu'au bout de la route
Tournez à droite
Allez tout droit aux deux premiers rond-points
Tournez à gauche au troisième rond-point
Roulez sur 300 mètres, l'école est sur votre droite&lt;/textarea&gt;

&lt;div class="playable-buttons"&gt;
  &lt;input id="reset" type="button" value="Réinitialiser"&gt;
  &lt;input id="solution" type="button" value="Voir la solution"&gt;
&lt;/div&gt;</pre>

<pre class="brush: css hidden">html {
  font-family: sans-serif;
}

h2 {
  font-size: 16px;
}

.a11y-label {
  margin: 0;
  text-align: right;
  font-size: 0.7rem;
  width: 98%;
}

body {
  margin: 10px;
  background: #f5f9fa;
}</pre>

<pre class="brush: js hidden">var textarea = document.getElementById('code');
var reset = document.getElementById('reset');
var solution = document.getElementById('solution');
var output = document.querySelector('.output');
var code = textarea.value;
var userEntry = textarea.value;

function updateCode() {
  output.innerHTML = textarea.value;
}

reset.addEventListener('click', function() {
  textarea.value = code;
  userEntry = textarea.value;
  solutionEntry = htmlSolution;
  solution.value = 'Voir la solution';
  updateCode();
});

solution.addEventListener('click', function() {
  if(solution.value === 'Voir la solution') {
    textarea.value = solutionEntry;
    solution.value = 'Cacher la solution';
  } else {
    textarea.value = userEntry;
    solution.value = 'Voir la solution';
  }
  updateCode();
});

var htmlSolution = '&lt;ol&gt;\n&lt;li&gt;Roulez jusqu\'au bout de la route&lt;/li&gt;\n&lt;li&gt;Tournez à droite&lt;/li&gt;\n&lt;li&gt;Allez tout droit aux deux premiers rond-points&lt;/li&gt;\n&lt;li&gt;Tournez à gauche au troisième rond-point&lt;/li&gt;\n&lt;li&gt;Roulez sur 300 mètres, l\'école est sur votre droite&lt;/li&gt;\n&lt;/ol&gt;';
var solutionEntry = htmlSolution;

textarea.addEventListener('input', updateCode);
window.addEventListener('load', updateCode);

// bloquer le déplacement du focus hors de la zone texte avec la touche Tab
// faire en sorte que la touche Tab mette une tabulation à la position du curseur

textarea.onkeydown = function(e){
  if (e.keyCode === 9) {
    e.preventDefault();
    insertAtCaret('\t');
  }

  if (e.keyCode === 27) {
    textarea.blur();
  }
};

function insertAtCaret(text) {
  var scrollPos = textarea.scrollTop;
  var caretPos = textarea.selectionStart;

  var front = (textarea.value).substring(0, caretPos);
  var back = (textarea.value).substring(textarea.selectionEnd, textarea.value.length);
  textarea.value = front + text + back;
  caretPos = caretPos + text.length;
  textarea.selectionStart = caretPos;
  textarea.selectionEnd = caretPos;
  textarea.focus();
  textarea.scrollTop = scrollPos;
}

// Mettre à jour le code utilisateur enregistré chaque fois que l'utilisateur
// met à jour le texte du code

textarea.onkeyup = function(){
  // nous souhaitons uniquement enregistrer l'état quand le code utilisateur est montré,
  // non la solution, donc elle n'est pas enregistrée sur le code utilisateur
  if(solution.value === 'Voir la solution') {
    userEntry = textarea.value;
  } else {
    solutionEntry = textarea.value;
  }

  updateCode();
};</pre>

<p>{{ EmbedLiveSample('Apprentissage_actif_baliser_une_liste_ordonnée', 700, 500) }}</p>

<h3 id="Apprentissage_actif_mettre_des_balises_pour_une_recette_de_cuisine">Apprentissage actif : mettre des balises pour une recette de cuisine</h3>

<p>Si vous êtes arrivé jusqu'ici dans l'article, vous avez toutes les connaissances nécessaires pour mettre en forme la recette de cuisine donnée en exemple. Vous pouvez soit télécharger le fichier <a href="https://github.com/mdn/learning-area/blob/master/html/introduction-to-html/html-text-formatting/text-start.html">text-start.html</a> et le modifier de votre côté, soit faire l'exercice dans l'exemple modifiable ci-dessous. Il est conseillé de le modifier localement, sur votre machine, car vous pourrez alors enregistrer votre travail. Si vous utilisez l'exemple modifiable de cette page, le travail sera perdu à l'ouverture suivante de la page. Chaque méthode a ses avantages et ses inconvénients.</p>

<pre class="brush: html hidden">&lt;h2&gt;Sortie directe&lt;/h2&gt;

&lt;div class="output" style="min-height: 50px;"&gt;
&lt;/div&gt;

&lt;h2&gt;Code modifiable&lt;/h2&gt;
&lt;p class="a11y-label"&gt;Pressez Esc pour sortir le focus de la zone de code (Tab insére une tabulation).&lt;/p&gt;

&lt;textarea id="code" class="input" style="min-height: 200px; width: 95%"&gt;Recette rapide de l'houmous

 Cette recette permet d'obtenir rapidement un houmous savoureux, sans complications. C'est une adaptation de plusieurs recettes différentes que j'ai essayées au fil des ans.

  L'houmous est une délicieuse pâte épaisse utilisée dans les plats en Grèce et au Moyen-Orient. Il s'accorde très bien avec la salade, les viandes grillées et du pain calabrais.

  Ingrédients

  1 boîte (400 g) de pois chiches (garbanzos)
  175g de crème de sésame
  6 tomates séchées
  un demi poivron rouge
  une pincée de piment de Cayenne
  1 gousse d'ail
  un trait d'huile d'olive

  Ôter la peau de l'ail et le hacher grossièrement.
  Enlever les graines et la tige du poivron, le hacher grossièrement.
  Mettre tous les ingrédients dans un robot et mixer jusqu'à l'obtention d'une pâte.
  Si vous voulez un houmous grenu, ne le mixez pas trop longtemps.
 Si vous voulez un houmous lisse, mixez-le plus longtemps.

  Pour des saveurs différentes, vous pouvez essayer d'y mettre un peu de jus de citron et de coriandre, du tabasco, de la limette et du chipotle, de la harissa et de la menthe ou des épinards et de la feta. Essayez et voyez ce qui vous va.

  Conservation

  Mettez l'houmous fini au réfrigérateur dans un récipient fermé. Vous le garderez ainsi pendant environ une semaine. S'il se met à fermenter, jettez‑le sans hésiter.

  L'houmous peut être congelé ; consommez‑le dans les deux mois qui suivent sa congélation.&lt;/textarea&gt;

&lt;div class="playable-buttons"&gt;
  &lt;input id="reset" type="button" value="Réinitialiser"&gt;
  &lt;input id="solution" type="button" value="Voir la solution"&gt;
&lt;/div&gt;</pre>

<pre class="brush: css hidden">html {
  font-family: sans-serif;
}

h2 {
  font-size: 16px;
}

.a11y-label {
  margin: 0;
  text-align: right;
  font-size: 0.7rem;
  width: 98%;
}

body {
  margin: 10px;
  background: #f5f9fa;
}</pre>

<pre class="brush: js hidden">var textarea = document.getElementById('code');
var reset = document.getElementById('reset');
var solution = document.getElementById('solution');
var output = document.querySelector('.output');
var code = textarea.value;
var userEntry = textarea.value;

function updateCode() {
  output.innerHTML = textarea.value;
}

reset.addEventListener('click', function() {
  textarea.value = code;
  userEntry = textarea.value;
  solutionEntry = htmlSolution;
  solution.value = 'Voir la solution';
  updateCode();
});

solution.addEventListener('click', function() {
  if(solution.value === 'Voir la solution') {
    textarea.value = solutionEntry;
    solution.value = 'Cacher la solution';
  } else {
    textarea.value = userEntry;
    solution.value = 'Voir la solution';
  }
  updateCode();
});

var htmlSolution = '&lt;h1&gt;Recette rapide de l\'houmous&lt;/h1&gt;\n\n&lt;p&gt;Cette recette permet d\'obtenir rapidement un houmous savoureux, sans complications. C\'est une adaptation de plusieurs recettes différentes que j\'ai essayées au fil des ans.&lt;/p&gt;\n\n&lt;p&gt;L\'houmous est une délicieuse pâte épaisse utilisée dans les plats en Grèce et au moyen-orient. Il s\'accorde très bien avec la salade, les viandes grillées et du pain calabrais.&lt;/p&gt;\n\n&lt;h2&gt;Ingrédients&lt;/h2&gt;\n\n&lt;ul&gt;\n&lt;li&gt;1 boîte (400 g) de pois chiches (garbanzos)&lt;/li&gt;\n&lt;li&gt;175g de crème de sésame&lt;/li&gt;\n&lt;li&gt;6 tomates séchées&lt;/li&gt;\n&lt;li&gt;un demi poivron rouge&lt;/li&gt;\n&lt;li&gt;une pincée de piment de Cayenne&lt;/li&gt;\n&lt;li&gt;1 gousse d\'ail&lt;/li&gt;\n&lt;li&gt;un trait d\'huile d\'olive&lt;/li&gt;\n&lt;/ul&gt;\n\n&lt;h2&gt;Instructions&lt;/h2&gt;\n\n&lt;ol&gt;\n&lt;li&gt;Ôter la peau de l\'ail et le hacher grossièrement.&lt;/li&gt;\n&lt;li&gt;Enlever les graines et la tige du poivron, le hacher grossièrement.&lt;/li&gt;\n&lt;li&gt;Mettre tous les ingrédients dans un robot mixer jusqu\'à l\'obtention d\'une pâte.&lt;/li&gt;\n&lt;li&gt;Si vous voulez un houmous grenu, ne le mixez pas trop longtemps.&lt;/li&gt;\n&lt;li&gt;Si vous voulez un houmous lisse, mixez-le plus longtemps.&lt;/li&gt;\n&lt;/ol&gt;\n\n&lt;p&gt;Pour des saveurs différentes, vous pouvez essayer d\'y mettre un peu de jus de citron et de coriandre, du tabasco, de la limette et du chipotle, de la harissa et de la menthe ou des épinards et de la feta. Essayez et voyez ce qui vous va.&lt;/p&gt;\n\n&lt;h2&gt;Conservation&lt;/h2&gt;\n\n&lt;p&gt;Mettez l\'houmous fini au réfrigérateur dans un récipient fermé. Vous le garderez ainsi pendant environ une semaine. S\'il se met à fermenter, jettez‑le sans hésiter.&lt;/p&gt;\n\n&lt;p&gt;L\'houmous peut être congelé ; consommez‑le dans les deux mois qui suivent sa congélation.&lt;/p&gt;';
var solutionEntry = htmlSolution;

textarea.addEventListener('input', updateCode);
window.addEventListener('load', updateCode);

// bloquer le déplacement du focus hors de la zone texte avec la touche Tab
// faire en sorte que la touche Tab mette une tabulation à la position du curseur

textarea.onkeydown = function(e){
  if (e.keyCode === 9) {
    e.preventDefault();
    insertAtCaret('\t');
  }

  if (e.keyCode === 27) {
    textarea.blur();
  }
};

function insertAtCaret(text) {
  var scrollPos = textarea.scrollTop;
  var caretPos = textarea.selectionStart;

  var front = (textarea.value).substring(0, caretPos);
  var back = (textarea.value).substring(textarea.selectionEnd, textarea.value.length);
  textarea.value = front + text + back;
  caretPos = caretPos + text.length;
  textarea.selectionStart = caretPos;
  textarea.selectionEnd = caretPos;
  textarea.focus();
  textarea.scrollTop = scrollPos;
}

// Mettre à jour le code utilisateur enregistré chaque fois que l'utilisateur
// met à jour le texte du code

  textarea.onkeyup = function(){
// nous souhaitons uniquement enregistrer l'état quand le code utilisateur est montré,
// non la solution, donc elle n'est pas enregistrée sur le code utilisateur
  if(solution.value === 'Voir la solution') {
    userEntry = textarea.value;
  } else {
    solutionEntry = textarea.value;
  }

  updateCode();
};</pre>

<p>{{ EmbedLiveSample('Apprentissage_actif_mettre_des_balises_pour_une_recette_de_cuisine', 700, 500) }}</p>

<p>Si vous êtes bloqué, vous pouvez cliquer sur le bouton <em>Voir la solution</em>, ou alors regarder l'exemple <a href="https://github.com/mdn/learning-area/blob/master/html/introduction-to-html/html-text-formatting/text-complete.html">text-complete.html</a> sur le dépôt GitHub.</p>

<h3 id="Imbriquer_des_listes">Imbriquer des listes</h3>

<p>Il est parfaitement possible d'imbriquer une liste dans une autre. Il se peut que vous vouliez insérer une liste à puces derrière une même puce de niveau supérieur. Prenons par exemple la deuxième liste de la recette :</p>

<pre class="brush: html">&lt;ol&gt;
  &lt;li&gt;Ôter la peau de l'ail et le hacher grossièrement.&lt;/li&gt;
  &lt;li&gt;Enlever les graines et la tige du poivron, le hacher grossièrement.&lt;/li&gt;
  &lt;li&gt;Mettre tous les ingrédients dans un robot mixer jusqu'à l'obtention d'une pâte.&lt;/li&gt;
  &lt;li&gt;Si vous voulez un houmous grenu, ne le mixez pas trop longtemps.&lt;/li&gt;
  &lt;li&gt;Si vous voulez un houmous lisse, mixez-le plus longtemps.&lt;/li&gt;
&lt;/ol&gt;
</pre>

<p>Comme les deux dernières puces de la liste sont très liées à celle qui les précède (elles semblent être des sous-instructions ou des choix correspondant à cette puce), il peut être judicieux de les regrouper dans une même liste non-ordonnée, et placer cette liste dans le quatrième item. Cela ressemblerait alors à ceci :</p>

<pre class="brush: html">&lt;ol&gt;
  &lt;li&gt;Ôter la peau de l'ail et le hacher grossièrement.&lt;/li&gt;
  &lt;li&gt;Enlever les graines et la tige du poivron, le hacher grossièrement.&lt;/li&gt;
  &lt;li&gt;Mettre tous les ingrédients dans un robot mixer jusqu'à l'obtention d'une pâte.
    &lt;ul&gt;
      &lt;li&gt;Si vous voulez un houmous grenu, ne le mixez pas trop longtemps.&lt;/li&gt;
      &lt;li&gt;Si vous voulez un houmous lisse, mixez-le plus longtemps.&lt;/li&gt;
    &lt;/ul&gt;
  &lt;/li&gt;
&lt;/ol&gt;
</pre>

<p>N'hésitez pas à revenir au dernier apprentissage actif pour modifier vous même la liste correspondante dans la recette.</p>

<h2 id="Soulignement_et_importance">Soulignement et importance</h2>

<p>Dans le langage, nous mettons souvent l'accent sur certains mots pour modifier le sens d'une phrase et pour marquer certains mots comme étant importants ou différents d'une manière ou d'une autre. HTML fournit divers éléments de sémantique pour nous permettre de marquer un contenu textuel avec de tels effets. Dans cette section, nous examinerons quelques-uns des plus courants.</p>

<h3 id="Emphase">Emphase</h3>

<p>Dans le langage parlé, pour accentuer, nous insistons sur certains mots, modifiant subtilement le sens de ce que nous disons. De même, dans le langage écrit, nous avons tendance à mettre un certain accent sur des mots en les écrivant en italique. Par exemple, les deux phrases suivantes ont des significations différentes.</p>

<p>« Je suis content que vous n'ayez pas été en retard. »</p>

<p>« Je suis <em>content</em> que vous n'ayez pas été <em>en retard</em>. »</p>

<p>La première phrase semble indiquer que le locuteur est vraiment soulagé que la personne n'aie pas été en retard. En revanche, la seconde a une tonalité sarcastique ou passive-agressive, exprimant la gêne que la personne soit arrivée un peu en retard.</p>

<p>En HTML, nous utilisons l'élément {{htmlelement("em")}} (<strong>em</strong>phase) pour marquer ces circonstances. Outre rendre le document plus intéressant à lire, ces marqueurs sont reconnus par les lecteurs d'écran et exprimés sur un ton de voix différent. Les navigateurs utilisent l'italique par défaut, mais il ne faut pas utiliser cette balise pour mettre en italique. Pour cela, utilisez un élément {{htmlelement("span")}} et du CSS, ou plus simplement un élément {{htmlelement("i")}} (voir ci-dessous).</p>

<pre class="brush: html">&lt;p&gt;Je suis &lt;em&gt;content&lt;/em&gt; que vous n'ayez pas été &lt;em&gt;en retard&lt;/em&gt;.&lt;/p&gt;</pre>

<h3 id="Grande_importance">Grande importance</h3>

<p>Pour mettre l'accent sur des mots très importants, nous les soulignons d'un ton particulier dans la langue parlée et nous les mettons en caractères gras dans la langue écrite. Par exemple :</p>

<p>Ce liquide est <strong>hautement toxique</strong>.</p>

<p>Je compte sur vous. <strong>Ne soyez pas en retard</strong> !</p>

<p>En HTML, nous utilisons l'élément {{htmlelement("strong")}} (forte importance) comme balise de telles circonstances. En plus de rendre le document plus lisible, ces balises sont reconnues par les lecteurs d'écran et énoncées avec des intonations différentes. Par défaut, les navigateurs mettent le texte marqué en gras, mais il ne faut pas utiliser cette balise pour mettre en gras. Pour cela, utilisez un élément {{htmlelement("span")}}} et du CSS, ou plus simplement un élément {{htmlelement("b")}} (voir ci-dessous).</p>

<pre class="brush: html">&lt;p&gt;Ce liquide est &lt;strong&gt;hautement toxique&lt;/strong&gt;.&lt;/p&gt;

&lt;p&gt;Je compte sur vous. &lt;strong&gt;Ne soyez pas en retard&lt;/strong&gt; !&lt;/p&gt;</pre>

<p>Il est possible d'imbriquer <code>strong</code> et <code>em</code> :</p>

<pre class="brush: html">&lt;p&gt;Ce liquide est &lt;strong&gt;hautement toxique&lt;/strong&gt; —
si vous en buvez, &lt;strong&gt;vous pourriez en &lt;em&gt;mourir&lt;/em&gt;&lt;/strong&gt;.&lt;/p&gt;</pre>

<h3 id="Apprentissage_actif_soulignez_l'important">Apprentissage actif : soulignez l'important</h3>

<p>Dans ce paragraphe d'apprentissage actif, nous avons donné un exemple modifiable. À l'intérieur, nous aimerions que vous essayiez d'ajouter de l'emphase et de l'importance aux mots quand vous pensez qu'ils en ont besoin, juste pour une bonne pratique.</p>

<pre class="brush: html hidden">&lt;h2&gt;Live output&lt;/h2&gt;

&lt;div class="output" style="min-height: 50px;"&gt;
&lt;/div&gt;

&lt;h2&gt;Code modifiable&lt;/h2&gt;
&lt;p class="a11y-label"&gt;Pressez Esc pour sortir le focus de la zone de code (Tab insére une tabulation).&lt;/p&gt;

&lt;textarea id="code" class="input" style="min-height: 200px; width: 95%"&gt;&lt;h1&gt;Avis important&lt;/h1&gt;
&lt;p&gt;Le dimanche 9 janvier 2010, une bande de barbares
   a été repérée en train de voler plusieurs nains
   de jardin dans un centre commercial du centre-ville
   de Milwaukee. Ils portaient tous des combinaisons
   vertes et des chapeaux ridicules, et semblaient
   s'amuser comme des fous. Si quelqu'un a une quelconque information
  sur cet incident, veuillez contacter la police immédiatement.&lt;/p&gt;&lt;/textarea&gt;

&lt;div class="playable-buttons"&gt;
  &lt;input id="reset" type="button" value="Réinitialiser"&gt;
  &lt;input id="solution" type="button" value="Voir la solution"&gt;
&lt;/div&gt;</pre>

<pre class="brush: css hidden">html {
  font-family: sans-serif;
}

h2 {
  font-size: 16px;
}

.a11y-label {
  margin: 0;
  text-align: right;
  font-size: 0.7rem;
  width: 98%;
}

body {
  margin: 10px;
  background: #f5f9fa;
}</pre>


<pre class="brush: js hidden">var textarea = document.getElementById('code');
var reset = document.getElementById('reset');
var solution = document.getElementById('solution');
var output = document.querySelector('.output');
var code = textarea.value;
var userEntry = textarea.value;

function updateCode() {
  output.innerHTML = textarea.value;
}

reset.addEventListener('click', function() {
  textarea.value = code;
  userEntry = textarea.value;
  solutionEntry = htmlSolution;
  solution.value = 'Voir la solution';
  updateCode();
});

solution.addEventListener('click', function() {
  if(solution.value === 'Voir la solution') {
    textarea.value = solutionEntry;
    solution.value = 'Cacher la solution';
  } else {
    textarea.value = userEntry;
    solution.value = 'Voir la solution';
  }
  updateCode();
});

var htmlSolution = "&lt;h1&gt;Avis important&lt;/h1&gt;\n&lt;p&gt;Le &lt;strong&gt;dimanche 9 janvier 2010&lt;/strong&gt;, une bande de &lt;em&gt;barbares&lt;/em&gt; a été repérée en train de voler &lt;strong&gt;&lt;em&gt;plusieurs&lt;/em&gt; nains de jardin&lt;/strong&gt; dans un centre commercial du centre-ville de &lt;strong&gt;Milwaukee&lt;/strong&gt;. Ils portaient tous &lt;em&gt;des combinaisons vertes&lt;/em&gt; et des &lt;em&gt;chapeaux ridicules&lt;/em&gt; et semblaient s'amuser comme des fous. Si quelqu'un a une &lt;strong&gt;quelconque&lt;/strong&gt; information sur cet incident, veuillez contacter la police &lt;strong&gt;immédiatement&lt;/strong&gt;.&lt;/p&gt;";
var solutionEntry = htmlSolution;

textarea.addEventListener('input', updateCode);
window.addEventListener('load', updateCode);

// bloquer le déplacement du focus hors de la zone texte avec la touche Tab
// faire en sorte que la touche Tab mette une tabulation à la position du curseur
textarea.onkeydown = function(e){
  if (e.keyCode === 9) {
    e.preventDefault();
    insertAtCaret('\t');
  }

  if (e.keyCode === 27) {
    textarea.blur();
  }
};

function insertAtCaret(text) {
  var scrollPos = textarea.scrollTop;
  var caretPos = textarea.selectionStart;

  var front = (textarea.value).substring(0, caretPos);
  var back = (textarea.value).substring(textarea.selectionEnd, textarea.value.length);
  textarea.value = front + text + back;
  caretPos = caretPos + text.length;
  textarea.selectionStart = caretPos;
  textarea.selectionEnd = caretPos;
  textarea.focus();
  textarea.scrollTop = scrollPos;
}

  // Mettre à jour le code utilisateur enregistré chaque fois que l'utilisateur
  // met à jour le texte du code
textarea.onkeyup = function(){
  // nous souhaitons uniquement enregistrer l'état quand le code utilisateur est montré,
  // non la solution, donc elle n'est pas enregistrée sur le code utilisateur

  if(solution.value === 'Voir la solution') {
    userEntry = textarea.value;
  } else {
    solutionEntry = textarea.value;
  }

  updateCode();
};</pre>

<p>{{ EmbedLiveSample("Apprentissage_actif_soulignez_l'important", 700, 500) }}</p>

<h3 id="Italique_gras_soulignement…">Italique, gras, soulignement…</h3>

<p>Les éléments dont nous avons discuté jusqu'à présent ont une sémantique bien définie. La situation avec {{htmlelement("b")}}, {{htmlelement("i")}} et {{htmlelement("u")}} est un peu plus complexe. Ils sont apparus pour que les personnes puissent écrire du texte en gras, en italique ou souligné à une époque où le CSS était encore mal ou pas du tout pris en charge. De tels éléments, qui n'affectent que la présentation et non la sémantique, sont appelés <strong>éléments de présentation</strong> et ne devraient plus être utilisés, car comme nous l'avons vu précédemment, la sémantique a la plus grande importance pour l'accessibilité, le référencement, etc.</p>

<p>HTML5 a redéfini <code>&lt;b&gt;</code>, <code>&lt;i&gt;</code> et <code>&lt;u&gt;</code> avec de nouveaux rôles sémantiques quelques peu déroutants.</p>

<p>Voici la meilleure règle d'or : il est probablement approprié d'utiliser <code>&lt;b&gt;</code>, <code>&lt;i&gt;</code>, ou <code>&lt;u&gt;</code> pour communiquer le sens traditionnellement associé aux caractères gras, italiques ou soulignés, à condition qu'il n'y ait pas d'élément plus approprié. Toutefois, il demeure toujours essentiel de garder présent à l'esprit le concept d'accessibilité. L'écriture en italique n'est pas très utile aux personnes utilisant des lecteurs d'écran ou un système d'écriture autre que l'alphabet latin.</p>

<ul>
 <li>{{HTMLElement('i')}} s'utilise pour transmettre un sens traditionnellement véhiculé avec l'italique : des mots étrangers, une désignation taxonomique, des termes techniques, une pensée…</li>
 <li>{{HTMLElement('b')}} s'utilise pour transmettre un sens traditionnellement véhiculé avec les caractères en gras : des mots‑clés, des noms de produits, une phrase liminaire…</li>
 <li>{{HTMLElement('u')}} s'utilise pour transmettre un sens traditionnellement véhiculé avec le soulignement : noms propres, mauvaise orthographe...</li>
</ul>

<div class="note">
<p><strong>Note :</strong> Un petit avertissement à propos du soulignement : <strong>les gens associent fortement soulignement et hyperliens</strong>. Par conséquent, sur le Web, il est préférable de ne souligner que les liens. N'utilisez l'élément <code>&lt;u&gt;</code> que s'il est sémantiquement approprié, mais envisagez d'utiliser les CSS pour remplacer le soulignement par défaut par quelque chose de plus approprié sur le Web. L'exemple ci-dessous illustre comment cela peut être fait.</p>
</div>

<pre class="brush: html">&lt;!-- noms scientifiques --&gt;
&lt;p&gt;
  Le colibri à gorge rouge (&lt;i&gt;Archilochus colubris&lt;/i&gt;)
  est le colibri le plus courant dans l'ouest de l'Amérique du Nord.
&lt;/p&gt;

&lt;!-- mots dans une langue étrangère --&gt;
&lt;p&gt;
  Le menu était un océan de mots exotiques comme &lt;i lang="uk-latn"&gt;vatrushka&lt;/i&gt;,
  &lt;i lang="id"&gt;nasi goreng&lt;/i&gt; et &lt;i lang="en"&gt;porridge&lt;/i&gt;.
&lt;/p&gt;

&lt;!-- une faute d'orthographe connue --&gt;
&lt;p&gt;
  Un jour, j'apprendrai comment mieux &lt;u style="text-decoration-line: underline; text-decoration-style: wavy;"&gt;épeler&lt;/u&gt;.
&lt;/p&gt;

&lt;!-- Mettre en évidence les mots‑clés dans un ensemble d'instructions --&gt;
&lt;ol&gt;
  &lt;li&gt;
    &lt;b&gt;Trancher&lt;/b&gt; deux morceaux de pain dans la miche.
  &lt;/li&gt;
  &lt;li&gt;
    &lt;b&gt;Mettre&lt;/b&gt; une rondelle de tomate et une feuille de laitue
    entre les deux tranches de pain.
  &lt;/li&gt;
&lt;/ol&gt;</pre>

<h2 id="Résumé">Résumé</h2>

<p>C'est tout pour l'instant ! Cet article doit vous avoir donné une bonne idée de la façon de commencer à baliser le texte en HTML et présenté les éléments les plus importants dans ce domaine. Il existe énormément d'autres éléments sémantiques à connaître dans ce domaine ; nous en verrons beaucoup plus dans notre article « More Semantic Elements », plus loin dans ce cours. Dans le prochain article, nous examinerons en détail comment <a href="/fr/docs/Learn/HTML/Introduction_to_HTML/Creating_hyperlinks">créer des hyperliens</a>, qui est peut-être l'élément le plus important sur le Web.</p>

<p>{{PreviousMenuNext("Learn/HTML/Introduction_to_HTML/The_head_metadata_in_HTML", "Learn/HTML/Introduction_to_HTML/Creating_hyperlinks", "Learn/HTML/Introduction_to_HTML")}}</p>

<h2 id="Dans_ce_module">Dans ce module</h2>

<ul>
 <li><a href="/fr/docs/Learn/HTML/Introduction_to_HTML/Getting_started">Commencer avec le HTML</a></li>
 <li><a href="/fr/docs/Learn/HTML/Introduction_to_HTML/The_head_metadata_in_HTML">Qu'y-a-t-il dans l'en-tête ? Métadonnées en HTML</a></li>
 <li>Fondamentaux du texte HTML</li>
 <li><a href="/fr/docs/Learn/HTML/Introduction_to_HTML/Creating_hyperlinks">Creation d'hyperliens</a></li>
 <li><a href="/fr/docs/Learn/HTML/Introduction_to_HTML/Advanced_text_formatting">Formatage avancé du texte</a></li>
 <li><a href="/fr/docs/Learn/HTML/Introduction_to_HTML/Document_and_website_structure">Structure de Site Web et de document</a></li>
 <li><a href="/fr/docs/Learn/HTML/Introduction_to_HTML/Debugging_HTML">Déboguer de l'HTML</a></li>
 <li><a href="/fr/docs/Learn/HTML/Introduction_to_HTML/Marking_up_a_letter">Faire une Lettre</a></li>
 <li><a href="/fr/docs/Learn/HTML/Introduction_to_HTML/Structuring_a_page_of_content">Structurer une page de contenu</a></li>
</ul>