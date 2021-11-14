---
title: Introduction à la mise en page en CSS
slug: Learn/CSS/CSS_layout/Introduction
tags:
  - Apprendre
  - Article
  - Boîtes flexibles
  - CSS
  - Débutant
  - Flottants
  - Flux
  - Grille
  - Intro
  - Mise en page
  - Positionnement
  - Tableaux
translation_of: Learn/CSS/CSS_layout/Introduction
original_slug: Apprendre/CSS/CSS_layout/Introduction
---
<div>{{LearnSidebar}}</div>

<div>{{NextMenu("Apprendre/CSS/CSS_layout/Normal_Flow", "Apprendre/CSS/CSS_layout")}}</div>

<p>Cet article récapitule quelques fonctionnalités de mise en page CSS que l'on a déjà côtoyées dans les modules précédents — telles que les différentes valeurs de {{cssxref("display")}} — et en introduit de nouveaux que nous aborderons dans ce module.</p>

<table class="standard-table">
 <tbody>
  <tr>
   <th scope="row">Prérequis :</th>
   <td>Les fondamentaux du HTML (étudiez <a href="/fr/Apprendre/HTML/Introduction_%C3%A0_HTML">Introduction au HTML</a>) et avoir une idée de la manière dont la CSS fonctionne (étudiez <a href="/fr/Apprendre/CSS/Introduction_à_CSS">Introduction aux CSS</a>).</td>
  </tr>
  <tr>
   <th scope="row">Objectif :</th>
   <td>Vous donner un aperçu des techniques de mise en page des CSS. Chaque technique peut être apprise plus précisément dans des tutoriels dédiés.</td>
  </tr>
 </tbody>
</table>

<p>Les techniques de mise en page des CSS nous permettent de prendre des éléments contenus dans une page web et d'en contrôler le placement par rapport à leur position par défaut dans le flot d'une mise en page courante, aux autres éléments environnants, à leur conteneur parents ou à la fenêtre principale d'affichage. Les techniques de mises en page abordées en détail dans ce module sont:</p>

<ul>
 <li>le cours normal</li>
 <li>la propriété {{cssxref("display")}}</li>
 <li>Flexbox</li>
 <li>les trames</li>
 <li>les flotteurs</li>
 <li>le positionnement</li>
 <li>la mise en page des tableaux</li>
 <li>la disposition sur plusieurs colonnes</li>
</ul>

<p>Chaque technique à ses usages, ses avantages et ses inconvénients. Aucune technique n'a été conçue pour être utilisée isolément. En comprenant ce pourquoi chaque méthode a été conçue, vous saurez utiliser le meilleur outil de mise en page dans chaque situation.</p>

<h2 id="Cours_normal">Cours normal</h2>

<p>Le cours normal est la manière dont le navigateur présente les pages HTML par défaut quand vous ne faites rien pour contrôler la mise en page. Regardons rapidement un exemple HTML:</p>

<pre class="brush: html">&lt;p&gt;J'aime mon chat.&lt;/p&gt;

&lt;ul&gt;
  &lt;li&gt;Acheter des croquettes&lt;/li&gt;
  &lt;li&gt;Exercice&lt;/li&gt;
  &lt;li&gt;Haut les cœurs, ami&lt;/li&gt;
&lt;/ul&gt;

&lt;p&gt;La fin !&lt;/p&gt;</pre>

<p>Par défaut, le navigateur affichera ce code ainsi :</p>

<p>{{ EmbedLiveSample('Cours_normal', '100%', 200) }}</p>

<p>Notez que le HTML est affiché dans l'ordre exact où il est dans le code source : les éléments s'empilent les uns sur les autres — le premier paragraphe, puis la liste non ordonnée suivie par le second paragraphe.</p>

<p>Les éléments disposés en empilement sont désignés comme étant des éléments <em>blocs</em>, par opposition aux éléments <em>en ligne</em> qui apparaissent l'un après l'autre telle la succession de mots distincts d'un paragraphe.</p>

<div class="note">
<p><strong>Note :</strong> « Block Direction » (Sens d'empilement) définit le sens dans lequel les éléments blocs sont disposés. Le sens d'empilement est vertical pour une langue comme l'anglais dont le mode d'écriture est horizontal. Ce sens sera horizontal pour toute langue avec un mode d'écriture vertical, comme le japonais. La « Inline Direction » (sens d'écriture) correspond à celle dont les contenus en ligne (comme une phrase) sont disposés.</p>
</div>

<p>Lorsque vous utilisez les CSS pour faire une mise en page, vous déplacez les éléments de leur cours normal ; toutefois, pour la plupart des éléments de la page, ce cours normal crée exactement la mise en page dont vous avez besoin. C'est pourquoi il est si important de commencer avec un document HTML bien structuré, car vous pouvez alors travailler la façon dont les choses seront disposées par défaut au lieu de lutter contre cette disposition.</p>

<p>Les méthodes des CSS pouvant changer le placement des éléments sont les suivantes :</p>

