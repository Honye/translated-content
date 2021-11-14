---
title: Les widgets de formulaire natifs
slug: Learn/Forms/Basic_native_form_controls
tags:
  - Contrôles
  - Exemple
  - Formulaires
  - Guide
  - HTML
  - Web
  - Widgets
translation_of: Learn/Forms/Basic_native_form_controls
original_slug: Web/Guide/HTML/Formulaires/Les_blocs_de_formulaires_natifs
---
<div>{{LearnSidebar}}<br>
{{PreviousMenuNext("Web/Guide/HTML/Formulaires/Comment_structurer_un_formulaire_HTML", "Web/Guide/HTML/Formulaires/Envoyer_et_extraire_les_données_des_formulaires", "Web/Guide/HTML/Formulaires")}}</div>

<p>Nous examinerons maintenant en détail les fonctionnalités des divers widgets pour formulaires, en soulignant les options disponibles pour collecter les différents types de données. Ce guide vise à être exhaustif en couvrant tous les widgets natifs de formulaire disponibles.</p>

<table class="standard-table">
 <tbody>
  <tr>
   <th scope="row">Prérequis :</th>
   <td>Notions concernant les ordinateurs et les <a href="/fr/docs/Apprendre/HTML/Introduction_à_HTML">connaissances de base du HTML</a>.</td>
  </tr>
  <tr>
   <th scope="row">Objectif :</th>
   <td>Comprendre quels sont les types de widgets de forme native disponibles dans les navigateurs pour collecter des données et comment les mettre en œuvre en se servant du HTML.</td>
  </tr>
 </tbody>
</table>

<p>Ici, nous nous attarderons sur les widgets de formulaires intégrés aux navigateurs, mais comme les formulaires HTML restent très circonscrits et que la qualité des implémentations peut être très différente d'un navigateur à l'autre, les développeurs web construisent parfois leurs propres widgets de formulaires — voir <a href="/fr/docs/Web/Guide/HTML/Formulaires/Comment_construire_des_widgets_de_formulaires_personnalisés">Comment construire des widgets de formulaires personnalisés</a> plus loin dans ce même module pour plus d'idées à ce propos.</p>

<div class="note">
<p><strong>Note :</strong> La plupart des fonctionnalités discutées dans cet article sont abondamment explicitées dans les navigateurs ; nous soulignerons les exceptions à ce sujet. Si vous voulez plus de précisions, consultez les <a href="/fr/docs/Web/HTML/Element#Forms">références aux éléments de formulaires HTML</a>, et en particulier nos références détaillées aux <a href="/fr/docs/Web/HTML/Element/input">types &lt;input&gt;</a>.</p>
</div>

<h2 id="Attributs_communs">Attributs communs</h2>

<p>Beaucoup d'éléments utilisés pour définir les widgets de formulaire ont leurs propres attributs. Cependant, il y a un jeu d'attributs communs à tous les éléments de formulaire. Il vous permettent un certain contrôle sur ces widgets. Voici une liste de ces attributs communs :</p>

<table>
 <thead>
  <tr>
   <th scope="col">Nom de l'attribut</th>
   <th scope="col">Valeur par défaut</th>
   <th scope="col">Description</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><code>autofocus</code></td>
   <td>(<em>false</em>)</td>
   <td>Cet attribut, booléen, vous permet de spécifier que cet élément doit avoir automatiquement le focus au chargement de la page, sauf si l'utilisateur prend la main, en faisant, par exemple, une saisie dans un autre contrôle. Seul un élément associé à un formulaire peut avoir cet attribut activé.</td>
  </tr>
  <tr>
   <td><code>disabled</code></td>
   <td>(<em>false</em>)</td>
   <td>Cet attribut est un booléen. Il indique que l'utilisateur ne peut pas avoir d'action sur cet élément. S'il n'est pas précisé, l'élément hérite son comportement de l'élément contenant, comme, {{HTMLElement("fieldset")}} ; si le conteneur n'a pas d'attribut <code>disabled</code> mis, l'élément est activé.</td>
  </tr>
  <tr>
   <td><code>form</code></td>
   <td></td>
   <td>L'élément &lt;form&gt; auquel le widget est associé. La valeur de l'attribut doit être l'attribut <code>id</code> d'un élément {{HTMLElement("form")}} dans le même document. En théorie, il vous permet de mettre un widget en dehors d'un élément {{HTMLElement("form")}}. En pratique, toutefois, il n'y a pas de navigateur qui prenne en charge cette fonctionnalité.</td>
  </tr>
  <tr>
   <td><code>name</code></td>
   <td></td>
   <td>Le nom de l'élément ; il sera soumis en même temps que les données du formulaire.</td>
  </tr>
  <tr>
   <td><code>value</code></td>
   <td></td>
   <td>La valeur initiale de l'élément.</td>
  </tr>
 </tbody>
</table>

<h2 id="Champs_de_saisie_de_texte">Champs de saisie de texte</h2>

<p>Les champs {{htmlelement("input")}} de saisie de texte sont les widgets de formulaire les plus élémentaires. Ils sont très pratiques pour permettre à un utilisateur de saisir n'importe quel type de données. Toutefois, certains champs textuels peuvent être spécialisés pour répondre à des besoins précis. Nous avons déjà vu quelques exemples.</p>

<div class="note">
<p><strong>Note :</strong> Les champs textuels dans les formulaires HTML sont des contrôles de saisie de texte brut. Cela signifie que vous ne pouvez pas les utiliser pour réaliser de la <a href="/fr/docs/Rich-Text_Editing_in_Mozilla" title="/en-US/docs/Rich-Text_Editing_in_Mozilla">mise en forme riche</a> (gras, italique, etc.). Tous les éditeurs de textes évolués que vous rencontrez utilisent des widgets personnalisés créés avec HTML, CSS et JavaScript.</p>
</div>

<p>Tous les champs textuels ont des comportement en commun :</p>

<ul>
 <li>Il peuvent être définis comme {{htmlattrxref("readonly","input")}} (l'utilisateur ne peut pas modifier la valeur) voire {{htmlattrxref("disabled","input")}} (la valeur n'est pas envoyé avec le restant des données du formulaire).</li>
 <li>Ils peuvent avoir un {{htmlattrxref("placeholder","input")}}. Ce texte apparaît dans le champs de saisie et décrit brièvement le rôle de cette boîte.</li>
 <li>Des contraintes peuvent leur être imposées avec {{htmlattrxref("size","input")}} (la taille physique de la boîte) et avec {{htmlattrxref("maxlength","input")}} (le nombre maximum de caractères qui peuvent être saisis dans la boîte).</li>
 <li>Ils peuvent bénéficier d'une <a href="/fr/docs/HTML/Element/input#attr-spellcheck" title="/fr/docs/HTML/Element/input#attr-spellcheck">correction orthographique</a>, si le navigateur la prend en charge.</li>
</ul>

