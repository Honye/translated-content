---
title: Méthodes de mises en page traditionnelles
slug: Learn/CSS/CSS_layout/Legacy_Layout_Methods
tags:
  - Apprendre
  - Boîtes flottantes
  - CSS
  - Disposition
  - Débutant
  - Guide
  - Héritage
  - systèmes de trames
translation_of: Learn/CSS/CSS_layout/Legacy_Layout_Methods
original_slug: Apprendre/CSS/CSS_layout/Legacy_Layout_Methods
---
<div>{{LearnSidebar}}</div>

<p>{{PreviousMenuNext("Learn/CSS/CSS_layout/Multiple-Column_Layout", "Learn/CSS/CSS_layout/Supporting_Older_Browsers", "Learn/CSS/CSS_layout")}}</p>

<p>Les systèmes de trames sont courants dans les mises en page avec une CSS, mais avant la création de l'application « CSS Grid Layout », ces mises en page  étaient mises en œuvre à l'aide de boîtes flottantes ou autres. Vous imaginiez votre mise en page sous la forme d'un nombre fixe de colonnes (par exemple 4, 6 ou 12), puis insériez des colonnes de contenu dans ces colonnes imaginaires. Dans cet article, nous allons explorer le fonctionnement de ces méthodes traditionnelles anciennes pour que vous compreniez comment elles sont utilisées si vous travaillez sur un projet ancien.</p>

<table class="standard-table">
 <tbody>
  <tr>
   <th scope="row">Prérequis:</th>
   <td>Les fondamentaux du HTML (voyez <a href="/fr/Apprendre/HTML/Introduction_à_HTML">Introduction au HTML</a>) et une idée du fonctionnement de CSS (voyez <a href="/fr/Apprendre/CSS/Introduction_à_CSS">Introduction à CSS</a> et <a href="/fr/docs/Apprendre/CSS/styliser_boites">Styles de boîtes</a>).</td>
  </tr>
  <tr>
   <th scope="row">Objectif:</th>
   <td>Comprendre les concepts fondamentaux derrière les systèmes de disposition en trame utilisés avant que CSS Grid Layout soit disponible dans les navigateurs.</td>
  </tr>
 </tbody>
</table>

<h2 id="Mise_en_page_et_systèmes_de_trames_avant_CSS_Grid_Layout">Mise en page et systèmes de trames avant CSS Grid Layout</h2>

<p>Il peut sembler surprenant pour un désigner web que les CSS n'avaient pas de système de disposition en trame intégré jusqu'à peu. Au lieu de cela, nous utilisions diverses méthodes peu performantes pour créer des designs à trames. Nous appelerons maintenant ces méthodes « méthodes héritées ».</p>

<p>Pour les nouveaux projets, dans la plupart des cas, CSS Grid Layout forme la base de toute mise en page en combinaison avec une ou plusieurs autres méthodes modernes. Vous rencontrerez cependant de temps en temps des « systèmes de trame » utilisant ces méthodes héritées. Il est intéressant de comprendre comment elles fonctionnent et en quoi elles différent de CSS Grid Layout.</p>

<p>Cette leçon explique comment fonctionnent les systèmes et les cadres de trames se fondant sur des boîtes flottantes et Flexbox. Après avoir étudié « Grid Layout », vous serez probablement surpris de voir à quel point tout cela semble compliqué ! Ces connaissances vous seront utile si vous avez besoin de créer du code de recours pour les navigateurs qui ne prenent pas en charge les nouvelles méthodes ; de plus, elles vous permettront de travailler sur des projets existants qui utilisent ces types de systèmes.</p>

<p>Gardons présent à l'esprit, en explorant ces systèmes, qu'aucun d'entre eux ne crée réellement une trame de la même manière que CSS Grid Layout. Leur mode de fonctionnement consiste à donner une taille aux objets et à les pousser pour les aligner d'une manière figurant une trame.</p>

<h2 id="Disposition_sur_deux_colonnes">Disposition sur deux colonnes</h2>

<p>Débutons avec l'exemple le plus simple qui soit — une disposition sur deux colonnes. Vous pouvez suivre en créant un nouveau fichier <code>index.html</code> sur l'ordinateur, en le remplissant avec le <a href="https://github.com/mdn/learning-area/blob/master/html/introduction-to-html/getting-started/index.html">modèle HTML simple</a> et en y insérant le code ci-dessous aux endroits appropriés. À la fin du paragraphe, vous verrez un exemple en direct de ce à quoi devrait ressembler le code final.</p>

<p>Tout d'abord, nous avons besoin de contenu à mettre dans nos colonnes. Remplacez ce qui se trouve à l'intérieur de <code>body</code> par ceci :</p>

<pre class="brush: html">&lt;h1&gt;Exemple de disposition sur 2 colonnes&lt;/h1&gt;
&lt;div&gt;
  &lt;h2&gt;Première colonne&lt;/h2&gt;
  &lt;p&gt; Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla luctus aliquam dolor, eu lacinia lorem placerat vulputate. Duis felis orci, pulvinar id metus ut, rutrum luctus orci. Cras porttitor imperdiet nunc, at ultricies tellus laoreet sit amet. Sed auctor cursus massa at porta. Integer ligula ipsum, tristique sit amet orci vel, viverra egestas ligula. Curabitur vehicula tellus neque, ac ornare ex malesuada et. In vitae convallis lacus. Aliquam erat volutpat. Suspendisse ac imperdiet turpis. Aenean finibus sollicitudin eros pharetra congue. Duis ornare egestas augue ut luctus. Proin blandit quam nec lacus varius commodo et a urna. Ut id ornare felis, eget fermentum sapien.&lt;/p&gt;
&lt;/div&gt;