<ul>
 <li><strong>La propriété {{cssxref("display")}}</strong> — les valeurs standards comme <code>block</code>, <code>inline</code> ou <code>inline-block</code> peuvent changer la manière dont l'élément se comporte dans le cours normal (voir <a href="/fr/Apprendre/CSS/Introduction_%C3%A0_CSS/Le_mod%C3%A8le_de_bo%C3%AEte#Les_types_de_bo%C3%AEte">Types de boîtes</a> pour plus d'informations). Ensuite, nous disposons de méthodes de mise en page autonomes activées par l'intermédiaire d'une valeur de <code>display</code>, par exemple les <a href="/fr/docs/Learn/CSS/CSS_layout/Grids">Grilles CSS</a> ou <a href="/fr/docs/Learn/CSS/CSS_layout/Flexbox">Flexbox</a>.</li>
 <li><strong>Flotteurs</strong> — appliquer à {{cssxref("float")}} une valeur comme <code>left</code> peut créer une juxtaposition d'un élément bloc à côté d'un autre, tout comme les images « baignent » dans le texte dans les mises en page de magazines.</li>
 <li><strong>La propriété {{cssxref("position")}}</strong> — vous permet de contrôler avec précision le placement de boîtes dans d'autres boîtes. <code>static</code> est le placement par défaut dans le cours, mais vous pouvez manipuler les éléments pour qu'ils se comportent différemment à l'aide d'autres valeurs, par exemple en les fixant en haut à gauche de la fenêtre d'affichage du navigateur.</li>
 <li><strong>Mise en page de tableaux</strong> — les fonctions conçues pour styliser les parties d'un tableau HTML peuvent être utilisées sur des éléments non tableau en utilisant <code>display: table</code> et les propriétés associées.</li>
 <li><strong>Mise en page sur plusieurs colonnes</strong> — Les propriétés <a href="/fr/docs/Web/CSS/CSS_Columns">Multi-column</a> peuvent faire qu'un contenu bloc soit disposé en colonnes, comme dans un journal.</li>
</ul>

<h2 id="La_propriété_«_display_»">La propriété « display »</h2>

<p>Les principales modalités de mise en page avec les CSS relèvent toutes des valeurs de la propriété <code>display</code>. Cette propriété permet de modifier l'affichage par défaut des éléments. Chaque chose dans le cours normal a une valeur de propriété <code>display</code>. Les éléments se règlent sur cette valeur pour définir leur comportement par défaut. Par exemple, le fait que des paragraphes en langue anglaise se placent les uns au dessus des autres provient du fait que leur style est <code>display: block</code>. Si vous créez un lien sur un texte à l'intérieur d'un paragraphe, ce lien reste aligné avec le reste du texte et ne s'affiche pas sur une nouvelle ligne. C'est parce que l'élément {{htmlelement("a")}} est <code>display: inline</code> par défaut.</p>

<p>Vous pouvez modifier le comportement d'affichage par défaut. Par exemple, l'élément {{htmlelement("li")}} est <code>display: block</code> par défaut, ce qui signifie que les éléments de la liste s'afficheront l'un sous l'autre dans un document en anglais. Si nous changeons la valeur de <code>display</code> pour <code>inline</code>, ils s'afficheront alors les uns à côté des autres, comme les mots dans une phrase. Le fait que vous puissiez changer la valeur d'affichage de n'importe quel élément signifie que vous pouvez choisir des éléments HTML pour leur signification sémantique, sans vous soucier de leur apparence. Leur apparence est quelque chose que vous pouvez modifier.</p>

<p>En plus de pouvoir changer la présentation par défaut en faisant passer un élément de <code>block</code> à <code>inline</code> et vice versa, il existe des méthodes de mise en page accrues commençant avec une valeur particulière de <code>display</code>. Cependant, si vous les utilisez, vous devrez généralement invoquer des propriétés supplémentaires. Les deux valeurs les plus importantes pour notre discussion sur la mise en page sont <code>display: flex</code> et <code>display: grid</code>.</p>

<h2 id="Flexbox">Flexbox</h2>

<p>Flexbox est l'abréviation pour <a href="/fr/docs/Web/CSS/CSS_Flexible_Box_Layout">Flexible Box Layout</a> Module (Mise en page de boîtes modulaires), conçu pour faciliter une disposition alignée sur une dimension — soit en ligne, soit en colonne. Pour utiliser <code>flexbox</code>, appliquez <code>display: flex</code> à l'élément parent des éléments à placer ; tous ses enfants directs deviennent alors des éléments <code>flex</code>. Voyons cela avec un simple exemple.</p>

<p>Le balisage HTML ci-dessous crée un élément conteneur de la classe <code>wrapper</code>, dans lequel nous plaçons 3 éléments {{htmlelement("div")}}. Par défaut ces éléments s'afficheront en tant qu'éléments blocs, les uns sous les autres, dans ce document en langue française.</p>

<h3>Utiliser display: flex</h3>

<p>Mais nous ajoutons <code>display: flex</code> sur le parent ; les trois éléments se placent maintenant côte à côte. Cela provient du fait qu'ils sont devenus des <em>éléments flex</em> et qu'ils utilisent les valeurs initiales données par flexbox. Ils sont disposés alignés, car la valeur initiale de {{cssxref("flex-direction")}} est <code>row</code>. Ils apparaissent serrés au haut de l'élément le plus haut, car la valeur initiale de la propriété {{cssxref("align-items")}} est <code>stretch</code>. Ce qui signifie que les éléments se casent dans la hauteur du conteneur <code>flex</code> défini dans ce cas par l'élément le plus grand. Les éléments s'alignent à partir de l'origine du conteneur à la fin sans laisser d'espace.</p>

<pre class="brush: css hidden">* {box-sizing: border-box;}

.wrapper &gt; div {
    border-radius: 5px;
    background-color: rgb(207,232,220);
    padding: 1em;
}
    </pre>

<pre class="brush: css">.wrapper {
  display: flex;
}
</pre>

<pre class="brush: html">&lt;div class="wrapper"&gt;
  &lt;div class="box1"&gt;Un&lt;/div&gt;
  &lt;div class="box2"&gt;Deux&lt;/div&gt;
  &lt;div class="box3"&gt;Trois&lt;/div&gt;
&lt;/div&gt;
</pre>

<p>{{ EmbedLiveSample('Utiliser_display_flex', '300', '200') }}</p>

<h3>Définir la propriété flex</h3>