<div class="note">
<p><strong>Note :</strong> L'élément {{htmlelement("input")}} est spécial car il peut être pratiquement n'importe quoi. En réglant simplement ses attributs de type, il peut changer radicalement, et il est utilisé pour créer la plupart des types de widgets de formulaire allant des champs texte sur une seule ligne, contrôles sans entrée de texte, contrôles de date et heure jusqu'aux boutons. Il y a toutefois des exceptions, comme {{htmlelement("textarea")}} pour les entrées multi-lignes. Prenez bien note de ceci en lisant cet article.</p>
</div>

<h3 id="Champs_texte_sur_une_seule_ligne"> Champs texte sur une seule ligne</h3>

<p>On crée un champ texte sur une seule ligne avec l'élément {{HTMLElement("input")}} dont l'attribut {{htmlattrxref("type", "input")}} est mis à <code>text</code> (maisi, si vous n'indiquez pas l'attribut {{htmlattrxref("type", "input")}}, <code>text</code> est la valeur par défaut). <code>text</code> est aussi la valeur de repli si celle indiquée pour l'attribut {{htmlattrxref("type", "input")}} est inconnue du navigateur (par exemple, si vous spécifiez <code>type="date"</code> et que le navigateur ne prend pas en charge les sélecteurs de date natifs).</p>

<div class="note">
<p><strong>Note :</strong> Vous trouverez des exemples de tous les types de champ texte sur une ligne dans GitHub à <a href="https://github.com/mdn/learning-area/blob/master/html/forms/native-form-widgets/single-line-text-fields.html">single-line-text-fields.html</a> (voir <a href="https://mdn.github.io/learning-area/html/forms/native-form-widgets/single-line-text-fields.html">directement aussi</a>).</p>
</div>

<p>Voici un exemple élémentaire de champ texte sur une ligne :</p>

<pre class="brush: html">&lt;input type="text" id="comment" name="comment" value="Je suis un champ texte"&gt;</pre>

<p>Les champs texte sur une ligne n'ont qu'une seule contrainte : si vous saisissez du texte avec des sauts de ligne, le navigateur les supprime avant d'envoyer les données.</p>

<p><img alt="Screenshots of single line text fields on several platforms." src="https://developer.mozilla.org/files/4273/all-single-line-text-field.png"></p>

<p>HTML5 améliore le champ texte élémentaire sur une ligne par ajout de valeurs spéciales pour l'attribut {{htmlattrxref("type","input")}}. Ces valeurs conservent l'élément {{HTMLElement("input")}} en tant que champ texte sur une ligne mais ajoutent quelques contraintes et caractéristiques supplémentaires au champ.</p>

<h4 id="Champ_dadresse_électronique">Champ d'adresse électronique</h4>

<p>Ce type de champ est défini en donnant la valeur <code>email</code> à l'attribut {{htmlattrxref("type","input")}} :</p>

<pre class="brush: html">    &lt;input type="email" id="email" name="email" multiple&gt;</pre>

<p>Avec ce <code>type</code> , l'utilisateur doit saisir un e‑mail valide dans le champ. Tout autre type de contenu amène le navigateur à émettre une erreur lors de la soumission du formulaire. Notez que cette validation s'opère côté client et est faite par le navigateur :</p>

<p><img alt="Entrée d'un e-mail non valide déclenchant un message d'avertissement « Veuillez saisir une adresse électronique valide »" src="fr-email.png"></p>

<p>Avec l'attribut {{htmlattrxref("multiple","input")}}, l'utilisateur pourra saisir plusieurs adresses électroniques dans la même entrée (avec une virgule comme séparateur).</p>

<p>Sur certains périphériques (les mobiles en particulier), un clavier virtuel différent et mieux adapté à la saisie d'adresses électroniques peut être affiché.</p>

<div class="note">
<p><strong>Note :</strong> Vous trouverez plus de détails sur la validation des formulaires dans l'article <a href="/fr/docs/Web/Guide/HTML/Formulaires/Validation_donnees_formulaire">Validation des données de formulaires</a>.</p>
</div>

<h4 id="Champ_pour_mot_de_passe">Champ pour mot de passe</h4>

<p>Ce type de champ est défini en donnant la valeur <code>password</code> à l'attribut {{htmlattrxref("type","input")}} :</p>

<pre class="brush: html">    &lt;input type="password" id="pwd" name="pwd"&gt;</pre>

<p>Aucune contrainte de saisie du texte n'est ajoutée, mais la valeur entrée dans le champ est masquée (avec des points ou des astérisques) afin qu'elle ne puisse pas être lue par d'autres.</p>

<p>Gardez à l'esprit que ceci n'est qu'une fonction de l'interface utilisateur ; sauf si vous soumettez le formulaire de manière sécurisée, il sera envoyé en texte brut, ce qui est mauvais pour la sécurité — un tiers malicieux pourrait intercepter les données et voler le mot de passe, les détails de la carte de crédit ou autre texte soumis. La meilleure façon de protéger l'utilisateur contre ceci consiste à héberger toute page contenant des formulaires avec une connexion sécurisée (par ex. avec https:// ...), ainsi les données sont chiffrées avant expédition.</p>

<p>Les navigateurs modernes reconnaissent les risques courus lors de l'envoi de formulaires avec une connexion non sécurisée et affichent des avertissements pour prévenir les utilisateurs. Pour plus de précisions sur ce que Firefox a mis en œuvre, voir <a href="/fr/docs/Sécurité/MotsdepasseInsecurisés">Mots de passe peu sûrs</a>.</p>

<h4 id="Champ_de_recherche">Champ de recherche</h4>

<p>Ce type de champ se définit avec la valeur <code>search</code> de l'attribut {{htmlattrxref("type","input")}} :</p>

<pre class="brush: html">    &lt;input type="search" id="search" name="search"&gt;</pre>

<p>La principale différence entre un champ textuel et un champ de recherche est dans l'apparence — souvent, les champs de recherche sont affichés avec des coins arrondis, et/ou avec une « × » à cliquer pour effacer la valeur entrée. Toutefois, une fonction est aussi ajoutée : les valeurs saisies peuvent être automatiquement enregistrées afin d'être utilisées pour compléter des recherches sur plusieurs pages du même site.</p>

<p><img alt="Screenshots of search fields on several platforms." src="all-search-field.png"></p>

<h4 id="Champ_pour_numéro_de_téléphone">Champ pour numéro de téléphone</h4>

<p>Ce type de champ se définit en donnant la valeur <code>tel</code> à l'attribut {{htmlattrxref("type","input")}} :</p>

<pre class="brush: html">    &lt;input type="tel" id="tel" name="tel"&gt;</pre>

<p>À cause de la grande variété de formats de numéros de téléphones à travers le monde, ce type de champ n'ajoute pas de contrainte à la valeur saisie par l'utilisateur. C'est principalement une différence sémantique, bien que sur certains appareils (notamment mobiles) un clavier virtuel différent, mieux adapté à la saisie de numéros de téléphone, puisse être présenté.</p>

<h4 id="Champ_dURL">Champ d'URL</h4>

