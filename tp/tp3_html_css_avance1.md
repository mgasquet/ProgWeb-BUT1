---
title: TP3 &ndash; HTML / CSS avancé 1/2
subtitle: structuration et stylisation, block & inline, combinaison de sélecteurs
layout: tutorial
---

Nous allons continuer de modifier notre site et l'objectif de cette séance est de contruire une seconde page et d'obtenir le [rendu suivant]({{site.baseurl}}/assets/target_tp3.png) pour notre page principale.

Pour ce troisième TP, allez dans le dossier `Dev_Web` puis **copiez** et **collez** le contenu de votre dossier `TP2` dans un nouveau dossier nommé `TP3`.
C'est dans ce dossier que vous travaillerez durant ce TP. 

La spécification HTML5 propose différentes manières de classer les
balises/éléments selon leurs caractéristiques
([Liste des balises par catégorie](https://developer.mozilla.org/en-US/docs/Web/Guide/HTML/Content_categories)). Nous
allons ici nous intéresser à deux types spécifiques :

* les balises de structure : elles permettent de délimiter l'articulation
  logique de la page web en la découpant en différentes sections. Nous y
  consacrerons la prochaine section.

* les balises au niveau du texte : elles apportent une précision sur la
  sémantique d'une partie du texte (mise en avant d'une partie de texte
  importante, ajout d'un type exposant, time,...).

  Voici quelques exemples de balises au niveau du texte :

  * `<sup>` : un exposant
  * `<time>` : mise en valeur d'une date
  * `<em>` : emphase sur du texte
  * `<strong>` : on rajoute de l'importance à un texte
  * `<br>` : saut de ligne


  Ces balises au niveau du texte sont souvent naturellement liées à un style
  associé (les `<em>` seront stylisées par une mise en italique, les `<sup>` en
  exposants,...).  Les navigateurs se chargent d'ajouter pour nous certains
  styles par défaut très courant.

Il existe encore beaucoup d'autres balises HTML. Cela dit, il arrive qu'aucune
ne corresponde à ce que l'on veut exprimer (lors d'une construction de layout
par exemple). Deux balises neutres ont été ajoutées pour ces constructions :

   * Au niveau du texte `<span>` : cette balise est neutre, sans signification
     particulière. Son utilisation permet entre autres de créer des règles de
     formatage spécifiques du contenu textuel.
   * Balise de structure `<div>` : cette balise est neutre, son utilisation
     permet de distinguer une section qui ne revêt aucune signification
     particulière. Contrairement au `span` elle provoque un saut de ligne.

## Structuration de la page

Vous allez d'abord structurer logiquement le contenu du site. Voici un
*template* HTML (modèle HTML en français) d'une structuration classique de page
Web.


```html
<!DOCTYPE html>
<html>
    <head>...</head>
    <body>
        <header>
            ...
            <nav>...</nav>
        </header>
        <main>
            <article>...</article>
            <article>...</article>
            <aside>...</aside>
        </main>
        <footer>
            ...
        </footer>
    </body>
</html>
```

Pour fixer les idées, voici un aperçu d'une mise en page correspondante à
l'exemple précédent :

<img src="{{site.baseurl}}/assets/sections.png" alt="Structuration d'une page" style="margin: 0 auto;display: block;">

Par défaut, ces balises découpent la page web en sections horizontales qu'elles
occupent en entier (du bord gauche au bord droit de la section). Par défaut Les
balises de structure s'empilent verticalement car elles ne peuvent pas partager
une même section horizontale (donc nous devrons appliquer un style particulier
pour `<aside>`).

Expliquons le rôle de quelques balises de structure:

* `<header>` : section contenant l'en-tête affichée de la page (à ne pas
  confondre avec `<head>`, qui sont les méta-informations de la page Web)