&lt;div&gt;
  &lt;h2&gt;Seconde colonne&lt;/h2&gt;
  &lt;p&gt;Nam vulputate diam nec tempor bibendum. Donec luctus augue eget malesuada ultrices. Phasellus turpis est, posuere sit amet dapibus ut, facilisis sed est. Nam id risus quis ante semper consectetur eget aliquam lorem. Vivamus tristique elit dolor, sed pretium metus suscipit vel. Mauris ultricies lectus sed lobortis finibus. Vivamus eu urna eget velit cursus viverra quis vestibulum sem. Aliquam tincidunt eget purus in interdum. Cum sociis natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus.&lt;/p&gt;
&lt;/div&gt;</pre>

<p>Chacune de ces colonnes nécessite un élément extérieur conteneur du dit contenu et manipulons‑le en bloc.. Dans notre exemple, nous avons choisi des éléments {{htmlelement("div")}}, mais vous auriez pu choisir n'importe quoi d'autre sémantiquement approprié comme un élément  {{htmlelement("article")}}, {{htmlelement("section")}} ou {{htmlelement("aside")}} ou tout autre.</p>

<p>Pour la CSS maintenant appliquons ce qui suit au HTML comme base de configuration :</p>

<pre class="brush: css">body {
  width: 90%;
  max-width: 900px;
  margin: 0 auto;
}</pre>

<p>Le corps du document prendra 90% de la largeur de fenêtre de la vue jusqu'à atteindre 900px de large ; au delà, il restera fixe à cette largeur et se centrera lui-même dans la fenêtre. Par défaut, ses enfants (les éléments {{htmlelement("h1")}}} et les deux {{htmlelement("div")}}) prenent 100% de la largeur du corps. Si nous voulons que les deux {{htmlelement("div")}} flottent l'un à côté de l'autre, nous devons fixer la somme de leur largeurs à 100% de la largeur totale de leur parent ou moins pour qu'ils puissent se placer l'un à côté de l'autre. Ajoutez ceci au bas de la CSS :</p>

<pre class="brush: css">div:nth-of-type(1) {
  width: 48%;
}

div:nth-of-type(2) {
  width: 48%;
}</pre>

<p>Ici nous faisons en sorte que chaque élément représente 48% de la largeur du parent — soit 96% au total, laissant 4% libres pour jouer le rôle de gouttière entre les deux colonnes et leur donner un peu d'air. Maintenant nous avons juste à faire flotter les deux colonnes ainsi :</p>

<pre class="brush: css">div:nth-of-type(1) {
  width: 48%;
  float: left;
}

div:nth-of-type(2) {
  width: 48%;
  float: right;
}</pre>

<p>En mettant tout ensemble, voici le résultat :</p>

<h3>Exemple complet</h3>

<pre class="brush: html hidden">&lt;h1&gt;Exemple de disposition sur 2 colonnes&lt;/h1&gt;

&lt;div&gt;
  &lt;h2&gt;Première colonne&lt;/h2&gt;
  &lt;p&gt;Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla luctus aliquam dolor, eu lacinia lorem placerat vulputate. Duis felis orci, pulvinar id metus ut, rutrum luctus orci. Cras porttitor imperdiet nunc, at ultricies tellus laoreet sit amet. Sed auctor cursus massa at porta. Integer ligula ipsum, tristique sit amet orci vel, viverra egestas ligula. Curabitur vehicula tellus neque, ac ornare ex malesuada et. In vitae convallis lacus. Aliquam erat volutpat. Suspendisse ac imperdiet turpis. Aenean finibus sollicitudin eros pharetra congue. Duis ornare egestas augue ut luctus. Proin blandit quam nec lacus varius commodo et a urna. Ut id ornare felis, eget fermentum sapien.&lt;/p&gt;
&lt;/div&gt;

&lt;div&gt;
  &lt;h2&gt;Seconde colonne&lt;/h2&gt;
  &lt;p&gt;Nam vulputate diam nec tempor bibendum. Donec luctus augue eget malesuada ultrices. Phasellus turpis est, posuere sit amet dapibus ut, facilisis sed est. Nam id risus quis ante semper consectetur eget aliquam lorem. Vivamus tristique elit dolor, sed pretium metus suscipit vel. Mauris ultricies lectus sed lobortis finibus. Vivamus eu urna eget velit cursus viverra quis vestibulum sem. Aliquam tincidunt eget purus in interdum. Cum sociis natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus.&lt;/p&gt;
&lt;/div&gt;
</pre>

<pre class="brush: css hidden">body {
  width: 90%;
  max-width: 900px;
  margin: 0 auto;
}

div:nth-of-type(1) {
  width: 48%;
  float: left;
}

div:nth-of-type(2) {
  width: 48%;
  float: right;
}
</pre>

<p>{{ EmbedLiveSample('Exemple_complet', '100%', 520) }}</p>

<p>Notez que nous avons utilisé des pourcentages pour définir les largeurs — c'est la bonne stratégie, cela crée une <strong>disposition fluide</strong>, s'ajustant à diverses tailles d'écran et gardant les mêmes proportions pour les tailles d'écran plus petites. Modifiez la taille de la fenêtre du navigateur pour voir par vous‑même. C'est un outil adapté au désign web adaptatif.</p>

<div class="note">
<p><strong>Note :</strong> Vous pouvez voir cet exemple en cours à la page <a href="http://mdn.github.io/learning-area/css/css-layout/floats/0_two-column-layout.html">0_two-column-layout.html</a> (voyez aussi son  <a href="https://github.com/mdn/learning-area/blob/master/css/css-layout/floats/0_two-column-layout.html">code source</a>).</p>
</div>

<h2 id="Ancienne_création_d'un_cadre_de_trames">Ancienne création d'un cadre de trames</h2>

<p>La plupart des anciens cadres de création de trames utilisaient le comportement de la propriété {{cssxref("float")}} pour faire flotter les colonnes les unes à côté des autres pour créer quelque chose qui ressemble à des trames. Travailler le processus de création d'une trame avec des boîtes flottantes vous en montre le fonctionnement et sert également d'introduction à certains concepts plus avancés pour construire les choses apprises dans la leçon sur le <a href="/fr/docs/Learn/CSS/CSS_layout/Floats">dégagement des boîtes flottantes</a>.</p>