<p>Ce type de champ se définit en donnant la valeur <code>url</code> à l'attribut {{htmlattrxref("type","input")}} :</p>

<pre class="brush: html">    &lt;input type="url" id="url" name="url"&gt;</pre>

<p>Il ajoute une contrainte de validation spéciale du champ ; le navigateur renvoie une erreur si une URL invalide est saisie.</p>

<div class="note">
  <p><strong>Note :</strong> ce n'est pas parce qu'une URL est bien formée qu'elle pointe vers un emplacement qui existe réellement.</p>
</div>

<div class="note">
<p><strong>Note :</strong> La présence de champs avec contraintes spéciales considérés comme erronés bloquent l'envoi du formulaire. De plus, leur apparence peut être adaptée afin de mettre en évidence l'erreur. Nous allons discuter de cela dans l'article <a href="/fr/docs/HTML/Formulaires/Validation_de_formulaires" title="/fr/docs/HTML/Formulaires/Validation_de_formulaire">Validation de formulaires</a>.</p>
</div>

<h3 id="Champs_texte_multilignes">Champs texte multilignes</h3>

<p>Un champ texte sur plusieurs lignes  se définit avec l'élément {{HTMLElement("textarea")}}, et non avec l'élément {{HTMLElement("input")}}.</p>

<pre class="brush: html">    &lt;textarea cols="30" rows="10"&gt;&lt;/textarea&gt;</pre>

<p>La principale différence entre un champ <code>textarea</code> et un champ monoligne est que, dans un textarea, l'utilisateur peut saisir du texte avec des sauts de ligne en dur (c'est à dire en pressant la touche <code>Retour</code>).</p>

<p><img alt="Screenshots of multi-lines text fields on several platforms." src="all-multi-lines-text-field.png"></p>

<div class="note">
<p><strong>Note :</strong> Vous trouverez un exemple de champ texte multiligne sur GitHub à l'adresse <a href="https://github.com/mdn/learning-area/blob/master/html/forms/native-form-widgets/multi-line-text-field.html">multi-line-text-field.html</a> (voir aussi <a href="https://mdn.github.io/learning-area/html/forms/native-form-widgets/multi-line-text-field.html">directement</a>). Jetez-y un coup d'œil, et remarquez que dans la plupart des navigateurs, la zone de texte est dotée d'une poignée d'étirement en bas à droite pour permettre à l'utilisateur de la redimensionner. Cette capacité de redimensionnement peut être désactivée en réglant la propriété {{cssxref("resize")}} de la zone de texte à <code>none</code> dans les CSS.</p>
</div>

<p>{{htmlelement("textarea")}} accepte également quelques attributs pour contrôler son rendu sur plusieurs lignes  (outre plusieurs autres) :</p>

<table>
 <caption>Attributs pour l'élément {{HTMLElement("textarea")}}</caption>
 <thead>
  <tr>
   <th scope="col">Nom de l'attribut</th>
   <th scope="col">Valeur par défaut</th>
   <th scope="col">Description</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td>{{htmlattrxref("cols","textarea")}}</td>
   <td><code>20</code></td>
   <td>Largeur visible de la boîte de contrôle texte, mesurée en largeurs de caractères.</td>
  </tr>
  <tr>
   <td>{{htmlattrxref("rows","textarea")}}</td>
   <td></td>
   <td>Nombre de lignes de texte visibles dans la boîte de contrôle.</td>
  </tr>
  <tr>
   <td>{{htmlattrxref("wrap","textarea")}}</td>
   <td><code>soft</code></td>
   <td>Indique comment le contrôle va à la ligne. Les valeurs possibles sont : <code>hard</code> ou <code>soft</code></td>
  </tr>
 </tbody>
</table>

<p>Notez que l'élément {{HTMLElement("textarea")}} est écrit un peu différemment de l'élément {{HTMLElement("input")}}. Ce dernier est un élément vide, ce qui signifie qu'il ne peut pas contenir d'élément enfant. A contrario, l'élément {{HTMLElement("textarea")}} est un élément régulier pouvant contenir des enfants contenus de texte.</p>

<p>Deux points clés à noter ici :</p>

<ul>
 <li>Si vous voulez définir une valeur par défaut pour un élément {{HTMLElement("input")}}, vous devez utiliser l'attribut <code>value</code> ; avec un élément {{HTMLElement("textarea")}} mettez le texte par défaut entre la balise ouvrante et la balise fermante du dit élément.</li>
 <li>Par nature, l'élément {{HTMLElement("textarea")}} n'accept que des contenus textuels ; ce qui signifie que si du contenu HTML est placé dans un élément {{HTMLElement("textarea")}} il sera restitué sous forme de texte brut.</li>
</ul>

<h2 id="Contenu_déroulant">Contenu déroulant</h2>

<p>Les widgets déroulants sont une manière simple de permettre à l'utilisateur de choisir une option parmi plusieurs sans que cela prenne trop de place dans l'interface utilisateur. HTML dispose de deux types de contenus déroulants la <strong>boîte à sélections</strong> et la <strong>boîte à complétement automatique</strong>. Dans les deux cas l'interation est identique. Une fois le contrôle activé, le navigateur affiche une liste de valeurs ouverte au choix de l'utilisateur.</p>

<h3 id="Boîte_à_sélection">Boîte à sélection</h3>

<p>Une boîte à sélection est créée avec l'élément {{HTMLElement("select")}} complétée d'un ou plusieurs éléments enfants {{HTMLElement("option")}} définissant les valeurs possibles.</p>

<pre class="brush: html">    &lt;select&gt;
      &lt;option&gt;Banane&lt;/option&gt;
      &lt;option&gt;Cerise&lt;/option&gt;
      &lt;option&gt;Citron&lt;/option&gt;
    &lt;/select&gt;</pre>

<p>Si nécessaire, la valeur par défaut de la boîte de sélection peut être définie en utilisant l'attribut {{htmlattrxref("selected","option")}} dans l'élément {{HTMLElement("option")}} désiré. Les éléments {{HTMLElement("option")}} peuvent être imbriqués dans des éléments {{HTMLElement("optgroup")}} pour créer des groupes de valeurs associées :</p>

<pre class="brush: html">    &lt;select&gt;
      &lt;optgroup label="Fruits"&gt;
        &lt;option&gt;Banane&lt;/option&gt;
        &lt;option selected&gt;Cerise&lt;/option&gt;
        &lt;option&gt;Citron&lt;/option&gt;
      &lt;/optgroup&gt;
      &lt;optgroup label="Légumes"&gt;
        &lt;option&gt;Carotte&lt;/option&gt;
        &lt;option&gt;Aubergine&lt;/option&gt;
        &lt;option&gt;Pomme de terre&lt;/option&gt;
      &lt;/optgroup&gt;
    &lt;/select&gt;</pre>

<p><img alt="Screenshots of single line select box on several platforms." src="all-select.png"></p>