* `<nav>` : section contenant une série de liens hypertextes pour la navigation
   sur le site
 * `<main>` : section principale de la page, celle qui contient le contenu
   spécifique à cette page. Cette balise ne peut être présente dans une autre
   balise présentée ici à l'exception de `<div>`.
   <!--
   Elle n'est pas supportée par Internet Explorer <= 10 mais le support peut en
   être ajouté grâce à Javascript et en utilisant la règle CSS « main
   -->
   <!-- {display : block} ». -->
 * `<article>` : section contenant un document « auto-suffisant », *i.e.* qui
   peut être séparé du reste de la page et gardera cependant tout son
   sens. Une page peut contenir plusieurs articles, dans le cas d'un blog par
   exemple, de commentaires, d'une page listant les publications récentes ...
 * `<aside>` : section contenant du matériel périphérique au contenu
   principal. Cela peut-être par ex. une série de liens spécifiques au document
   principal, un bandeau de publicités …
 * `<footer>` : section contenant le pied de page.
 * `<section>` : une section non spécifique, ou une sous-section d'un article,
   d'un menu... Doit typiquement commencer par un titre `<hX>`.
 * `<figure>` : une illustration (au sens large) « auto-suffisante » illustrant
   le document principal ou un article, et qui doit pouvoir être placée
   librement dans la page sans en altérer le déroulement (par ex. dans le texte,
   dans un appendice...)
 * `<h1>`- `<h6>` : titres de section
 * `<blockquote>` : une citation avec en particulier `<cite>` pour la
   référence de la citation.
 * `<p>` : paragraphes de texte
 * `<address>` : coordonnées de contact de l'auteur. Il ne peut y avoir qu'un
   bloc `<address>` par article et un pour le restant de la page



<div class="exercise">

1. Ajoutez une balise `<header>`. Son contenu sera la citation (blockquote) du TP1 et une
   barre de navigation `<nav>` vide pour l'instant,

2. Ajoutez une balise `<main>`, une balise `<article>` et une balise `<aside>`
   comme dans le *template* précédent. Mettez l'ancien contenu de la page dans
   `<article>` sauf les deux dernières sections ("Les autres écoles de sorcellerie" et
   "Top 10 des sorciers célèbres ayant fréquenté l'école") qui vont dans `<aside>`,

3. Ajoutez une balise `<footer>` qui contient le lien vers le retour au début du site,
   
4. Ajoutez dans la balise `<nav>` deux liens dans une structure de liste
   contenant : Un lien nommé "Accueil" qui pointe sur la page courante
   `index.html` et un nommé "Inscription" qui pointe vers une future page
   `inscription.html`,
   