<p>En plus des propriétés ci-dessus applicables au conteneur <code>flex</code>, il existe des propriétés applicables aux éléments flex. Ces propriétés, entre autres choses, peuvent changer le mode d'adaptation des éléments, leur permettant de s'étaler et de se resserrer pour s'adapter à l'espace disponible.</p>

<p>À titre d'exemple, nous pouvons donner la valeur <code>1</code> à la propriété {{cssxref("flex")}} des éléments enfants. Tous les éléments vont grandir jusqu'à remplir le conteneur, au lieu de laisser de l'espace à la suite. S'il y a assez d'espace, les éléments vont devenir plus larges ; s'il y en a moins ils vont devenir plus étroits. En outre, si vous ajoutez un autre élément au balisage, les éléments vont rapetisser pour lui faire de la place — ils ajusteront leur taille pour prendre la même quantité d'espace, quel qu'il soit.</p>

<pre class="brush: css hidden">    * {box-sizing: border-box;}

    .wrapper &gt; div {
        border-radius: 5px;
        background-color: rgb(207,232,220);
        padding: 1em;
    }
    </pre>

<pre class="brush: css">.wrapper {
    display: flex;
}

.wrapper &gt; div {
    flex: 1;
}
</pre>

<pre class="brush: html">&lt;div class="wrapper"&gt;
    &lt;div class="box1"&gt;Un&lt;/div&gt;
    &lt;div class="box2"&gt;Deux&lt;/div&gt;
    &lt;div class="box3"&gt;Trois&lt;/div&gt;
&lt;/div&gt;
</pre>

<p>{{ EmbedLiveSample('Définir_la_propriété_flex', '300', '200') }}</p>

<div class="note">
<p><strong>Note :</strong> Ce n'est qu'une très brève introduction aux possibilités de Flexbox : pour en apprendre plus, voyez notre article sur <a href="/fr/docs/Learn/CSS/CSS_layout/Flexbox">Flexbox</a>.</p>
</div>

<h2 id="Disposition_en_trame">Disposition en trame</h2>

<p>Alors que « flexbox » est conçu pour une disposition unidimensionnelle, « Grid Layout » (Disposition tramée) est bidimensionnel — il place les choses en rangées et colonnes.</p>

<p>À nouveau, vous basculez en disposition tramée en donnant une valeur appropriée à <code>display</code> — <code>display: grid</code>. L'exemple ci-dessous utilise un balisage semblable à celui de l'exemple flex : un conteneur et quelques éléments enfants. Outre <code>display: grid</code>, nous définissons une trame de placement sur le parent avec les propriétés {{cssxref("grid-template-rows")}} et {{cssxref("grid-template-columns")}}. Nous avons défini trois colonnes de <code>1fr</code> chacune et deux lignes de <code>100px</code>. Il n'est pas nécessaire de mettre de règles sur les éléments enfants ; il seront automatiquement placés dans les cellules de trame créées.</p>

<h3>Utiliser display: grid</h3>

<pre class="brush: css hidden">    * {box-sizing: border-box;}

    .wrapper &gt; div {
        border-radius: 5px;
        background-color: rgb(207,232,220);
        padding: 1em;
    }
    </pre>

<pre class="brush: css">.wrapper {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
    grid-template-rows: 100px 100px;
    grid-gap: 10px;
}
</pre>

<pre class="brush: html">&lt;div class="wrapper"&gt;
    &lt;div class="box1"&gt;Un&lt;/div&gt;
    &lt;div class="box2"&gt;Deux&lt;/div&gt;
    &lt;div class="box3"&gt;Trois&lt;/div&gt;
    &lt;div class="box4"&gt;Quatre&lt;/div&gt;
    &lt;div class="box5"&gt;Cinq&lt;/div&gt;
    &lt;div class="box6"&gt;Six&lt;/div&gt;
&lt;/div&gt;
</pre>

<p>{{ EmbedLiveSample('Utiliser_display_grid', '300', '330') }}</p>

<h3>Placer des objets sur la grille</h3>

<p>Une fois la trame créée, vous pouvez y placer explicitement les éléments au lieu de compter sur le placement automatique. Dans ce second exemple ci‑dessous nous avons défini la même trame, mais cette fois avec trois éléments enfants. Nous avons défini début et fin de ligne pour chaque élément avec les propriétés {{cssxref("grid-column")}} et {{cssxref("grid-row")}}. Les éléments occupent alors plusieurs trames.</p>

<pre class="brush: css hidden">    * {box-sizing: border-box;}

    .wrapper &gt; div {
        border-radius: 5px;
        background-color: rgb(207,232,220);
        padding: 1em;
    }
    </pre>

<pre class="brush: css">.wrapper {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
    grid-template-rows: 100px 100px;
    grid-gap: 10px;
}

.box1 {
    grid-column: 2 / 4;
    grid-row: 1;
}

.box2 {
    grid-column: 1;
    grid-row: 1 / 3;
}

.box3 {
    grid-row: 2;
    grid-column: 3;
}
</pre>

<pre class="brush: html">&lt;div class="wrapper"&gt;
    &lt;div class="box1"&gt;Un&lt;/div&gt;
    &lt;div class="box2"&gt;Deux&lt;/div&gt;
    &lt;div class="box3"&gt;Trois&lt;/div&gt;
&lt;/div&gt;
</pre>
</div>

<p>{{ EmbedLiveSample('Placer_des_objets_sur_la_grille', '300', '330') }}</p>

<div class="note">
<p><strong>Note :</strong> Ces deux exemples ne sont qu'une petite partie de la puissance des dispositions tramées ; pour en savoir plus, voyez l'article <a href="/fr/docs/Learn/CSS/CSS_layout/Grids">Disposition tramée</a>.</p>
</div>