<p>Le type de cadre de trames le plus facile à créer est un cadre de largeur fixe — il faut simplement déterminer la largeur totale du désign, le nombre de colonnes voulues et la largeur des gouttières et des colonnes. Si nous décidons plutôt de disposer ce design sur une trame avec des colonnes s'adaptant à la largeur de vue du navigateur, nous devrons  calculer les pourcentages de largeur des colonnes et celui des gouttières entre colonnes.</p>

<p>Dans les paragraphes suivants, nous verrons comment créer ces deux types. Nous allons faire une trame à 12 colonnes — un choix courant considéré comme adaptable à diverses situations étant donné que 12 est bien divisible par 6, 4, 3 et 2.</p>

<h3 id="Une_simple_trame_de_largeurs_fixes">Une simple trame de largeurs fixes</h3>

<p>Créons d'abord une trame à colonnes à largeur fixe.</p>

<p>Commençons par faire une copie locale du fichier exemple <a href="https://github.com/mdn/learning-area/blob/master/css/css-layout/grids/simple-grid.html">simple-grid.html</a> qui comporte le balisage suivant dans <code>body</code>.</p>

<pre class="brush: html">&lt;div class="wrapper"&gt;
  &lt;div class="row"&gt;
    &lt;div class="col"&gt;1&lt;/div&gt;
    &lt;div class="col"&gt;2&lt;/div&gt;
    &lt;div class="col"&gt;3&lt;/div&gt;
    &lt;div class="col"&gt;4&lt;/div&gt;
    &lt;div class="col"&gt;5&lt;/div&gt;
    &lt;div class="col"&gt;6&lt;/div&gt;
    &lt;div class="col"&gt;7&lt;/div&gt;
    &lt;div class="col"&gt;8&lt;/div&gt;
    &lt;div class="col"&gt;9&lt;/div&gt;
    &lt;div class="col"&gt;10&lt;/div&gt;
    &lt;div class="col"&gt;11&lt;/div&gt;
    &lt;div class="col"&gt;12&lt;/div&gt;
  &lt;/div&gt;
  &lt;div class="row"&gt;
    &lt;div class="col span1"&gt;13&lt;/div&gt;
    &lt;div class="col span6"&gt;14&lt;/div&gt;
    &lt;div class="col span3"&gt;15&lt;/div&gt;
    &lt;div class="col span2"&gt;16&lt;/div&gt;
  &lt;/div&gt;
&lt;/div&gt;</pre>

<p>Le but est d'en faire une trame de démonstration sur deux lignes à partir des 12 colonnes — la ligne haute montre la taille de colonnes prises isolément, la ligne basse montre des zones de taille différentes à partir de cette trame.</p>

<p><img alt="" src="simple-grid-finished.png"></p>

<p>À l'élément {{htmlelement("style")}}, ajoutons le code ci-après. Il donne une largeur de 980 pixels au conteneur enveloppe avec un remplissage de 20 pixels du côté droit. Cela nous laisse 960 pixels comme largeur totale pour les colonnes et les gouttières — dans ce cas, le remplissage est soustrait à la largeur totale du contenu car nous avons fixé la valeur de  {{cssxref("box-sizing")}} à <code>border-box</code> sur tous les éléments du site (voir <a href="/fr/docs/Apprendre/CSS/Styling_boxes/Box_model_recap#Modification totale du modèle de boîte">Modification totale du modèle de boîte</a> pour plus d'explications).</p>

<pre class="brush: css">* {
  box-sizing: border-box;
}

body {
  width: 980px;
  margin: 0 auto;
}

.wrapper {
  padding-right: 20px;
}</pre>

<p>Utilisez maintenant le conteneur enveloppe de chaque ligne de la trame pour dissocier et dégager chaque ligne. Ajoutez la règle suivante sous la règle précédente :</p>

<pre class="brush: css">.row {
  clear: both;
}</pre>

<p>Appliquer ce dégagement signifie que nous n'avons pas besoin de remplir totalement chaque rangée (ligne) d'éléments remplissant totalement les douze colonnes. Les lignes resteront séparées et n'interfèreront pas entre elles.</p>

<p>Les gouttières entre colonnes ont une largeur de 20 px. Ces gouttières sont faites en créant un marge du côté droit de chaque colonne ‑ y compris la première pour compenser le remplissage de 20 pixels du côté droit du conteneur. Nous avons donc 12 gouttières en tout — 12 x 20 = 240.</p>

<p>Il convient de soustraire cela de la largeur totale de 960 pixels, ce qui laisse 720 pixels pour les colonnes. En divisant par 12, nous voyons que chaque colonne aura une largeur de 60 pixels.</p>

<p>L'étape suivante consiste à créer un règle pour la classe <code>.col</code> la faisant flotter à gauche lui laissant une marge gauche de {{cssxref("margin-left")}} de 20 pixels formant la gouttière et  une largeur {{cssxref("width")}} de 60 pixels. Ajoutez la règle suivante en fin de la CSS :</p>

<pre class="brush: css">.col {
  float: left;
  margin-left: 20px;
  width: 60px;
  background: rgb(255, 150, 150);
}</pre>

<p>La ligne supérieure des colonnes unitaires est maintenant disposées en tant que trame.</p>

<div class="note">
<p><strong>Note :</strong> Nous avons aussi donné à chaque colonne une couleur légèrement rosée pour que vous puissiez voir exactement l'espace pris par chacune.</p>
</div>

<p>Les conteneurs destinés à accueillir plusieurs colonnes doivent être d'une classe spéciale pour pouvoir ajuster leurs valeurs {{cssxref("width")}} en fonction du nombre de colonnes requis (plus les gouttières intermédiaires). Nous devons créer une classe supplémentaire pour permettre aux conteneurs de s'étendre de 2 à 12 colonnes. Cette largeur est le résultat de l'addition de la largeur de toutes les colonnes plus les largeurs des gouttières dont le nombre est toujours inférieur de 1 au nombre de colonnes.</p>