<p>Si un élément {{HTMLElement("option")}} est défini avec l'attribut <code>value</code>, la valeur de cet attribut est envoyée lorsque le formulaire est soumis. Si l'attribut <code>value</code> est omis, le contenu de l'élément {{HTMLElement("option")}} est utilisé comme valeur de la boîte de sélection.</p>

<p>Sur l'élément {{HTMLElement("optgroup")}}, l'attribut <code>label</code> est affiché avant les valeurs, mais même s'il ressemble un peu à une option, il n'est pas sélectionnable.</p>

<h3 id="Boîte_à_sélections_multiples">Boîte à sélections multiples</h3>

<p>Par défaut, une boîte de sélection ne permet à l'utilisateur de ne sélectionner qu'une seule valeur. En ajoutant l'attribut {{htmlattrxref("multiple","select")}} à l'élément {{HTMLElement("select")}}, l'utilisateur peut sélectionner plusieurs valeurs en utilisant le mécanisme par défaut du système d'exploitation (par ex. en pressant <kbd>Cmd</kbd>/<kbd>Ctrl</kbd> et en cliquant sur plusieur valeurs).</p>

<p>Dans ce cas toutefois, la boîte d'utilisateur n'affiche plus les valeurs sous forme d'un menu déroulant. Les valeurs sont toutes affichées dans une liste.</p>

<pre class="brush: html">    &lt;select multiple&gt;
      &lt;option&gt;Banane&lt;/option&gt;
      &lt;option&gt;Cerise&lt;/option&gt;
      &lt;option&gt;Citron&lt;/option&gt;
    &lt;/select&gt;</pre>

<p><img alt="Screenshots of multi-lines select box on several platforms." src="all-multi-lines-select.png"></p>

<div class="note">
  <p><strong>Note :</strong> tous les navigateurs prenant en charge l'élément {{HTMLElement("select")}} prennent aussi en charge l'attribut {{htmlattrxref("multiple","select")}} sur lui.</p>
</div>

<h3 id="Contenus_auto-complétés">Contenus auto-complétés</h3>

<p>Vous pouvez suggérer des valeurs d'auto-complémentation pour les widgets avec un élément {{HTMLElement("datalist")}} accompagné d'éléments enfants {{HTMLElement("option")}} précisant les valeurs à afficher.</p>

<p>La liste de données est alors liée à un champ texte (généralement un élément <code>input</code>) avec l'attribut {{htmlattrxref("list","input")}}.</p>

<p>Une fois la liste de données affiliée au widget de formulaire, ses options s'utilisent comme complémentation du texte saisi par l'utilisateur ; cela se présente généralement à l'utilisateur sous forme d'une boîte déroulante listant des correspondances possibles avec ce qui doit être saisi dans la boîte.</p>

<pre class="brush: html">    &lt;label for="onFruit"&gt;Quel est votre fruit préféré ?&lt;/label&gt;
    &lt;input type="text" id="onFruit" list="maSuggestion" /&gt;
    &lt;datalist id="maSuggestion"&gt;
      &lt;option&gt;Pomme&lt;/option&gt;
      &lt;option&gt;Banane&lt;/option&gt;
      &lt;option&gt;Mûre&lt;/option&gt;
      &lt;option&gt;Airelles&lt;/option&gt;
      &lt;option&gt;Citron&lt;/option&gt;
      &lt;option&gt;Litchi&lt;/option&gt;
      &lt;option&gt;Pêche&lt;/option&gt;
      &lt;option&gt;Poire&lt;/option&gt;
    &lt;/datalist&gt;</pre>

<div class="note">
  <p><strong>Note :</strong> Selon la <a href="http://www.w3.org/TR/html5/common-input-element-attributes.html#attr-input-list" rel="external">norme HTML</a>, l'attribut {{htmlattrxref("list","input")}} et l'élément {{HTMLElement("datalist")}} peuvent s'utiliser avec tout type de widget nécessitant une saisie utilisateur. Toutefois, les modalités de ce fonctionnement ne sont pas claire pour des contrôles autres que textuels (de couleur ou de date par ex.) et les divers navigateurs se comporteront de manière différente selon le cas. Pour cette raison, soyez prudent en utilisant cette fonctionnalité avec autre chose que des champs textuels.</p>
</div>

<div><img alt="Screenshots of datalist on several platforms." src="all-datalist.png"></div>

<div>
<h4 id="Prise_en_charge_de_Datalist_et_recours">Prise en charge de Datalist et recours</h4>

<p>L'élément {{HTMLElement("datalist")}} est un ajout très récent aux formulaires HTML, donc sa prise en charge par les navigateurs est un peu plus limitée que ce que nous avons vu précédemment. En particulier, il n'est pas pris en charge dans les versions d'IE inférieures à 10, et Safari ne le prend toujours pas en charge au moment de la rédaction de cet article.</p>

<p>Pour gérer cela, voici une petite astuce offrant une bonne solution de repli pour ces navigateurs :</p>

<pre class="brush:html">&lt;label for="myFruit"&gt;Quel est votre fruit préféré ? (avec repli)&lt;/label&gt;
&lt;input type="text" id="myFruit" name="fruit" list="fruitList"&gt;

&lt;datalist id="fruitList"&gt;
  &lt;label for="suggestion"&gt;ou choisissez un fruit&lt;/label&gt;
  &lt;select id="suggestion" name="altFruit"&gt;
    &lt;option&gt;Pomme&lt;/option&gt;
    &lt;option&gt;Banane&lt;/option&gt;
    &lt;option&gt;Mûres&lt;/option&gt;
    &lt;option&gt;Airelles&lt;/option&gt;
    &lt;option&gt;Citron&lt;/option&gt;
    &lt;option&gt;Litchi&lt;/option&gt;
    &lt;option&gt;Pêche&lt;/option&gt;
    &lt;option&gt;Poire&lt;/option&gt;
  &lt;/select&gt;
&lt;/datalist&gt;</pre>

<p>Les navigateurs qui prennent en charge l'élément {{HTMLElement("datalist")}} ignoreront tous les éléments qui ne sont pas {{HTMLElement("option")}} et fonctionneront comme prévu. D'autre part, les navigateurs qui ne prennent pas en charge l'élément {{HTMLElement("datalist")}} afficheront l'étiquette et la boîte de sélection. Bien sûr, il y a d'autres façons de gérer ce manque de prise en charge de l'élément {{HTMLElement("datalist")}}, mais c'est la manière la plus simple (d'autres ont besoin de JavaScript).</p>

<table>
 <tbody>
  <tr>
   <th scope="row">Safari 6</th>
   <td><img alt="Screenshot of the datalist element fallback with Safari on Mac OS" src="https://developer.mozilla.org/files/4583/datalist-safari.png"></td>
  </tr>
  <tr>
   <th scope="row">Firefox 18</th>
   <td><img alt="Screenshot of the datalist element with Firefox on Mac OS" src="https://developer.mozilla.org/files/4581/datalist-firefox-macos.png"></td>
  </tr>
 </tbody>
</table>
</div>

<h2 id="Éléments_à_cocher">Éléments à cocher</h2>