<p>La suite de ce guide porte sur d'autres méthodes de mise en page. Elles ont moins d'importance pour la structure générale de la mise en page, mais peuvent tout de même vous aider à réaliser des tâches spécifiques. En comprenant la nature de chaque tâche de mise en page, vous découvrez rapidement, en regardant un composant particulier de votre design, que le type de mise en page le plus adapté est souvent évident.</p>

<h2 id="Flotteurs_boîtes_flottantes">Flotteurs (boîtes flottantes)</h2>

<p>Faire flotter un élément change son comportement ainsi que celui de l'élément qui le suit dans le cours normal. L'élément est déplacé à gauche ou à droite. Il est sorti du cours normal. Le contenu environnant l'enveloppe comme si l'élément flottait dans ce contenu.</p>

<p>La propriété {{cssxref("float")}} a quatre valeurs possibles :</p>

<ul>
 <li><code>left</code> — fait flotter l'élément sur la gauche.</li>
 <li><code>right</code> — fait flotter l'élément sur la droite.</li>
 <li><code>none</code> — indique que rien ne flotte. C'est la valeur par défaut.</li>
 <li><code>inherit</code> — indique que la valeur de la propriété <code>float</code> sera héritée de celle de l'élément parent.</li>
</ul>

<p>Dans l'exemple ci‑dessous nous faisons flotter un élément <code>&lt;div&gt;</code> à gauche avec un valeur pour la propriété {{cssxref("margin")}} sur la droite pour éloigner le texte de l'élément. Cela donne un effet de texte enveloppant cette boîte. C'est l'essentiel de ce qu'il faut savoir à propos des boîtes flottantes dans le design du web moderne.</p>

<pre class="brush: css hidden">body {
    width: 90%;
    max-width: 900px;
    margin: 0 auto;
}

p {
    line-height: 2;
    word-spacing: 0.1rem;
}

.box {
    background-color: rgb(207,232,220);
    border: 2px solid rgb(79,185,227);
    padding: 10px;
    border-radius: 5px;
}
</pre>

<pre class="brush: html">&lt;h1&gt;Exemple simple de boîte flottante&lt;/h1&gt;

&lt;div class="box"&gt;Boîte flottante&lt;/div&gt;

&lt;p&gt; Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla luctus aliquam dolor, eu lacinia lorem placerat vulputate. Duis felis orci, pulvinar id metus ut, rutrum luctus orci. Cras porttitor imperdiet nunc, at ultricies tellus laoreet sit amet. Sed auctor cursus massa at porta. Integer ligula ipsum, tristique sit amet orci vel, viverra egestas ligula. Curabitur vehicula tellus neque, ac ornare ex malesuada et. In vitae convallis lacus. Aliquam erat volutpat. Suspendisse ac imperdiet turpis. Aenean finibus sollicitudin eros pharetra congue. Duis ornare egestas augue ut luctus. Proin blandit quam nec lacus varius commodo et a urna. Ut id ornare felis, eget fermentum sapien.&lt;/p&gt;

</pre>

<pre class="brush: css">
.box {
    float: left;
    width: 150px;
    height: 150px;
    margin-right: 30px;
}
</pre>

<p>{{ EmbedLiveSample('Flotteurs_boîtes_flottantes', '100%', 600) }}</p>

<div class="note">
<p><strong>Note :</strong> Les boîtes flottantes sont précisément expliquées dans la leçon à propos des propriétés <a href="/fr/docs/Learn/CSS/CSS_layout/Floats">float et clear</a>. Précédant les techniques telles que Flexbox et les trames, les boîtes flottantes étaient utilisées comme méthode pour créer des dispositions en colonnes. Vous rencontrerez peut‑être encore ce méthodes sur le Web ; nous les expliciterons dans la leçon sur les <a href="/fr/docs/Learn/CSS/CSS_layout/Legacy_Layout_Methods">Méthodes de mise en page traditionnelles</a>.</p>
</div>

<h2 id="Techniques_de_positionnement">Techniques de positionnement</h2>

<p>Le positionnement permet de déplacer un élément de l'endroit où il serait placé dans le cours normal vers un autre endroit. Le positionnement n'est pas une méthode pour créer des mises en page principales, il s'agit plutôt de gérer et d'affiner la position d'éléments donnés sur la page.</p>

<p>Il existe cependant des techniques utiles pour certains modes de positionnement se fondant sur la propriété {{cssxref("position")}}. Comprendre le positionnement aide aussi à comprendre le cours normal et le fait de déplacer un objet hors du cours normal.</p>

<p>Il y a cinq types de positionnement à connaître :</p>

<ul>
 <li><strong>positionnement statique</strong> : valeur par défaut reçue par chaque élément — il signifie simplement « placer l'élément à sa position normale suivant le cours normal de mise en page du document — rien de spécial à constater ici ».</li>
 <li><strong>positionnement relatif : </strong>modification de la position d'un élément dans la page — il est déplacé par rapport à sa position dans le cours normal — y compris la possibilité de chevaucher d'autres éléments de la page.</li>
 <li><strong>positionnement absolu</strong> : déplacement d'un élément indépendamment du cours normal de positionnement, comme s'il était placé sur un calque séparé. À partir de là, vous pouvez le fixer à une position relative au bord de la page de l'élément <code>&lt;html&gt;</code> (ou de son plus proche élément ancêtre positionné). Ce positionnement est utile pour créer des effets de mise en page complexes tels que des boîtes à onglets où différents panneaux de contenu sont superposés, affichés ou cachés comme vous le souhaitez, ou des panneaux d'information hors de l'écran par défaut, mais qui peuvent glisser à l'écran à l'aide d'un bouton de contrôle.</li>
 <li><strong>positionnement fixe : </strong>tout à fait semblable au précédent, à l'exception que l'élément est fixé par rapport à la vue du navigateur et non d'un autre élément. C'est très pratique pour créer des effets tels qu'un menu de navigation persistant, toujours au même endroit sur l'écran, quand l'utilisateur fait défiler le reste de la page.</li>
 <li><strong>positionnement collant : </strong>nouvelle méthode de positionnement qui fait qu'un élément se comporte comme <code>position: static</code> jusqu'à un certain décalage de la vue au delà duquel il se comporte comme si sa propriété était <code>position: fixed</code>.</li>