<p>Ajoutez ce qui suit en bas de la CSS :</p>

<pre class="brush: css">/* Deux largeurs de colonnes (120px) plus une largeur de gouttière (20px) */
.col.span2 { width: 140px; }
/* Trois largeurs de colonnes (180px) plus deux largeurs de gouttières (40px) */
.col.span3 { width: 220px; }
/* et ainsi de suite... */
.col.span4 { width: 300px; }
.col.span5 { width: 380px; }
.col.span6 { width: 460px; }
.col.span7 { width: 540px; }
.col.span8 { width: 620px; }
.col.span9 { width: 700px; }
.col.span10 { width: 780px; }
.col.span11 { width: 860px; }
.col.span12 { width: 940px; }</pre>

<p>Une fois ces classes crées, nous pouvons disposer des colonnes de largeur différentes sur la trame. Enregistrez et chargez cette page dans le navigateur pour voir l'effet.</p>

<div class="note">
<p><strong>Note :</strong> Si vous avez du mal à faire fonctionner cet exemple, comparez‑le avec notre <a href="https://github.com/mdn/learning-area/blob/master/css/css-layout/grids/simple-grid-finished.html">version terminée</a> sur GitHub (la voir aussi <a href="http://mdn.github.io/learning-area/css/css-layout/grids/simple-grid-finished.html">en fonctionnement direct</a>).</p>
</div>

<p>Modifiez les classes de vos éléments soit en ajoutant ou retirant certains conteneurs, pour voir comment faire varier la disposition. Par exemple, vous pouvez faire en sorte que la deuxième ligne ressemble à ceci :</p>

<pre class="brush: css">&lt;div class="row"&gt;
  &lt;div class="col span8"&gt;13&lt;/div&gt;
  &lt;div class="col span4"&gt;14&lt;/div&gt;
&lt;/div&gt;</pre>

<p>Maintenant vous avez un système de trame fonctionnel. Il suffit simplement de définir les lignes et le nombre de colonnes dans chaque ligne, puis de remplir chaque conteneur avec le contenu voulu. Super !</p>

<h3 id="Creation_d'une_trame_fluide">Creation d'une trame fluide</h3>

<p>Cette trame est tout à fait correcte, mais elle a une largeur fixe. Nous souhaitons vraiment une trame souple (fluide) qui s'élargisse ou s'étrécisse avec l'espace disponible dans la fenêtre de vue du navigateur. Pour ce faire, il faut transformer les largeurs de référence de pixels en pourcentages.</p>

<p>L'équation qui transforme une largeur fixe en pourcentage est la suivante :</p>

<pre>cible / contexte = résultat</pre>

<p>Pour la largeur de la première colonne, la <strong>largeur cible</strong> est de 60 pixels et le <strong>contexte</strong> est l'enveloppe de 960 pixels. Avec la formule ci‑dessus nous calculons le pourcentage.</p>

<pre>60 / 960 = 0.0625</pre>

<p>Décalant de deux le point décimal nous obtenons un pourcentage de 6.25%. Donc, dans la CSS, nous pouvons remplacer la largeur de colonne de 60 pixels par 6.25%.</p>

<p>En faisant de même pour la largeur de la gouttière :</p>

<pre>20 / 960 = 0.02083333333</pre>

<p>Donc, remplaçons par 2.08333333% la valeur 20 pixels de {{cssxref("margin-left")}} dans la règle <code>.col</code> et de {{cssxref("padding-right")}} dans la règle <code>.wrapper</code>.</p>

<h4 id="Mise_à_jour_de_la_trame">Mise à jour de la trame</h4>

<p>Pour ce paragraphe, faites une autre copie de la page exemple précédente ou faites une copie locale du code de <a href="https://github.com/mdn/learning-area/blob/master/css/css-layout/grids/simple-grid-finished.html">simple-grid-finished.html</a> comme point de départ.</p>

<p>Mettez à jour la deuxième règle CSS (avec le sélecteur <code>.wrapper</code>) comme suit :</p>

<pre class="brush: css">body {
  width: 90%;
  max-width: 980px;
  margin: 0 auto;
}

.wrapper {
  padding-right: 2.08333333%;
}</pre>

<p>Outre la définition du pourcentage comme valeur de {{cssxref("width")}}, nous avons ajouté la propriété {{cssxref("max-width")}} de façon à plafonner une mise en page qui deviendrait trop large.</p>

<p>Ensuite, mettez à jour les quatre règles CSS (du sélecteur <code>.col</code>) ainsi :</p>

<pre class="brush: css">.col {
  float: left;
  margin-left: 2.08333333%;
  width: 6.25%;
  background: rgb(255, 150, 150);
}</pre>

<p>Maintenant vient la partie un peu plus laborieuse — nous devons mettre à jour toutes  les règles <code>.col.span</code> en utilisant des largeurs en pourcentage au lieu de pixels. Cela prend un peu de temps avec une calculette ; pour vous économiser du travail, nous l'avons fait pour vous.</p>

<p>Mettez à jour le bloc bas des règles CSS avec ce qui suit :</p>

<pre class="brush: css">/* Deux largeurs de colonnes (12.5%) plus une largeur de gouttière (2.08333333%) */
.col.span2 { width: 14.58333333%; }
/* Trois largeurs de colonnes (18.75%) plus deux largeurs de gouttière (4.1666666%) */
.col.span3 { width: 22.91666666%; }
/* Et ainsi de suite... */
.col.span4 { width: 31.24999999%; }
.col.span5 { width: 39.58333332%; }
.col.span6 { width: 47.91666665%; }
.col.span7 { width: 56.24999998%; }
.col.span8 { width: 64.58333331%; }
.col.span9 { width: 72.91666664%; }
.col.span10 { width: 81.24999997%; }
.col.span11 { width: 89.5833333%; }
.col.span12 { width: 97.91666663%; }</pre>