<p>Les éléments à cocher sont des widgets dont l'état se modifie en cliquant sur eux. Il existe deux types d'éléments à cocher : la case à cocher et le bouton radio. Les deux utilisent l'attribut {{htmlattrxref("checked","input")}} pour indiquer si le widget est coché par défaut ou non.</p>

<p>Il est important de noter que ces widgets ne se comportent pas tout à fait comme les autres widgets de formulaires. Pour la plupart des widgets, une fois que le formulaire est envoyé, tous les widgets dont l'attribut {{htmlattrxref("name","input")}} est défini sont envoyés, même s'ils ne sont pas renseignés. Dans le cas des éléments à cocher, leurs valeurs ne sont envoyées que s'ils sont cochés. S'ils ne sont pas cochés, rien n'est envoyé, pas même la valeur de leur attribut <code>name</code>.</p>

<div class="note">
<p><strong>Note :</strong> Vous trouverez les exemples de cette section sur GitHub à l'adresse <a href="https://github.com/mdn/learning-area/blob/master/html/forms/native-form-widgets/checkable-items.html">checkable-items.html</a> (<a href="https://mdn.github.io/learning-area/html/forms/native-form-widgets/checkable-items.html">voir directement aussi</a>).</p>
</div>

<p>Pour un maximum de convivialité/accessibilité, il est conseillé d'entourer chaque liste d'éléments liés dans un {{htmlelement("fieldset")}}, avec un élément {{htmlelement("legend")}} fournissant une description globale de la liste.  Chaque paire individuelle d'éléments {{htmlelement("label")}}/{{htmlelement("input")}} doit être contenue dans son propre élément de liste (ou similaire), comme le montrent les exemples.</p>

<p>Vous devez également fournir des valeurs pour ces types d'entrées dans l'attribut <code>value</code> si vous voulez qu'elles aient un sens — si aucune valeur n'est fournie, les cases à cocher et les boutons radio ont la valeur <code>on</code>.</p>

<h3 id="Case_à_cocher">Case à cocher</h3>

<p>Une casce à cocher se crée avec l'élément {{HTMLElement("input")}} dont l'attribut {{htmlattrxref("type","input")}} a pour valeur <code>checkbox</code>.</p>

<pre class="brush: html">    &lt;input type="checkbox" checked id="carrots" name="carrots" value="carrots"&gt;
</pre>

<p>Mettre l'attribut <code>checked</code> fait que la case sera cochée au chargement de la page.</p>

<p><img alt="Screenshots of check boxes on several platforms." src="all-checkbox.png"></p>

<h3 id="Bouton_radio">Bouton radio</h3>

<p>Un bouton radio se crée avec un élément {{HTMLElement("input")}} dont l'attribut {{htmlattrxref("type","input")}} a la valeur <code>radio</code>.</p>

<pre class="brush: html">    &lt;input type="radio" checked id="soup" name="meal"&gt;</pre>

<p>Plusieurs boutons radio peuvent être liés ensemble. S'ils partagent la même valeur pour leur attribut {{htmlattrxref("name","input")}}, ils seront considérés comme faisant partie d'un seul groupe de boutons. Seulement un bouton à la fois peut être coché par groupe. Ceci signifie que si l'un d'entre eux est coché, tous les autres sont automatiquement décochés. Lorsque le formulaire est envoyé, seule la valeur du bouton coché est envoyée. Si aucun des boutons n'est coché, l'ensemble des boutons du groupe est considéré comme étant dans un état inconnu et aucune valeur n'est envoyée avec le formulaire.</p>

<pre class="brush: html">&lt;fieldset&gt;
  &lt;legend&gt;Quel est votre mets préféré ?&lt;/legend&gt;
  &lt;ul&gt;
    &lt;li&gt;
      &lt;label for="soup"&gt;Soupe&lt;/label&gt;
      &lt;input type="radio" checked id="soup" name="meal" value="soup"&gt;
    &lt;/li&gt;
    &lt;li&gt;
      &lt;label for="curry"&gt;Curry&lt;/label&gt;
      &lt;input type="radio" id="curry" name="meal" value="curry"&gt;
    &lt;/li&gt;
    &lt;li&gt;
      &lt;label for="pizza"&gt;Pizza&lt;/label&gt;
      &lt;input type="radio" id="pizza" name="meal" value="pizza"&gt;
    &lt;/li&gt;
  &lt;/ul&gt;
&lt;/fieldset&gt;</pre>

<p><img alt="Screenshots of radio buttons on several platforms." src="all-radio.png"></p>

<h2 id="Boutons">Boutons</h2>

<p>Dans les formulaires HTML, il existe trois types de boutons :</p>

<dl>
 <dt>Submit</dt>
 <dd>Envoie les données du formulaire au serveur.</dd>
 <dt>Reset</dt>
 <dd>Réinitialise les widgets de formulaire à leurs valeurs par défaut.</dd>
 <dt>Anonymous</dt>
 <dd>Type de bouton n'ayant pas d'effet prédéfini mais qui peut être personnalisé grâce à du code JavaScript.</dd>
</dl>

<p>Un bouton se crée avec un élément {{HTMLElement("button")}} ou un élément {{HTMLElement("input")}}. C'est la valeur de l'attribut {{htmlattrxref("type","input")}} qui définit le type de bouton affiché :</p>

<h3 id="submit">submit</h3>

<pre class="brush: html">    &lt;button type="submit"&gt;
        Ceci est un &lt;br&gt;&lt;strong&gt;bouton d'envoi&lt;/strong&gt;
    &lt;/button&gt;

    &lt;input type="submit" value="Ceci est un bouton d'envoi"&gt;</pre>

<h3 id="reset">reset</h3>

<pre class="brush: html">    &lt;button type="reset"&gt;
        Ceci est un &lt;br&gt;&lt;strong&gt;bouton de réinitialisation&lt;/strong&gt;
    &lt;/button&gt;

    &lt;input type="reset" value="Ceci est un bouton de réinitialisation"&gt;</pre>

<h3 id="anonymous">anonymous</h3>

<pre class="brush: html">    &lt;button type="button"&gt;
        Ceci est un &lt;br&gt;&lt;strong&gt;bouton lambda&lt;/strong&gt;
    &lt;/button&gt;

    &lt;input type="button" value="Ceci est un bouton lambda"&gt;</pre>

<p>Les boutons se comportent de la même manière que vous utilisiez l'élément {{HTMLElement("button")}} ou l'élément {{HTMLElement("input")}}. Il existe toutefois quelques différences à noter :</p>