</ul>

<h3 id="Exemple_simple_de_positionnement">Exemple simple de positionnement</h3>

<p>Afin de se familiariser avec ces techniques de mises en page, nous allons vous montrer quelques exemples. Nos exemples utiliserons tous le même code HTML, qui est celui-ci:</p>

<pre class="brush: html">&lt;h1&gt;Positionnement&lt;/h1&gt;

&lt;p&gt;Je suis un élément de niveau bloc de base.&lt;/p&gt;
&lt;p class="positioned"&gt;Je suis un élément de niveau bloc de base.&lt;/p&gt;
&lt;p&gt;Je suis un élément de niveau bloc de base.&lt;/p&gt;</pre>

<p>Ce code HTML sera stylisé par défaut en utilisant la CSS suivante :</p>

<pre class="brush: css">body {
  width: 500px;
  margin: 0 auto;
}

p {
    background-color: rgb(207,232,220);
    border: 2px solid rgb(79,185,227);
    padding: 10px;
    margin: 10px;
    border-radius: 5px;
}
</pre>

<p>Le rendu est le suivant:</p>

<p>{{ EmbedLiveSample('Exemple_simple_de_positionnement', '100%', 300) }}</p>

<h3 id="Positionnement_relatif">Positionnement relatif</h3>

<p>Le positionnement relatif vous permet de décaler un élément de la position qu'il occuperait par défaut dans le cours normal de la mise en page. Ce positionnement permet de déplacer légèrement une icône pour l'aligner avec une étiquette de texte. Pour faire cette opération, nous ajoutons la règle suivante pour réaliser le positionnement relatif :</p>

<pre class="brush: css">.positioned {
  position: relative;
  top: 30px;
  left: 30px;
}</pre>

<p>Ici, nous donnons au paragraphe médian à la propriété  {{cssxref("position")}} la valeur <code>relative</code> — ce qui ne fait rien en soi, alors nous ajoutons également les propriétés {{cssxref("top")}} et {{cssxref("left")}}. Elles servent à déplacer l'élément en question vers le bas et à droite — cela pourrait sembler être l'opposé de ce à quoi vous vous attendiez, mais représentez-vous l'élément comme poussé à partir de ses côtés gauche et haut : il en résulte un déplacement vers la droite et vers le bas.</p>

<p>Ajouter ce code donne le résultat suivant :</p>

<pre class="brush: html hidden">&lt;h1&gt;Positionnement relatif&lt;/h1&gt;

&lt;p&gt;Je suis un élément de niveau bloc de base.&lt;/p&gt;
&lt;p class="positioned"&gt;Voici un élément avec un positionnement relatif.&lt;/p&gt;
&lt;p&gt;Je suis un élément de niveau bloc de base.&lt;/p&gt;</pre>

<pre class="brush: css hidden">body {
  width: 500px;
  margin: 0 auto;
}

p {
    background-color: rgb(207,232,220);
    border: 2px solid rgb(79,185,227);
    padding: 10px;
    margin: 10px;
    border-radius: 5px;
}
</pre>

<pre class="brush: css">.positioned {
  position: relative;
  background: rgba(255,84,104,.3);
  border: 2px solid rgb(255,84,104);
  top: 30px;
  left: 30px;
}</pre>

<p>{{ EmbedLiveSample('Positionnement_relatif', '100%', 300) }}</p>

<h3 id="Positionnement_absolu">Positionnement absolu</h3>

<p>Le positionnement absolu s'utilise pour sortir totalement un élément du cours normal de la mise en page et le placer selon son décalage par rapport à un bloc conteneur.</p>

<p>En revenant à l'exemple sans positionnement, nous pourrions ajouter la règle CSS suivante pour implémenter un positionnement absolu :</p>

<pre class="brush: css">.positioned {
  position: absolute;
  top: 30px;
  left: 30px;
}</pre>

<p>Ici pour notre paragraphe médian, nous donnons à la propriété {{cssxref("position")}} la valeur <code>absolute</code> et les mêmes valeurs aux propriétés {{cssxref("top")}} et {{cssxref("left")}} que précédemment. Ajouter ce code, cependant, donnera le résultat suivant :</p>

<pre class="brush: html hidden">&lt;h1&gt;Positionnement absolu&lt;/h1&gt;

&lt;p&gt;Je suis un élément de niveau bloc de base.&lt;/p&gt;
&lt;p class="positioned"&gt;Voici un élément avec un positionnement absolu.&lt;/p&gt;
&lt;p&gt;Je suis un élément de niveau bloc de base.&lt;/p&gt;</pre>

<pre class="brush: css hidden">body {
  width: 500px;
  margin: 0 auto;
}

p {
    background-color: rgb(207,232,220);
    border: 2px solid rgb(79,185,227);
    padding: 10px;
    margin: 10px;
    border-radius: 5px;
}
</pre>

<pre class="brush: css">.positioned {
  position: absolute;
  background: rgba(255,84,104,.3);
  border: 2px solid rgb(255,84,104);
  top: 30px;
  left: 30px;
}</pre>

<p>{{ EmbedLiveSample('Positionnement_absolu', '100%', 300) }}</p>