<p>Maintenant enregistrez le code, chargez le dans le navigateur et modifiez la largeur de vue — vous devez constater que la largeur des colonnes s'ajuste comme il convient.</p>

<div class="note">
<p><strong>Note :</strong> Si vous avez du mal à faire fonctionner l'exemple ci‑dessus, comparez‑le avec notre <a href="https://github.com/mdn/learning-area/blob/master/css/css-layout/grids/fluid-grid.html">version terminée sur GitHub</a> (voir aussi celle <a href="http://mdn.github.io/learning-area/css/css-layout/grids/fluid-grid.html">s'exécutant en direct</a>).</p>
</div>

<h3 id="Faciliter_les_calculs_avec_la_fonction_calc()">Faciliter les calculs avec la fonction calc()</h3>

<p>Vous pouvez utiliser la fonction {{cssxref("calc()")}} pour faire les calculs à l'intérieur même de la CSS — la fonction vous permet d'insérer de simples expressions mathématiques pour calculer la valeur qu'il convient de donner à la propriété CSS. C'est utile quand les calculs sont complexes ; vous pouvez même effectuer un calcul avec des unités différentes, par exemple « je veux que la hauteur de cet élément soit toujours égale à 100% de son parent moins 50px ». Voir <a href="/fr/docs/Web/API/MediaRecorder_API/Using_the_MediaRecorder_API#Keeping_the_interface_constrained_to_the_viewport_regardless_of_device_height_with_calc()">cet exemple dans le didacticiel MediaRecorder API</a>.</p>

<p>Revenon à nos trames ! Toute colonne se développant au delà de la première a une largeur totale de 6.25% multipliée par le nombre de colonnes précédentes plus 2.08333333% multiplié par le nombre de gouttières (qui doit toujours être égal au nombre de colonnes moins 1). La fonction <code>calc()</code> nous permet de faire ce calcul dans la valeur <code>width</code> même, ainsi pour tout élément au-delà de la colonne 4 nous pouvons écrire, par exemple :</p>

<pre class="brush: css">.col.span4 {
  width: calc((6.25%*4) + (2.08333333%*3));
}</pre>

<p>Remplacez le bloc de règles le plus bas par le suivant, puis actualisez le navigateur pour constater que vous obtenez un résultat identique :</p>

<pre class="brush: css">.col.span2 { width: calc((6.25%*2) + 2.08333333%); }
.col.span3 { width: calc((6.25%*3) + (2.08333333%*2)); }
.col.span4 { width: calc((6.25%*4) + (2.08333333%*3)); }
.col.span5 { width: calc((6.25%*5) + (2.08333333%*4)); }
.col.span6 { width: calc((6.25%*6) + (2.08333333%*5)); }
.col.span7 { width: calc((6.25%*7) + (2.08333333%*6)); }
.col.span8 { width: calc((6.25%*8) + (2.08333333%*7)); }
.col.span9 { width: calc((6.25%*9) + (2.08333333%*8)); }
.col.span10 { width: calc((6.25%*10) + (2.08333333%*9)); }
.col.span11 { width: calc((6.25%*11) + (2.08333333%*10)); }
.col.span12 { width: calc((6.25%*12) + (2.08333333%*11)); }</pre>

<div class="note">
<p><strong>Note :</strong> Vous pouvez voir la version terminée dans <a href="https://github.com/mdn/learning-area/blob/master/css/css-layout/grids/fluid-grid-calc.html">fluid-grid-calc.html</a> (la voir aussi  <a href="http://mdn.github.io/learning-area/css/css-layout/grids/fluid-grid-calc.html">en direct</a>).</p>
</div>

<div class="note">
<p><strong>Note :</strong> Si vous n'arrivez pas à faire fonctionner ce qui précède, cela peut être dû au fait que votre navigateur ne prend pas en charge la fonction <code>calc()</code>, même si elle est assez bien prise en charge parmi les navigateurs — au‑delà de IE9.</p>
</div>

<h3 id="Systèmes_de_trames_«_sémantiques_»_vs._«_non_sémantiques_»">Systèmes de trames « sémantiques » vs. « non sémantiques »</h3>

<p>Ajouter des classes au balisage pour définir une mise en page signifie que le contenu et le balisage sont liés à la présentation visuelle. Cette utilisation de classes CSS est parfois décrite comme étant « non sémantique » — montrant comment le contenu est disposé — par opposition à l'utilisation sémantique des classes qui décrit le contenu. C'est le cas de nos classes <code>span2</code>, <code>span3</code>, etc.</p>

<p>Ce n'est pas la seule approche. À la place, vous pouvez décider de la trame, puis ajouter les informations de taille aux règles des classes sémantiques existantes. Par exemple, si vous avez un élément {{htmlelement("div")}} de classe <code>content</code> que vous voulez développer sur huit colonnes, vous pouvez copier sur la largeur de la classe <code>span8</code>, ce qui vous donne une règle :</p>

<pre class="brush: css">.content {
  width: calc((6.25%*8) + (2.08333333%*7));
}</pre>

<div class="note">
<p><strong>Note :</strong> Si vous deviez utiliser un préprocesseur tel que <a href="http://sass-lang.com/">Sass</a>, vous pourriez créer un simple mixage pour qu'il insère cette valeur pour vous.</p>
</div>

<h3 id="Décalage_du_conteneur_d'une_trame">Décalage du conteneur d'une trame</h3>

<p>La trame créée plus haut fonctionne bien tant que tous les conteneurs sont placés à l'aplomb du côté gauche d'une colonne de trame. Si nous voulons laisser une colonne vide avant le premier conteneur — ou entre les conteneurs — nous devons créer une classe <code>offset</code> pour ajouter une marge gauche à notre site pour le décaler visuellement dans la grille. Encore des calculs !</p>