<ul>
 <li>Comme on peut le voir dans l'exemple précédent, les éléments {{HTMLElement("button")}} autorisent l'utilisation de contenu HTML dans l'étiquette, tandis que les éléments {{HTMLElement("input")}} n'acceptent que du texte brut.</li>
 <li>Dans le cas des éléments {{HTMLElement("button")}}, il est possible d'avoir une valeur différente de l'étiquette du bouton (toutefois, ceci ne peut être utilisé pour les versions antérieures à la version 8 d'Internet Explorer).</li>
</ul>

<p><img alt="Screenshots of buttons on several platforms." src="all-buttons.png"></p>

<p>Techniquement parlant, il n'y a pratiquement pas de différence entre un bouton défini avec l'élément {{HTMLElement("button")}} ou l'élément {{HTMLElement("input")}}. La seule différence à noter réside dans l'étiquette du bouton lui-même. Dans un élément {{HTMLElement("input")}}, l'étiquette ne peut être constituée que de données de type caractère, alors que dans un élément {{HTMLElement("button")}}, l'étiquette peut être mise sous HTML, de sorte qu'elle peut être mise en forme en conséquence.</p>

<h2 id="Widgets_de_formulaires_avancés">Widgets de formulaires avancés</h2>

<p>Ces widgets sont des contrôles permettant l'utilisateur de saisir des données plus complexes ou moins habituelles, comme des nombres exacts ou approchés, des dates et heures ainsi que des couleurs.</p>

<h3 id="Nombres">Nombres</h3>

<p>On crée un widget pour nombres avec un élément {{HTMLElement("input")}} dont l'attribut {{htmlattrxref("type","input")}} a pour valeur <code>number</code>. Ce contrôle ressemble à un champ texte mais il n'accepte que des chiffres en virgule flottante, et propose habituellement des boutons pour augmenter ou réduire la valeur dans le widget.</p>

<p>Il est aussi possible de :</p>

<ul>
 <li>contraindre la valeur en définissant les attributs {{htmlattrxref("min","input")}} et {{htmlattrxref("max","input")}}.</li>
 <li>définir l'incrément de modification de la valeur du widget à l'aide des boutons ad‑hoc en précisant l'attribut {{htmlattrxref("step","input")}}.</li>
</ul>

<h4 id="Exemple">Exemple</h4>

<pre class="brush: html">    &lt;input type="number" name="age" id="age" min="1" max="10" step="2"&gt;</pre>

<p>Ceci créé un widget pour un nombre dont la valeur est comprise entre 1 et 10 et dont les boutons d'incrémentation/décrémentation modifient la valeur par pas de 2.</p>

<h3 id="Curseurs">Curseurs</h3>

<p>Le curseur est une autre manière de sélectionner un nombre. Comme, visuellement parlant, les curseurs sont moins précis qu'un champ textuel, ils sont utilisés pour retenir un nombre dont la précision de valeur n'est pas primordiale.</p>

<p>Un curseur se crée avec l'élément {{HTMLElement("input")}} dont l'attribut {{htmlattrxref("type","input")}} a pour valeur <code>range</code>. Il est important de configurer convenablement le curseur. À cet effet, il est fortement recommandé de définir les attributs {{htmlattrxref("min","input")}}, {{htmlattrxref("max","input")}} et {{htmlattrxref("step","input")}}.</p>

<h4 id="Exemple_2">Exemple</h4>

<pre class="brush: html">&lt;input type="range" name="beans" id="beans" min="0" max="500" step="10"&gt;</pre>

<p>Cet exemple créé un curseur dont les valeurs varient entre 0 et 500, et dont les bouton d'incrément/décrément font varier la valeur de ±10.</p>

<p>Un problème avec les curseurs est qu'il n'offrent aucun moyen visue de savoir quelle est leur valeur courante. Il est nécessaire d'ajouter cela vous‑même à l'aide de JavaScript, mais c'est assez facile. Dans cet exemple nous ajoutons un élément {{htmlelement("span")}} dans lequel nous écrivons la valeur courante du curseur et la mettons à jour quand elle est modifiée.</p>

<pre class="brush: html">&lt;label for="beans"&gt;Combien de haricots pouvez‑vous manger ?&lt;/label&gt;
&lt;input type="range" name="beans" id="beans" min="0" max="500" step="10"&gt;
&lt;span class="beancount"&gt;&lt;/span&gt;</pre>

<p>et en  JavaScript :</p>

<pre class="brush: js">var beans = document.querySelector('#beans');
var count = document.querySelector('.beancount');

count.textContent = beans.value;

beans.oninput = function() {
  count.textContent = beans.value;
}</pre>

<p>Ici nous stockons dans deux variables les références du curseur et celle de <code>span</code>, puis nous réglons immédiatement le <code><a href="/fr/docs/Web/API/Node/textContent">textContent</a></code>  de <code>span</code> à la valeur courante <code>value</code> de l'entrée. Enfin, nous avons mis en place un gestionnaire d'événements oninput de sorte que chaque fois que le curseur de plage est déplacé, le <code>textContent</code> de <code>span</code> est mis à jour avec la nouvelle valeur de l'entrée.</p>

<p>L'attribut <code>range</code> pour <code>input</code> n'est pas pris en charge dans les versions d'Internet Explorer dont le numéro est inférieur à 10.</p>

<h3 id="Sélection_de_date_et_heure">Sélection de date et heure</h3>

<p>Recueillir des données de date et heure a traditionnellement toujours été un cauchemar pour les développeurs web. HTML5 ajoute des améliorations en ajoutant un contrôle qui permet de manipuler ce type de données.</p>

<p>Un contrôle de sélection de date et heure se crée avec l'élément {{HTMLElement("input")}} et une valeur appropriée de l'attribut {{htmlattrxref("type","input")}} selon que vous voulez recueillir des dates, des heures ou les deux.</p>

<h4 id="datetime-local"><code>datetime-local</code></h4>

<p>Cette valeur d'attribut créé un widget pour afficher et sélectionner une date et une heure quelque soit le fuseau horaire.</p>

<pre class="brush: html">&lt;input type="datetime-local" name="datetime" id="datetime"&gt;</pre>

<h4 id="month"><code>month</code></h4>

<p>Cette valeur d'attribut créé un widget pour afficher et sélectionner un mois dans une année donnée.</p>

<pre class="brush: html">&lt;input type="month" name="month" id="month"&gt;</pre>

<h4 id="time"><code>time</code></h4>

<p>Cette valeur d'attribut créé un widget pour afficher et sélectionner un horaire.</p>

<pre class="brush: html">&lt;input type="time" name="time" id="time"&gt;</pre>

<h4 id="week"><code>week</code></h4>

<p>Cette valeur d'attribut crée un widget pour afficher et sélectionner une semaine et l'année correspondante.</p>

<pre class="brush: html">&lt;input type="week" name="week" id="week"&gt;</pre>

<p>Tous les contrôles de sélection de date et heure peuvent être contraints à l'aide des attributs {{htmlattrxref("min","input")}} et {{htmlattrxref("max","input")}}.</p>

<pre class="brush: html">    &lt;label for="maDate"&gt;Quand êtes vous disponible cet été ?&lt;/label&gt;
    &lt;input type="date" min="2013-06-01" max="2013-08-31" id="maDate"&gt;</pre>

<div class="warning">
  <p><strong>Attention :</strong> Les widgets de date et heure sont encore peu pris en charge. Au moment de la rédaction de cet article, Chrome, Edge et Opera les prennent bien en charge, mais il n'y a pas de prise en charge dans Internet Explorer et Firefox et Safari n'ont qu'une prise en charge lacunaire de ces derniers.</p>
</div>

<h3 id="Sélecteur_de_couleur">Sélecteur de couleur</h3>

<p>Les couleurs sont toujours compliquées à manier. Il existe plusieurs façons de les exprimer : valeurs RGB (décimale ou hexadécimale), valeurs HSL, mots-clés, etc. Les widgets de sélection de couleur permettent aux utilisateurs de sélectionner une couleur dans un contexte textuel et visuel.</p>

<p>Un widget de sélection de couleur se crée avec un élément {{HTMLElement("input")}} dont l'attribut {{htmlattrxref("type","input")}} a pour valeur <code>color</code>.</p>

<pre class="brush: html">&lt;input type="color" name="color" id="color"&gt;</pre>

<p>Attention : la prise en charge du widget <code>color</code> n'est pas très bonne actuellement. Il n'y a aucune prise en charge dans Internet Explorer, ni actuellement dans Safari. Les autres navigateurs majeurs le prennent en charge.</p>

<h2 id="Autres_widgets">Autres widgets</h2>

<p>Il existe d'autres types de widgets qui ne peuvent pas être classés facilement à cause de leur comportement très particulier, mais qui sont toujours très utiles.</p>

<div class="note">
<p><strong>Note :</strong> Vous trouverez les exemples de cette section sur GitHub à l'adresse <a href="https://github.com/mdn/learning-area/blob/master/html/forms/native-form-widgets/other-examples.html">other-examples.html</a> (à voir aussi<a href="https://mdn.github.io/learning-area/html/forms/native-form-widgets/other-examples.html"> directement</a>).</p>
</div>

<h3 id="Sélection_de_fichier_2">Sélection de fichier</h3>

<p>Les formulaires HTML permettent d'envoyer des fichiers à un serveur. Cette action spécifique est détaillée dans l'article  « <a href="/fr/docs/Web/Guide/HTML/Formulaires/Envoyer_et_extraire_les_données_des_formulaires" title="/fr/docs/HTML/Formulaires/Envoyer_et_extraire_les_données_des_formulaires">Envoi et extraction des données de formulaire</a> ». Le widget de sélection de fichier permet à l'utilisateur de choisir un ou plusieurs fichiers à envoyer.</p>

<p>Pour créer un widget de sélection de fichier, vous devez utiliser un élément {{HTMLElement("input")}} dont l'attribut {{htmlattrxref("type","input")}} a pour valeur <code>file</code>. Les types de fichiers acceptés peuvent être contraints en utilisant l'attribut {{htmlattrxref("accept","input")}}. De plus, si vous souhaitez permettre à l'utilisateur de choisir plusieurs fichiers, vous pouvez le faire en ajoutant l'attribut {{htmlattrxref("multiple","input")}}.</p>

<h4 id="Exemple_3">Exemple</h4>

<p>Dans cet exemple, le widget de sélection de fichiers permet de sélectionner des fichiers d'images. L'utilisateur peut sélectionner plusieurs fichiers.</p>

<pre class="brush: html">&lt;input type="file" name="file" id="file" accept="image/*" multiple&gt;</pre>

<h3 id="Contenu_caché">Contenu caché</h3>

<p>Il est parfois pratique pour des raisons techniques d'avoir des morceaux d'informations qui soient envoyés au serveur sans être montrées à l'utilisateur. Pour ce faire, vous pouvez ajouter un élément invisible dans votre formulaire. Cela est possible en utilisant un élément {{HTMLElement("input")}} dont l'attribut {{htmlattrxref("type","input")}} a pour valeur <code>hidden</code>.</p>

<p>Si vous créez un tel élément, il est obligatoire de définir ses attributs <code>name</code> et <code>value</code> :</p>

<pre class="brush: html">    &lt;input type="hidden" id="timestamp" name="timestamp" value="1286705410"&gt;</pre>

<h3 id="Image-bouton">Image-bouton</h3>

<p>Le contrôle <strong>image-bouton</strong> est affiché comme un élément {{HTMLElement("img")}}, à la différence que lorsque l'utilisateur clique dessus, il se comporte comme un bouton d'envoi (voir ci-dessus).</p>

<p>Une image-bouton se crée avec un élément {{HTMLElement("input")}} dont l'attribut {{htmlattrxref("type","input")}} a pour valeur <code>image</code>. Cet élément accepte exactement le même ensemble d'attributs que l'élément {{HTMLElement("img")}}, en plus de tous les attributs valides pour n'importe quel bouton de formulaire.</p>

<pre class="brush: html">    &lt;input type="image" alt="Click me!" src="my-img.png" width="80" height="30" /&gt;</pre>

<p>Si l'image-bouton est utilisée pour envoyer un formulaire, ce widget n'envoie pas sa valeur mais les coordonnées X et Y du clic sur l'image (les coordonnées sont relatives à l'image, ce qui veut dire que le coin supérieur gauche représente les coordonnées 0, 0). Les coordonnées sont envoyées sous la forme de deux paires de clé/valeur :</p>