<p>C'est vraiment différent ! L'élément positionné a maintenant complètement été séparé du reste de la mise en page et se situe au haut de celle-ci. Les deux autres paragraphes se trouvent maintenant ensemble comme si leur frère positionné n'existait pas. Les propriétés {{cssxref("top")}} et {{cssxref("left")}} ont des effets différents pour un positionnement absolu comparativement à un relatif. Dans ce cas les décalages ont été calculés à compter du haut et du côté gauche de la la page. Il est possible de modifier l'élément parent conteneur ; nous verrons cela dans la leçon sur le <a href="/fr/docs/Learn/CSS/CSS_layout/Positioning">positionnement</a>.</p>

<h3 id="Positionnement_fixé">Positionnement fixé</h3>

<p>Le positionnement fixé sort l'élément du cours normal de la même façon que le positionnement absolu. Toutefois, les décalages ne sont plus relatifs au conteneur, mais à la vue. L'élément étant fixé par rapport à la vue, nous pourrons créer des effets comme celui d'un menu restant fixé au haut de la fenêtre alors que la page défile sous lui.</p>

<p>Pour cet exemple, l'HTML est constitué de trois paragraphes de texte, de façon à pouvoir les faire défiler, et d'une boîte à laquelle nous avons donné la propriété <code>position: fixed</code>.</p>

<pre class="brush: html">&lt;h1&gt;Positionnement fixé&lt;/h1&gt;

&lt;div class="positioned"&gt;Fixé&lt;/div&gt;

&lt;p&gt;Paragraphe 1.&lt;/p&gt;
&lt;p&gt;Paragraphe 2.&lt;/p&gt;
&lt;p&gt;Paragraphe 3.&lt;/p&gt;
</pre>

<pre class="brush: html hidden">&lt;h1&gt;Positionnement fixé&lt;/h1&gt;

&lt;div class="positioned"&gt;Fixé&lt;/div&gt;

&lt;p&gt; Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla luctus aliquam dolor, eu lacinia lorem placerat vulputate. Duis felis orci, pulvinar id metus ut, rutrum luctus orci. Cras porttitor imperdiet nunc, at ultricies tellus laoreet sit amet. Sed auctor cursus massa at porta. Integer ligula ipsum, tristique sit amet orci vel, viverra egestas ligula. Curabitur vehicula tellus neque, ac ornare ex malesuada et. In vitae convallis lacus. Aliquam erat volutpat. Suspendisse ac imperdiet turpis. Aenean finibus sollicitudin eros pharetra congue. Duis ornare egestas augue ut luctus. Proin blandit quam nec lacus varius commodo et a urna. Ut id ornare felis, eget fermentum sapien.&lt;/p&gt;

&lt;p&gt;Nam vulputate diam nec tempor bibendum. Donec luctus augue eget malesuada ultrices. Phasellus turpis est, posuere sit amet dapibus ut, facilisis sed est. Nam id risus quis ante semper consectetur eget aliquam lorem. Vivamus tristique elit dolor, sed pretium metus suscipit vel. Mauris ultricies lectus sed lobortis finibus. Vivamus eu urna eget velit cursus viverra quis vestibulum sem. Aliquam tincidunt eget purus in interdum. Cum sociis natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus.&lt;/p&gt;

&lt;p&gt; Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla luctus aliquam dolor, eu lacinia lorem placerat vulputate. Duis felis orci, pulvinar id metus ut, rutrum luctus orci. Cras porttitor imperdiet nunc, at ultricies tellus laoreet sit amet. Sed auctor cursus massa at porta. Integer ligula ipsum, tristique sit amet orci vel, viverra egestas ligula. Curabitur vehicula tellus neque, ac ornare ex malesuada et. In vitae convallis lacus. Aliquam erat volutpat. Suspendisse ac imperdiet turpis. Aenean finibus sollicitudin eros pharetra congue. Duis ornare egestas augue ut luctus. Proin blandit quam nec lacus varius commodo et a urna. Ut id ornare felis, eget fermentum sapien.&lt;/p&gt;

</pre>

<pre class="brush: css hidden">body {
    width: 500px;
    margin: 0 auto;
}

.positioned {
    background: rgba(255,84,104,.3);
    border: 2px solid rgb(255,84,104);
    padding: 10px;
    margin: 10px;
    border-radius: 5px;
}</pre>

<pre class="brush: css">.positioned {
    position: fixed;
    top: 30px;
    left: 30px;
}</pre>

<p>{{ EmbedLiveSample('Positionnement_fixé', '100%', 200) }}</p>

<h3 id="Positionnement_collant">Positionnement collant</h3>

<p>Le positionnement collant est la dernière méthode de positionnement à notre disposition. Elle mélange le positionnement statique par défaut avec le positionnement fixé. Lorsqu'un élément a la propriété <code>position: sticky</code>, il défile dans le cours normal jusqu'à atteindre un décalage défini de la fenêtre de vue. A ce moment-là, il est « collé » comme si <code>position: fixed</code> lui était appliqué.</p>

<pre class="brush: html hidden">&lt;h1&gt;Positionnement collant&lt;/h1&gt;

&lt;p&gt; Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla luctus aliquam dolor, eu lacinia lorem placerat vulputate. Duis felis orci, pulvinar id metus ut, rutrum luctus orci. Cras porttitor imperdiet nunc, at ultricies tellus laoreet sit amet. Sed auctor cursus massa at porta. Integer ligula ipsum, tristique sit amet orci vel, viverra egestas ligula. Curabitur vehicula tellus neque, ac ornare ex malesuada et. In vitae convallis lacus. Aliquam erat volutpat. Suspendisse ac imperdiet turpis. Aenean finibus sollicitudin eros pharetra congue. Duis ornare egestas augue ut luctus. Proin blandit quam nec lacus varius commodo et a urna. Ut id ornare felis, eget fermentum sapien.&lt;/p&gt;

&lt;div class="positioned"&gt;Collé&lt;/div&gt;