<p>Essayons.</p>

<p>Démarrons avec le code précédent ou utilisons le fichier <a href="https://github.com/mdn/learning-area/blob/master/css/css-layout/grids/fluid-grid.html">fluid-grid.html</a> comme point de départ.</p>

<p>Créons dans la CSS une classe qui décale un élément de conteneur d'une largaur de colonne. Ajoutons ce qui suit au bas de la CSS :</p>

<pre class="brush: css">.offset-by-one {
  margin-left: calc(6.25% + (2.08333333%*2));
}</pre>

<p>Ou, si vous préférez calculer le pourcentage vous-même, utilisez :</p>

<pre class="brush: css">.offset-by-one {
  margin-left: 10.41666666%;
}</pre>

<p>Vous pouvez maintenant ajouter cette classe à tout conteneur pour lequel vous voulez laisser une colonne vide sur sa gauche. Par exemple, si vous avez ceci dans votre HTML :</p>

<pre class="brush: html">&lt;div class="col span6"&gt;14&lt;/div&gt;</pre>

<p>remplacez‑le par :</p>

<pre class="brush: html">&lt;div class="col span5 offset-by-one"&gt;14&lt;/div&gt;</pre>

<div class="note">
<p><strong>Note :</strong> Notez que vous devez réduire le nombre de colonnes réparties pour faire de la place au décalage !</p>
</div>

<p>Chargez et actualisez pour voir la différence, ou bien vérifiez avec l'exemple <a href="https://github.com/mdn/learning-area/blob/master/css/css-layout/grids/fluid-grid-offset.html">fluid-grid-offset.html</a> (voir aussi <a href="http://mdn.github.io/learning-area/css/css-layout/grids/fluid-grid-offset.html">l'exécution directement</a>). L'exemple terminé doit ressembler à ceci :</p>

<p><img alt="" src="offset-grid-finished.png"></p>

<div class="note">
<p><strong>Note :</strong> Comme exercice supplémentaire, pouvez‑vous implémenter une classe <code>offset-by-two</code> ?</p>
</div>

<h3 id="Limitations_des_trames_de_boîtes_flottantes">Limitations des trames de boîtes flottantes</h3>

<p>En utilisant un tel système, vous devez veiller à ce que la somme des largeurs doit correcte et que ne soit pas inclus d'éléments dans une ligne qui s'étendent sur plus de colonnes que la rangée peut en contenir. En raison du mode de fonctionnement des boîtes flottantes, si le nombre de colonnes de la grille devient trop large pour la trame, les éléments d'extrémité descendront sur la ligne suivante et casseront la trame.</p>

<p>N'oubliez pas non plus que si le contenu des éléments s'élargit au-delà des rangées qu'ils occupent, il y aura débordement et tout sera gâché.</p>

<p>La plus grande limite de ce système est essentiellement son caractère unidimensionnel. Il s'agit de colonnes et de répartition d'éléments transversaux, mais pas de lignes. Il est très difficile avec ces anciennes méthodes de mise en page de contrôler la hauteur des éléments sans fixer explicitement une hauteur, et c'est aussi une approche très rigide — cela ne fonctionne que si vous pouvez garantir que le contenu est d'une hauteur donnée..</p>

<h2 id="Trames_Flexbox">Trames Flexbox ?</h2>

<p>Si vous avez lu le précédent article à propors de Flexbox, vous pourriez penser que Flexbox est la solution idéale pour créer un système de trames. Il existe actuellement nombre de systèmes de grille fondés sur Flexbox et Flexbox peut résoudre beaucoup de problèmes mis en évidence lors de la création de notre trame ci-dessus.</p>

<p>Cependant, Flexbox n'a jamais été conçu comme système de trames : il conduit à un nouvel ensemble de défis lorsqu'il est utilisé comme tel. Comme simple exemple, prenons le même exemple que celui utilisé ci-dessus et utilisons la CSS suivante pour mettre en page les classes <code>wrapper</code>, <code>row</code> et <code>col</code> :</p>

<pre class="brush: css">body {
  width: 90%;
  max-width: 980px;
  margin: 0 auto;
}

.wrapper {
  padding-right: 2.08333333%;
}


.row {
  display: flex;
}

.col {
  margin-left: 2.08333333%;
  margin-bottom: 1em;
  width: 6.25%;
  flex: 1 1 auto;
  background: rgb(255,150,150);
}</pre>

<p>Faites ces remplacements dans votre exemple, ou regardez l'exemeple de code <a href="https://github.com/mdn/learning-area/blob/master/css/css-layout/grids/flexbox-grid.html">flexbox-grid.html</a> (voir aussi en  <a href="http://mdn.github.io/learning-area/css/css-layout/grids/flexbox-grid.html">exécution directe</a>).</p>

<p>Ici, nous transformons chaque rangée en conteneur flexible. Avec une trame fondée sur Flexbox, nous avons encore besoin de rangées  pour avoir des éléments tant que leur somme est inférieure à 100%. Nous avons réglé ce conteneur à <code>display : flex</code>.</p>

<p>Pour <code>.col</code> nous fixons à 1 la première valeur ({{cssxref("flex-grow")}}) de la propriété  {{cssxref("flex")}}, ainsi nos éléments peuvent s'élargir, la deuxième valeur ({{cssxref("flex-shrink")}}) à 1 également, ainsi les éléments peuvent s'étrécir, et la troisième valeur ({{cssxref("flex-basis")}}) à <code>auto</code>. Comme la valeur {{cssxref("width")}} de l'élément est fixée, <code>auto</code> utilisera cette valeur en tant que valeur de <code>flex-basis</code>.</p>

<p>Sur la ligne haute, nous disposons de douze boîtes nettes sur la trame et elle s'élargissent ou s'étrécissent de manière égale quand nous modifions la largeur de la vue. Sur la ligne suivante, toutefois, nous n'avons que quatre éléments et ceux-ci s'élargissent ou s'étrécissent à partir de la base de 60px. Avec seulement quatre d'entre eux ils peuvent s'élargir un peu plus que les éléments de la ligne au‑dessus, le résultat étant qu'ils occupent tous la même largeur sur la deuxième ligne.</p>