<ul>
 <li>la valeur X est la valeur de l'attribut {{htmlattrxref("name","input")}} suivie de la chaîne « <em>.x</em> »</li>
 <li>la valeur Y est la valeur de l'attribut {{htmlattrxref("name","input")}} suivie de la chaîne « <em>.y</em> ».</li>
</ul>

<p>Lorsque vous cliquez sur l'image dans ce formulaire, vous êtes redirigés une URL du type suivant :</p>

<pre>    http://foo.com?pos.x=123&amp;pos.y=456</pre>

<p>C'est une façon très commode de construire une « hot map » (cartographie des parties d'une page Internet le plus souvent balayées par le regard des lecteurs). La manière d'envoyer et d'extraire ces valeurs est détaillée dans l'article « <a href="/fr/docs/Web/Guide/HTML/Formulaires/Envoyer_et_extraire_les_données_des_formulaires" title="/fr/docs/HTML/Formulaires/Envoyer_et_extraire_les_données_des_formulaires">Envoi des données de formulaire</a> ».</p>

<h3 id="Compteurs_et_barres_de_progression">Compteurs et barres de progression</h3>

<p>Les compteurs et barres de progressions sont des représentations visuelles de valeurs numériques.</p>

<h4 id="Progress">Progress</h4>

<p>Une barre de progression représente une valeur qui évolue dans le temps jusqu'à une valeur maximale définie par l'attribut {{htmlattrxref("max","progress")}}. Une telle barre peut être créée grace à un élément {{ HTMLElement("progress")}}.</p>

<pre class="brush: html">    &lt;progress max="100" value="75"&gt;75/100&lt;/progress&gt;</pre>

<p>Cela sert à mettre en œuvre visuellement un rapport d'avancement, comme le pourcentage du nombre total de fichiers téléchargés ou le nombre de questions posées dans un questionnaire.</p>