&lt;p&gt;Nam vulputate diam nec tempor bibendum. Donec luctus augue eget malesuada ultrices. Phasellus turpis est, posuere sit amet dapibus ut, facilisis sed est. Nam id risus quis ante semper consectetur eget aliquam lorem. Vivamus tristique elit dolor, sed pretium metus suscipit vel. Mauris ultricies lectus sed lobortis finibus. Vivamus eu urna eget velit cursus viverra quis vestibulum sem. Aliquam tincidunt eget purus in interdum. Cum sociis natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus.&lt;/p&gt;

&lt;p&gt; Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla luctus aliquam dolor, eu lacinia lorem placerat vulputate. Duis felis orci, pulvinar id metus ut, rutrum luctus orci. Cras porttitor imperdiet nunc, at ultricies tellus laoreet sit amet. Sed auctor cursus massa at porta. Integer ligula ipsum, tristique sit amet orci vel, viverra egestas ligula. Curabitur vehicula tellus neque, ac ornare ex malesuada et. In vitae convallis lacus. Aliquam erat volutpat. Suspendisse ac imperdiet turpis. Aenean finibus sollicitudin eros pharetra congue. Duis ornare egestas augue ut luctus. Proin blandit quam nec lacus varius commodo et a urna. Ut id ornare felis, eget fermentum sapien.&lt;/p&gt;       </pre>

<pre class="brush: css hidden">body {
  width: 500px;
  margin: 0 auto;
}

.positioned {
  background: rgba(255,84,104,.3);
  border: 2px solid rgb(255,84,104);
  padding: 10px;
  margin: 10px;
  border-radius: 5px;
}</pre>

<pre class="brush: css">.positioned {
  position: sticky;
  top: 30px;
  left: 30px;
}</pre>

<p>{{ EmbedLiveSample('Positionnement_collant', '100%', 200) }}</p>

<div class="note">
<p><strong>Note :</strong> pour plus de précisions à propos du positionnement, voir l'article <a href="/fr/docs/Learn/CSS/CSS_layout/Positioning">Positionnement</a>.</p>
</div>

<h2 id="Les_tableaux_CSS">Les tableaux CSS</h2>

<p>Les tableaux HTML sont utiles pour afficher des données sous forme de tableaux, mais il y a des années de cela — avant même que les bases des CSS soit prises en charge de manière fiable par les navigateurs — les développeurs web avaient l'habitude d'utiliser les tableaux pour agencer toute la mise en page — y plaçant les en‑têtes, les pieds-de-page, diverses colonnes, etc. en multiples lignes et colonnes de tableaux. Cela fonctionnait en son temps, mais il y avait beaucoup de problèmes — la mise en page par tableau n'est pas souple, très lourde en balisage, difficile à déboguer et sémantiquement erronée (par ex., les utilisateurs de lecteur d'écran avaient des problèmes de navigation avec cette disposition en tableau).</p>

<p>La façon dont un tableau est affiché sur une page web quand vous utilisez le balisage « table » résulte d'un ensemble de propriétés des CSS définissant la composition du tableau. Ces propriétés peuvent être utilisées pour placer des éléments qui ne sont pas des tableaux, utilisation quelquefois désignée sous le vocable « utiliser des tableaux CSS ».</p>

<p>Prenons un exemple. Tout d'abord, un simple balisage qui crée un formulaire HTML. Chaque élément en entrée a une étiquette ; nous avons également inclus une légende à l'intérieur d'un paragraphe. Chaque paire étiquette/entrée est incorporée dans un élément {{htmlelement("div")}} pour les besoins de la mise en page.</p>

<pre class="brush: html">&lt;form&gt;
  &lt;p&gt;Tout d'abord, dites‑nous votre nom et votre âge.&lt;/p&gt;
  &lt;div&gt;
    &lt;label for="fname"&gt;Prénom :&lt;/label&gt;
    &lt;input type="text" id="fname"&gt;
  &lt;/div&gt;
  &lt;div&gt;
    &lt;label for="lname"&gt;Nom :&lt;/label&gt;
    &lt;input type="text" id="lname"&gt;
  &lt;/div&gt;
  &lt;div&gt;
    &lt;label for="age"&gt;Âge :&lt;/label&gt;
    &lt;input type="text" id="age"&gt;
  &lt;/div&gt;
&lt;/form&gt;</pre>

<p>Maintenant, le CSS pour cet exemple. Le gros de la CSS est plutôt ordinaire, à l'exception de l'utilisation de la propriété {{cssxref("display")}}. Les éléments {{htmlelement("form")}}, {{htmlelement("div")}} et {{htmlelement("label")}} ainsi que {{htmlelement("input")}} ont été configurés pour disposés en tableau, en lignes de tableau et en cellules de tableau respectivement — à la base, ils se comporteront comme dans le cas d'un balisage de tableau HTML, avec pour résultat un bon alignement par défaut entre les étiquettes et le texte. Tout ce qu'il nous reste à faire est d'ajouter un peu d'ampleur, des marges, etc. pour que tout soit agréable visuellement et c'est tout.</p>

<p>Notez que les propriétés <code>display: table-caption;</code> et <code>caption-side: bottom;</code> ont été affectées au paragraphe légende — il sera donc disposé comme une légende de tableau ({{htmlelement("caption")}})  placée en bas de la table pour des raisons de style, même si son balisage est placé avant les éléments <code>input</code> dans le code source. Voilà une bonne dose de souplesse.</p>

<pre class="brush: css">html {
  font-family: sans-serif;
}

form {
  display: table;
  margin: 0 auto;
}

form div {
  display: table-row;
}

form label, form input {
  display: table-cell;
  margin-bottom: 10px;
}

form label {
  width: 200px;
  padding-right: 5%;
  text-align: right;
}

form input {
  width: 300px;
}