5. Validez votre pages HTML sur le validateur
   [https://html5.validator.nu/](https://html5.validator.nu/). (Faites-le
   systématiquement sans qu'on vous le demande :-) ).

</div>
<div class="exercise">

1. Construire une page `inscription.html` au même niveau (même dossier) que `index.html`. Elle doit
   contenir le même template HTML (patron HTML) que `index.html`. En particulier:

   1. elle reprend les mêmes  `<header>` et `<footer>` que `index.html`,
   2. elle appelle la même feuille de style CSS,
   3. elle définit son propre `<title>` (qui sera **Inscription**, ou ce que vous voulez).

2. Dans la partie `<main>` de la page, ajoutez

   1. une section `Inscription` (un titre `h2` avec le même style que pour la page `index.html`)  
   2. l'image [join_us.PNG]({{site.baseurl}}/assets/join_us.PNG) qui est...encore une image du directeur.
   
3. En utilisant le CSS, donnez une largeur de `200px` à l'image `join_us.PNG`.

4. Validez votre page HTML.
  
5. Laissez cette page de côté pour le moment, nous y reviendrons dans un prochain TP.

</div>

À ce point, le travail de division du site n'a pas encore de résultat visuel
marquant. C'est avant tout un travail de structuration logique qui permet au
navigateur, ou à un moteur de recherche, de mieux comprendre votre page web.
Nous verrons comment changer la mise en page globale dans les TPs suivants. Pour
la suite du TP, nous allons ajouter du style aux éléments de la page d'accueil.
  
**Pensez bien à revenir sur la page d'accueil (index) pour la suite du travail. Nous poursuivrons le travail sur la page d'inscription dans un prcohain TP**

## Tableaux

L'élément `<table>` correspond à une structuration récurrente, qui sert à représenter un ensemble de données sous forme de colonnes et de lignes.

### Les éléments `<table>`, `<tr>`, et `<td>`

L'élément `<table>` contient la table.
La table est composée de ligne (l'élément `<tr>`) contenant des cellules (élément `<td>`).


### L'élément `<th>`

Dans l'arborescence du document, un élément `<th>` doit être le fils d'un élément
`<tr>`. Il représente une cellule en-tête (le titre d'une colonne ou le titre d'une
ligne du tableau). Il peut être utilisé à la place d'un élément `<td>`.

Voici un squelette de table :

```html
<table>
   <tr>
      <th>Caract1</th>
      <th>Caract2</th>
      <th>Caract3</th>
      <th>Caract4</th>
   </tr>
   <tr>
      <td>Val1_1</td>
      <td>Val1_2</td>
      <td>Val1_3</td>
      <td>Val1_4</td>
   </tr>
   <tr>
      <td>Val2_1</td>
      <td>Val2_2</td>
      <td>Val2_3</td>
      <td>Val2_4</td>
   </tr>
   ...
</table>
```

<div class="exercise">

1. Ajoutez une section `Maîtrise des sorts` à la fin de la partie `<article>` (à l'intérieur).
1. Après cette section, créez une table avec les six noms de colonnes suivants : 
`Sorcier, Kenavo, Abracadabra, Perros-Guirec, After Effects, Muchos Dineros`. Les noms
des sorts (donc, tout sauf `Sorcier`) doivent être contenus dans des balises `<span>`.
1. Ajoutez les six lignes suivantes (Un "Oui" indique que le sorcier maîtrise le sort, et "Non" qu'il ne le maîtrise pas) :

     * Albus Humblebundledore, Oui, Oui, Oui, Oui, Oui
     * Georges Tuséki, Oui, Oui, Oui, Non, Non
     * Henry PotDeBeurre, Non, Non, Oui, Oui, Non
     * Texas Granger, Oui, Non, Oui, Non, Non
     * Rogue-like, Non, Oui, Non, Oui, Non
     * Le professeur de SVT, Non, Non, Non, Non, Non

1. Donnez un identifiant à votre table.
1. Testez la conformité de votre site.

</div>

### Les éléments `<thead>` et `<tbody>`

Les éléments `<thead>` et `<tbody>` servent à définir plus explicitement la structure de notre table:

 * `<thead>` : la définition des colonnes (`Sorcier, Kenavo,`...) 
 * `<tbody>` : le corps du tableau, c'est-à-dire les lignes (nos sorciers et leur indication de maîtrise).

<div class="exercise">

1. Ajoutez ces balises pour englober ces deux parties (en oubliant pas leurs
   balises fermantes `</thead>` et `</tbody>`)

1. Testez la conformité de votre site.

</div>


À ce stade la structure de votre table reflète le sens que vous vouliez y mettre.
Voyons maintenant comment la styliser.

<div class="exercise">
 1. Définissez une couleur de fond `#00AAFF` pour la partie en-tête `thead` du tableau 
 (en ciblant celui-ci particulièrement, pas tous les tableaux).
 1. **Sans modifier le code HTML**, donnez la couleur violette `#640051` au texte des sorts 
 (contenus dans des éléments `span`) dans le tableau (voir la
 [section sur les sélecteurs]({{site.baseurl}}/tp/tp2_css.html#règles-de-compositions-des-css))
 1. ajoutez une règle pour que le fond d'une ligne (*row*) sur deux du corps de
 la table apparaisse en blanc et l'autre avec la couleur `#CCC` toujours 
 <strong>SANS</strong> modifier de quelque façon le HTML (voir la
 [section sur les sélecteurs]({{site.baseurl}}/tp/tp2_css.html#règles-de-compositions-des-css))  
 **Attention :** La ligne du `<thead>` doit rester bleue.

</div>

### Les attributs `rowspan` et `colspan` 

Les balises `<th>` et `<td>` peuvent prendre des attributs `rowspan` et/ou
`colspan`, qui permettent d'étirer la cellule courante pour prendre la place de
plusieurs cellules :

 * `rowspan` permet d'étirer la cellule sur plusieurs lignes (i.e rows),
 * `colspan` permet d'étirer la cellule sur plusieurs colonnes.

<div class="exercise">

Il apparaît qu'Albus Humblebundledore maîtrise tous les sorts.

1. Faites une cellule qui prend toute la largeur de manière à mettre cela encore
plus en exergue. (Il faut supprimer les autres cellules et n'en garder qu'une seule qui prend toute la place).

2. Mettez le "Oui" d'Humblebundledore en avant avec une balise `<strong>` pour bien montrer
qui est le directeur.

3. (Optionnel) Vous pouvez faire de même avec le "Non" du professeur de SVT.

Plus tard, nous verrons comment centrer le texte des cellules.

<!-- Faire en sorte que les noms des acteurs soient maintenant des liens vers leurs pages Wikipedia. -->

</div>

## Le modèle de boite

Comme vous l'avez vu précédemment, les balises de type structure définissent des
boîtes. Ces boîtes disposent toutes des propriétés CSS suivantes :

* `margin` : marge à l’extérieur de la bordure, entre cette boîte et la
  suivante, et/ou entre cette boite et son parent. La zone couverte par la marge
  est de la même couleur que son parent,
* `border` : bordure qui entoure le contenu. Cette propriété attend trois
   valeurs :

   1. `width`, par ex. `1px`,
   1. `style`, par ex. `solid`, `dotted`, `dashed`,  ...
   1. `color`, par ex. `black`.  
   **Attention :** Un border n'a pas de style par défaut, donc lui donner une
   width ne suffit pas pour le voir.
   
* `padding` : marge intérieure à la bordure, c'est-à-dire espacement entre le
   contenu et la bordure de la boîte. Le padding partage le même arrière plan
   (`background-color`) que la boîte,

* `width` : la largeur du contenu, *i.e.* de la boîte *content*

* `height` : la hauteur du contenu, *i.e.* de la boîte *content*

<img alt="Box model" src="{{site.baseurl}}/assets/boxmodel.png" style="margin:0
auto;display: block;">

Par exemple le code suivant

```css
.maboite {
  padding:20px 50px 20px 50px;
  border:5px solid green;
  background-color:gold;
}
```

s'affiche comme ceci.

<div style="text-align:center">
<div style="display:inline-block;padding:20px 50px;border:5px solid green;background-color:gold;">
La zone de contenu
</div>
</div>

<div class="exercise">

Inspectez la boite ci-dessus pour voir le style qui y est appliqué. Trouvez dans
la partie Style des outils de développement le modèle de boite (comme
ci-dessous) et inspectez les quatre boites *content*, *padding*, *border* et
*margin* pour les voir se dessiner à l'écran.

<img alt="Box model" src="{{site.baseurl}}/assets/boxmodeldevtool.png"
style="margin:0 auto;display: block;">

</div>

<!-- À noter que la taille réelle d'une boîte est égale à la taille du contenu -->
<!-- `content` (width, height) additionnée de l'épaisseur du padding, du bord et de -->
<!-- la marge.   -->

Il y a trois syntaxes différentes pour donner des valeurs au `margin`, au
`padding` et au `border` :

 * `margin : t r b l;` : Si on donne 4 tailles `t`, `r`, `b` et `l`, alors `t`
   est associé à la valeur du haut (top), `r` est la valeur droite (right), `b`
   au bas (bottom) et `l` à la gauche (left).
 * On peut aussi utiliser individuellement les 
   propriétés `margin-top`, `margin-bottom`, `margin-left` ou `margin-right` pour ne définir 
   qu'une seule valeur à la fois.
 * `padding : v h;` : Si on ne donne que 2 tailles `v` et `h` alors `v` est
   associé aux valeurs verticales et `h` horizontales. C'est donc équivalent à
   `padding: v h v h;`.
 * `padding : a;` Si on donne une seule valeur, elle sera associée aux quatre
   coté de la boite, comme si on avait écrit `padding: a a a a;`.
 * Comme pour `margin`, on peut aussi utiliser individuellement les 
   propriétés `padding-top`, `padding-bottom`, `padding-left` ou `padding-right`.

Exemples : 

```css
#titi {margin : 5px 0 4px 7px;}
/* Marges verticales (haute et basse) de 10px et horizontales de 5px */
div {margin: 10px 5px;} 
/* Le padding dans toutes les directions est de 5px */
.toto {padding : 5px}    
```

<div class="exercise">
 1. Ajoutez du padding vertical de `10px` aux titres de sections,
 1. Ajoutez du margin vertical de `30px` aux paragraphes (donc, pour le top et le bottom),
 1. Ajoutez du padding horizontal de `5px` aux sorts dans la table (et seulement pour cette table !).
 1. Ajoutez une bordure aux titres `<h3>` de `1px`, de style `solid` et de couleur `#CCCCCC`. 
</div>


### Centrer horizontalement :

Pour centrer le contenu d'une balise :

* si l'on veut centrer du texte (ou une balise au niveau du texte) dans une
  balise : `text-align: center`
* si le contenu est lui-même dans une balise de structure moins large que la
  balise parent : `margin : auto` sur la balise de structure.


<div class="exercise">
 1. Centrez le `body` horizontalement,
 1. Dans la table, centrez le texte des cellules, (le "Oui" d'Humblebundledore notamment est encore trop discret, selon lui)
</div>

## Les contenus flottant

La propriété `float` associée à un élément permet de faire flotter ce dernier complètement à gauche ou à droite de la ligne où il se trouve. 
Les valeurs de la propriété float sont  `left`, `right`, `none` et `inherit`.

<div class="exercise">

 1. Placez l'image d'Albus Humblebundledore à gauche du texte, 
 1. Placez l'image de Georges Tuseki à droite du texte.
 1. Placez les quatres logos des maisons dans un élément `div` (auquel vous donnerez un identifiant) et placez-le à droite du texte (seulement ce `div`, pas tous les `div` de la page !).

</div>

<div class="exercise">
1. Dans la section "L'école de sorcellerie Georges Pompidou", divisez le paragraphe en deux paragraphes distincts. 
Le premier commence sur "L'école de sorcellerie..." et finit sur "...d'un taux d'échec très élévé.". La suite va dans le 
second paragraphe.

   Vous devez alors avoir le rendu suivant :
   
   <img src="{{site.baseurl}}/assets/intro_noclear.PNG" alt="Intro no clear"
   style="display:block;margin:0 auto;">
   
2. Nous souhaitons plutôt ce rendu :
   
   <img src="{{site.baseurl}}/assets/intro_clear.PNG" alt="Intro clear"
   style="display:block;margin:0 auto;">
   Il faut d'abord régler le problème du texte collé à l'image, pour ça on peut simplement ajouter une marge de 5 pixels à droite de l'image.
   Pour interdire à notre paragraphe d'avoir un élément flottant sur son côté gauche,
rajoutez-lui la règle `clear:left`.  
**Note :** On peut aussi interdire le côté droit avec `clear:right` et les deux
  en même temps avec `clear:both`.

</div>

## Position

La propriété CSS `position` offre de nouvelles possibilités pour le
positionnement des éléments. Ses valeurs sont :

* `static` : comportement normal (par défaut), l'élément est inséré normalement.
* `relative`: le reste de la page fait comme si l'élément était positionné
  "normalement". De son côté, l'élément est positionné *relativement* à la
  position où il aurait dû être. On voit donc un espace où l'élément aurait dû
  être en `position:static`.
* `absolute` : le reste de la page fait comme si l'élément n'existait
pas. L'élément se positionne relativement à son plus proche ancêtre
<strong>positionné</strong> (voir ci-dessous) ou sinon à `<body>` (si aucun
ancêtre n'est positionné).
* `fixed` : le reste de la page fait comme si l'élément n'existait
pas. L'élément se positionne relativement à la fenêtre d'affichage ; il paraît donc *fixé* lors d'un défilement de la page.

Un élément est dit <strong>positionné</strong> s'il a une position autre que `static` (qui est la valeur par défaut).
Pour indiquer le décalage de position, on utilise les propriétés `top`, `left`,
`right` et `bottom`. Par exemple, les propriétés

```css
position:relative; 
top:20px; 
left:20px; 
```

vont positionner un élément `20px` plus à droite et en bas qu'il aurait dû l'être.

Référence : [Mozilla Developer Network (MDN)](https://developer.mozilla.org/fr/docs/Web/CSS/position)

<div class="exercise">

1. Testez votre compréhension des propriétés `position:
   relative;top:20px;left:20px;` précédente en les appliquant **temporairement** sur
   l'image d'Humblebundledore.

2. Ajoutez les icônes de réseaux sociaux
[facebook.png ![Facebook]({{site.baseurl}}/assets/facebook.png)]({{site.baseurl}}/assets/facebook.png)
et
[twitter.png ![Twitter]({{site.baseurl}}/assets/twitter.png)]({{site.baseurl}}/assets/twitter.png)
toujours positionnées en bas à droite de la fenêtre d'affichage l'une au-dessus
de l'autre comme [ceci]({{site.baseurl}}/assets/demo_reseaux.PNG). Pour cela, en plus du CSS, il peut
être utile d'utiliser l'élément `div` pour structurer la zone contenant ces icônes.

</div>