<p>Le contenu dans l'élément {{HTMLElement("progress")}} est un affichage informatif de repli pour les navigateurs ne prenant pas en charge cet élément ;  les technologies d'assistance vocalisent ce contenu.</p>

<h4 id="Meter">Meter</h4>

<p>Un étalon est une valeur fixe dans une plage délimitée par une valeur minimale {{htmlattrxref("min","meter")}} et une valeur maximale {{htmlattrxref("max","meter")}}. Cette valeur est affichée dans une barre, et pour savoir à quoi cette barre ressemble, nous comparons certaines valeurs :</p>

<ul>
 <li>les valeurs {{htmlattrxref("low","meter")}} et {{htmlattrxref("high","meter")}} divisent l'intervalle en trois parties :
  <ul>
   <li>la partie basse de l'intervalle est comprise entre les valeurs {{htmlattrxref("min","meter")}} et {{htmlattrxref("low","meter")}} (les deux valeurs sont incluses)</li>
   <li>la partie médiane de l'intervalle est comprise entre les valeurs {{htmlattrxref("low","meter")}} et {{htmlattrxref("high","meter")}} (les deux valeurs sont exclues)</li>
   <li>la partie haute de l'intervalle est comprise entre les valeurs {{htmlattrxref("high","meter")}} et {{htmlattrxref("max","meter")}} (les deux valeurs sont incluses)</li>
  </ul>
 </li>
 <li>La valeur {{htmlattrxref("optimum","meter")}} définit la valeur optimale pour l'élément {{HTMLElement("meter")}}. En conjonction avec les valeurs {{htmlattrxref("low","meter")}} et {{htmlattrxref("high","meter")}}, elle définit quelle partie de la plage est préféré :
  <ul>
   <li>Si la valeur {{htmlattrxref("optimum","meter")}} est dans la partie basse de l'intervalle, la partie basse est considérée comme la partie préférée, la partie médiane est considérée comme la partie moyenne et la partie haute comme la moins favorable.</li>
   <li>Si la valeur {{htmlattrxref("optimum","meter")}} est dans la partie médiane, la partie basse est considérée comme la partie moyenne, la partie médiane comme la partie préférée et la partie haute comme moyenne également.</li>
   <li>Si la valeur {{htmlattrxref("optimum","meter")}} est dans la partie haute, la partie basse est considérée comme la moins favorable, la partie médiane comme moyenne et la partie haute comme la partie préférée.</li>
  </ul>
 </li>
</ul>

<p>Tous les navigateurs compatibles avec l'élément {{HTMLElement("meter")}} utilisent ces valeurs pour modifier la couleur de la barre :</p>

<ul>
 <li>Si la valeur actuelle est dans la partie préférée, la barre est verte.</li>
 <li>Si la valeur actuelle est dans la partie moyenne, la barre est jaune.</li>
 <li>Si la valeut actuelle est dans la partie la moins favorable, la barre est rouge.</li>
</ul>

<p>Une telle barre se crée avec un élément {{HTMLElement("meter")}}. Cela permet d'implémenter toute sorte d'étalonnage, par exemple une barre montrant l'espace total utilisé sur un disque, qui devient rouge si le disque commence à être plein.</p>

<pre class="brush: html">&lt;meter min="0" max="100" value="75" low="33" high="66" optimum="50"&gt;75&lt;/meter&gt;</pre>

<p>Le contenu de l'élément {{HTMLElement("meter")}} est un affichage informatif de repli pour les navigateurs ne prenant pas en charge cet élément ; les technologies d'assistance vocalisent cet affichage.</p>

<p>La prise en charge de <code>progress</code> et <code>meter</code> est vraiment bonne — il n'y a pas de prise en charge dans Internet Explorer, mais les autres navigateurs l'acceptent bien.</p>

<h2 id="Conclusion">Conclusion</h2>

<p>Comme nous venons de le voir, il y a pas mal d'éléments de formulaire différents disponibles  — il n'est pas nécessaire de mémoriser l'ensemble de ces détails dès maintenant, mais vous pourrez revenir à cet article tant que vous le voudrez pour revoir tel ou tel détail.</p>

<h2 id="Voir_également">Voir également</h2>

<p>Pour entrer plus en détails des différents widgets de formulaires, voici quelques ressources externes très utiles que vous pouvez visiter :</p>

<ul>
 <li><a href="http://wufoo.com/html5/" rel="external">L'état actuelle des formulaires HTML5</a> par Wufoo (en anglais)</li>
 <li><a href="http://www.quirksmode.org/html5/inputs.html" rel="external">Tests HTML5 - inputs</a> sur Quirksmode (en anglais) (et <a href="http://www.quirksmode.org/html5/inputs_mobile.html" rel="external">pour les navigateurs mobiles</a>)</li>
</ul>

<p>{{PreviousMenuNext("Web/Guide/HTML/Formulaires/Comment_structurer_un_formulaire_HTML", "Web/Guide/HTML/Formulaires/Envoyer_et_extraire_les_données_des_formulaires", "Web/Guide/HTML/Formulaires")}}</p>

<h2 id="Dans_ce_module">Dans ce module</h2>

<ul>
 <li><a href="/fr/docs/Web/Guide/HTML/Formulaires/Mon_premier_formulaire_HTML">Mon premier formulaire HTML</a></li>
 <li><a href="/fr/docs/Web/Guide/HTML/Formulaires/Comment_structurer_un_formulaire_HTML">Comment structurer un formulaire HTML</a></li>
 <li>Les widgets natifs pour formulaire</li>
 <li><a href="/fr/docs/Web/Guide/HTML/Formulaires/Envoyer_et_extraire_les_données_des_formulaires">Envoi des données de formulaire</a></li>
 <li><a href="/fr/docs/Web/Guide/HTML/Formulaires/Validation_donnees_formulaire">Validation des données de formulaire</a></li>
 <li><a href="/fr/docs/Web/Guide/HTML/Formulaires/Comment_construire_des_widgets_de_formulaires_personnalisés">Comment construire des widgets personnalisés pour formulaire</a></li>
 <li><a href="/fr/docs/Web/Guide/HTML/Formulaires/Sending_forms_through_JavaScript">Envoi de formulaires à l'aide du JavaScript</a></li>
 <li><a href="/fr/docs/Web/Guide/HTML/Formulaires/HTML_forms_in_legacy_browsers">Formulaires HTML dans les navigateurs anciens</a></li>
 <li><a href="/fr/docs/Web/Guide/HTML/Formulaires/Apparence_des_formulaires_HTML">Mise en forme des formulaires HTML</a></li>
 <li><a href="/fr/docs/Web/Guide/HTML/Formulaires/Advanced_styling_for_HTML_forms">Mise en forme avancée des formulaires HTML</a></li>
 <li><a href="/fr/docs/Web/Guide/HTML/Formulaires/Property_compatibility_table_for_form_widgets">Table de compatibilité des propriétés pour les widgets de formulaire</a></li>
</ul>