form p {
  display: table-caption;
  caption-side: bottom;
  width: 400px;
  color: #999;
  font-style: italic;
}</pre>

<p>Ce qui nous donne le résultat suivant:</p>

<p>{{ EmbedLiveSample('Les_tableaux_CSS', '100%', '170') }}</p>

<p>Vous pouvez également examiner cet exemple directement à <a href="https://mdn.github.io/learning-area/css/styling-boxes/box-model-recap/css-tables-example.html">css-tables-example.html</a> (voyez le <a href="https://github.com/mdn/learning-area/blob/master/css/styling-boxes/box-model-recap/css-tables-example.html">code source également</a>).</p>

<h2 id="Disposition_sur_plusieurs_colonnes">Disposition sur plusieurs colonnes</h2>

<p>Le module mise en page sur plusieurs colonnes permet de placer un contenu en colonnes, telle la présentation de l'enchaînement des textes dans un journal. Bien que la lecture de colonnes de haut en bas soit moins utile dans un contexte Web, car il n'est pas question de forcer les utilisateurs à faire défiler en tous sens le contenu d'écran, la disposition en colonnes peut se révéler une technique utile.</p>

<p>Pour transformer un bloc en conteneur multicolonnes, utilisez soit la propriété {{cssxref("column-count")}} qui indique au navigateur le nombre de colonnes souhaitées, soit la propriété {{cssxref("column-width")}}, qui demande au navigateur de remplir le conteneur d'autant de colonnes de la largeur donnée.</p>

<p>Dans l'exemple ci–dessous, nous démarrons avec un bloc HTML dans un élément conteneur <code>&lt;div&gt;</code> de la classe <code>container</code>.</p>

<pre class="brush: html">&lt;div class="container"&gt;
    &lt;h1&gt;Disposition en colonnes&lt;/h1&gt;

    &lt;p&gt;Paragraphe 1.&lt;/p&gt;
    &lt;p&gt;Paragraphe 2.&lt;/p&gt;

&lt;/div&gt;
</pre>

<p>Noux utilisons une propriété <code>column-width</code> de valeur 200 pixels pour ce conteneur ; le navigateur crée autant de colonnes de 200 pixels de large qu'il est possible de faire entrer dans le conteneur, puis il partage l'espace restant entre les colonnes crées.</p>

<pre class="brush: html hidden">    &lt;div class="container"&gt;
        &lt;h2&gt;Disposition en colonnes&lt;/h2&gt;

        &lt;p&gt; Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla luctus aliquam dolor, eu lacinia lorem placerat vulputate. Duis felis orci, pulvinar id metus ut, rutrum luctus orci. Cras porttitor imperdiet nunc, at ultricies tellus laoreet sit amet. Sed auctor cursus massa at porta. Integer ligula ipsum, tristique sit amet orci vel, viverra egestas ligula. Curabitur vehicula tellus neque, ac ornare ex malesuada et. In vitae convallis lacus. Aliquam erat volutpat. Suspendisse ac imperdiet turpis. Aenean finibus sollicitudin eros pharetra congue. Duis ornare egestas augue ut luctus. Proin blandit quam nec lacus varius commodo et a urna. Ut id ornare felis, eget fermentum sapien.&lt;/p&gt;


        &lt;p&gt;Nam vulputate diam nec tempor bibendum. Donec luctus augue eget malesuada ultrices. Phasellus turpis est, posuere sit amet dapibus ut, facilisis sed est. Nam id risus quis ante semper consectetur eget aliquam lorem. Vivamus tristique elit dolor, sed pretium metus suscipit vel. Mauris ultricies lectus sed lobortis finibus. Vivamus eu urna eget velit cursus viverra quis vestibulum sem. Aliquam tincidunt eget purus in interdum. Cum sociis natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus.&lt;/p&gt;

    &lt;/div&gt;
        </pre>

<pre class="brush: css hidden">body { max-width: 800px; margin: 0 auto; } </pre>

<pre class="brush: css">    .container {
        column-width: 200px;
    }</pre>

<p>{{ EmbedLiveSample('Disposition_sur_plusieurs_colonnes', '100%', 200) }}</p>

<h2 id="Résumé">Résumé</h2>

<p>Cet article donne un bref résumé de toutes les techniques de mise en page à connaître. Poursuivez la lecture pour en savoir plus à propos de chaque technique !</p>

<p>{{NextMenu("Apprendre/CSS/CSS_layout/Floats", "Apprendre/CSS/CSS_layout")}}</p>

<h2 id="In_this_module">In this module</h2>

<ul>
 <li><a href="/fr/docs/Apprendre/CSS/CSS_layout">La mise en page avec les CSS</a></li>
 <li><a href="/fr/docs/Apprendre/CSS/CSS_layout/Normal_Flow">Cours normal</a></li>
 <li><a href="/fr/docs/Learn/CSS/CSS_layout/Flexbox">Flexbox</a></li>
 <li><a href="/fr/docs/Learn/CSS/CSS_layout/Grids">Grid</a></li>
 <li><a href="/fr/docs/Learn/CSS/CSS_layout/Floats">Floats</a></li>
 <li><a href="/fr/docs/Learn/CSS/CSS_layout/Positioning">Positioning</a></li>
 <li><a href="/fr/docs/Learn/CSS/CSS_layout/Multiple-column_Layout">Multiple-column Layout</a></li>
 <li><a href="/fr/docs/Learn/CSS/CSS_layout/Legacy_Layout_Methods">Legacy Layout Methods</a></li>
 <li><a href="/fr/docs/Learn/CSS/CSS_layout/Supporting_Older_Browsers">Supporting older browsers</a></li>
 <li><a href="/fr/docs/Learn/CSS/CSS_layout/Fundamental_Layout_Comprehension">Fundamental Layout Comprehension Assessment</a></li>
</ul>