<p><img alt="" src="flexbox-grid-incomplete.png"></p>

<p>Pour corriger cela, nous avons encore besoin d'inclure les classes <code>span</code> pour donner une largeur qui remplave la valeur donnée par <code>flex-basis</code> pour cet élément.</p>

<p>Également, ils ne respectent pas la trame utilisée par les éléments au‑dessus car ils ne « savent » rien à son propos.</p>

<p>Flexbox est un design <strong>mono-dimensionnel</strong> par conception. Il compose avec une seule dimentsion, celle d'une ligne ou d'une colonne. Nous ne pouvons pas créer une trame stricte pour les colonnes <strong>et</strong> pour les lignes, ce qui signifie que si nous utilisons Flexbox pour  une trame, nous devons encore calculer les pourcentages comme pour la disposition en boîtes flottantes.</p>

<p>Dans votre projet, vous pouvez toujours choisir d'utiliser une « trame » Flexbox en raison des capacités d'alignement et de distribution de l'espace supplémentaires que Flexbox offre pour les boites flottantes. Mais sachez que vous utilisez encore un outil pour autre chose que ce pour quoi il a été conçu. Vous pouvez donc avoir l'impression d'être obligé de passer par un tas de circonvolutions pour obtenir le résultat final souhaité.</p>

<h2 id="Systèmes_de_trame_tierces_parties">Systèmes de trame tierces parties</h2>

<p>Maintenant que nous avons compris la mathématique derrière les calculs de grille, nous sommes au bon endroit pour examiner certains des systèmes de trame tierces parties couramment utilisés. Si vous faite une recherche web pour « CSS Grid framework », vous vous trouverez devant une liste de choix énorme. Les canevas populaires tels que <a href="http://getbootstrap.com/">Bootstrap</a> et <a href="http://foundation.zurb.com/">Foundation</a> incluent un système de trame. Il existe également des systèmes de trames autonomes, développés soit à l'aide des CSS, soit à l'aide de préprocesseurs.</p>

<p>Voyons un de ces systèmes autonomes : il montre les techniques courantes pour travailler dans un cadre de trames. La trame que nous allons utiliser fait partie de Skeleton, un simple canevas CSS.</p>

<p>Commençons par visiter le <a href="http://getskeleton.com/">site web de Skeleton</a> et choisissons « Download » pour télécharger le fichier ZIP. Faisons l'extraction et copions les fichiers <em>skeleton.css</em> et <em>normalize.css</em> dans un nouveau répertoire.</p>

<p>Faites une copie de <a href="https://github.com/mdn/learning-area/blob/master/css/css-layout/grids/html-skeleton.html">html-skeleton.html</a> et enregistrez le dans le même répertoire que <em>skeleton.css</em> et <em>normalize.css</em>.</p>

<p>Incorporez les .css <em>skeleton</em> et <em>normalize</em> dans la page HTML, en ajoutant ce qui suit dans <code>head</code> :</p>

<pre class="brush: html">&lt;link href="normalize.css" rel="stylesheet"&gt;
&lt;link href="skeleton.css" rel="stylesheet"&gt;</pre>

<p>Skeleton inclut plus qu'un système de grille — il contient aussi des CSS pour la typographie et autres éléments de page que vous pouvez utiliser comme point de départ. Toutefois nous les laisserons de côté pour l'instant — c'est la trame qui nous interesse pour le moment.</p>

<div class="note">
<p><strong>Note :</strong> <a href="/fr/docs/">Normalize</a> est une petite bibliothèque réellement utile écrite par Nicolas Gallagher, bibliothèque qui fait automatiquement quelques corrections sur les dispositions de base et rend le style des éléments par défaut plus conhérent entre les divers navigateurs.</p>
</div>

<p>Nous utiliserons un HTML similaire à celui de notre dernier exemple. Ajoutez ce qui suit dans le corps du HTML :</p>

<pre class="brush: html">&lt;div class="container"&gt;
  &lt;div class="row"&gt;
    &lt;div class="col"&gt;1&lt;/div&gt;
    &lt;div class="col"&gt;2&lt;/div&gt;
    &lt;div class="col"&gt;3&lt;/div&gt;
    &lt;div class="col"&gt;4&lt;/div&gt;
    &lt;div class="col"&gt;5&lt;/div&gt;
    &lt;div class="col"&gt;6&lt;/div&gt;
    &lt;div class="col"&gt;7&lt;/div&gt;
    &lt;div class="col"&gt;8&lt;/div&gt;
    &lt;div class="col"&gt;9&lt;/div&gt;
    &lt;div class="col"&gt;10&lt;/div&gt;
    &lt;div class="col"&gt;11&lt;/div&gt;
    &lt;div class="col"&gt;12&lt;/div&gt;
  &lt;/div&gt;
  &lt;div class="row"&gt;
    &lt;div class="col"&gt;13&lt;/div&gt;
    &lt;div class="col"&gt;14&lt;/div&gt;
    &lt;div class="col"&gt;15&lt;/div&gt;
    &lt;div class="col"&gt;16&lt;/div&gt;
  &lt;/div&gt;
&lt;/div&gt;</pre>

<p>Pour commencer à utiliser Skeleton nous devons donner à l'élément enveloppe {{htmlelement("div")}} une classe <code>container</code> — elle est déjà comprise dans le HTML. Ceci centre le contenu avec une largeur maximale de 960 pixels. Vous pouvez voir que les boîtes ne deviennent plus jamais plus large que 960 pixels.</p>

<p>Regardez dans le fichier skeleton.css, vous verrez la  CSS appliquée quand on se sert de cette classe. L'élément <code>&lt;div&gt;</code> est centré en utilisant la valeur <code>auto</code> pour les marges droite et gauche ; de plus, un remplissage de 20 pixels est appliqué à droite et à gauche. Skeleton fixe également la propriété {{cssxref("box-sizing")}} à la valeur <code>border-box</code> comme nous l'avions fait plu tôt et donc le remplissage et l'encadrement de cet élément seront inclus dans la largeur totale.</p>

<pre class="brush: css">.container {
  position: relative;
  width: 100%;
  max-width: 960px;
  margin: 0 auto;
  padding: 0 20px;
  box-sizing: border-box;
}</pre>

<p>Les éléments ne peuvent faire partie d'une trame que s'ils sont à l'intérieur d'une ligne, donc avec notre exemple précédent nous aurons besoin d'un <code>&lt;div&gt;</code> supplémentaire ou d'un autre élément de la classe <code>row</code> imbriqué entre le <code>&lt;div&gt;</code> de <code>content </code>et les véritables conteneurs <code>&lt;div&gt; </code>de contenu. Nous avons aussi déjà fait cela.</p>

<p>Disposons maintenant les boîtes conteneur. Skeleton est fondé sur une trame de 12 colonnes. Les boîtes de la ligne supérieure nécessitent toutes des classes <code>one column</code> pour qu'elles se répartissent à raison de une par colonne.</p>

<p>Ajoutez maintenant cet extrait de lignes de code :</p>

<pre class="brush: html">&lt;div class="container"&gt;
  &lt;div class="row"&gt;
    &lt;div class="one column"&gt;1&lt;/div&gt;
    &lt;div class="one column"&gt;2&lt;/div&gt;
    &lt;div class="one column"&gt;3&lt;/div&gt;
    /* and so on */
  &lt;/div&gt;
&lt;/div&gt;</pre>

<p>Ensuite, indiquez les conteneurs sur la deuxième ligne en précisant le nombre de colonnes qu'ils englobent , ainsi :</p>

<pre class="brush: html">&lt;div class="row"&gt;
  &lt;div class="one column"&gt;13&lt;/div&gt;
  &lt;div class="six columns"&gt;14&lt;/div&gt;
  &lt;div class="three columns"&gt;15&lt;/div&gt;
  &lt;div class="two columns"&gt;16&lt;/div&gt;
&lt;/div&gt;</pre>

<p>Enregistrez le fichier HTML et chargez‑le dans le navigateur pour voir ce que cela donne.</p>

<div class="note">
<p><strong>Note :</strong> Si vous éprouvez des difficulatés à faire fonctionner cet exemple, comparez votre code avec le fichier <a href="https://github.com/mdn/learning-area/blob/master/css/css-layout/grids/html-skeleton-finished.html">html-skeleton-finished.html</a> (à voir aussi  <a href="http://mdn.github.io/learning-area/css/css-layout/grids/html-skeleton-finished.html">en exécution directe</a>).</p>
</div>

<p>Si vous regardez dans le fichier <em>skeleton.css</em> vous verrez comment cela fonctionne. Par exemple, Skeleton prédéfinit ce qui suit pour styler des éléments de la classe « three columns » que l'on ajouterait.</p>

<pre class="brush: css">.three.columns { width: 22%; }</pre>

<p>Tout Skeleton (ou n'importe quel autre canevas) paramètre des classes prédéfinies qu'il est possible d'utiliser en les ajoutant à votre balisage. Vous avez fait exactement la même chose en calculant ces pourcentages vous même.</p>

<p>Comme vous le voyez, vous n'avez besoin d'écrire que peu de CSS en utilisant Skeleton. Il traite tout l'aspect boîte flottante pour vous quand vous ajoutez des classes à votre balisage. C'est la possibilité de gérer la responsabilité de la disposition sur quelque chose d'autre qui fait que l'utilisation d'un canevas pour un système de trames est un choix convaincan ! Toutefois, actuellement avec « CSS Grid Layout », nombre de développeurs délaissent ces canevas pour l'utilisation des trames natives intégrées que les CSS fournissent.</p>

<h2 id="Résumé">Résumé</h2>

<p>Vous savez maintenant comment les divers systèmes de trames sont créés. La connaissance de ces processus est utile dans le cadre d'un travail sur des sites anciens, ainsi que pour la compréhension des différences  entre les trames natives de « CSS Grid Layout » et celles des anciens systèmes.</p>

<p>{{PreviousMenuNext("Learn/CSS/CSS_layout/Multiple-Column_Layout", "Learn/CSS/CSS_layout/Supporting_Older_Browsers", "Learn/CSS/CSS_layout")}}</p>

<h2 id="Dans_ce_module">Dans ce module</h2>

<ul>
 <li><a href="/fr/docs/Learn/CSS/CSS_layout/Introduction">Introduction to CSS layout</a></li>
 <li><a href="/fr/docs/Learn/CSS/CSS_layout/Normal_Flow">Normal Flow</a></li>
 <li><a href="/fr/docs/Learn/CSS/CSS_layout/Flexbox">Flexbox</a></li>
 <li><a href="/fr/docs/Learn/CSS/CSS_layout/Grids">Grid</a></li>
 <li><a href="/fr/docs/Learn/CSS/CSS_layout/Floats">Floats</a></li>
 <li><a href="/fr/docs/Learn/CSS/CSS_layout/Positioning">Positioning</a></li>
 <li><a href="/fr/docs/Learn/CSS/CSS_layout/Multiple-column_Layout">Multiple-column Layout</a></li>
 <li><a href="/fr/docs/Learn/CSS/CSS_layout/Legacy_Layout_Methods">Legacy Layout Methods</a></li>
 <li><a href="/fr/docs/Learn/CSS/CSS_layout/Supporting_Older_Browsers">Supporting older browsers</a></li>
 <li><a href="/fr/docs/Learn/CSS/CSS_layout/Fundamental_Layout_Comprehension">Fundamental Layout Comprehension Assessment</a></li>
</ul>