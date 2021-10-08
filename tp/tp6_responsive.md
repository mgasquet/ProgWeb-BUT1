---
title: TP6 &ndash; Responsive Design
subtitle: 
layout: tutorial
---

## Introduction

Les smartphones, les tablettes et tous les appareils de la mobilité demandent de
repenser le web d'aujourd'hui. Concevoir un site ou une application Web
s'adressant à tous ces médias n'est pas une tâche triviale. Voici un aperçu des
nombreuses solutions existantes :

* Une solution en pur CSS. En effet, le CSS est le langage de base pour la mise
  en page des pages Web. Il est donc en constante évolution (CSS3 en cours
  d'élaboration) pour s'adapter aux nouveaux besoins.

* Coder deux sites en HTML/CSS : un pour les ordinateurs et un pour les
   smartphones (et un pour les tablettes ? et un pour les smartwatch ?). Exemple
   [lemonde.fr](http://lemonde.fr) et [mobile.lemonde.fr](http://mobile.lemonde.fr).

* Des applications natives pour chaque système (Android, iOS, Windows Phone, ...)

* L'utilisation de la puissance de Javascript pour faire des mises en page
  adaptatives. 

Plus pour nous positionner dans cette jungle que par purisme, nous prendrons
deux hypothèses de départ :

* *"Il n'y a pas besoin d'applications pour cela !"* : Pas besoin de faire du
   natif Android ou iOS.
* *"Il n'y a pas besoin de faire deux sites web pour cela !"* : On s'interdit de
   faire un site Web pour mobile et un pour ordinateur.


Nous adopterons dans ce TP une approche itérative, en rajoutant au fur et à
mesure des contraintes pour pouvoir adapter l'affichage notre site web dans différents 
contextes, de manière responsive.

Pour ce cinquième TP, allez dans le dossier `Dev_Web` puis **copiez** et **collez** le contenu de votre 
dossier `TP5` dans un nouveau dossier nommé `TP6`. C’est dans ce dossier que vous travaillerez durant ce TP.


## CSS2

Certaines propriétés n'ont pas attendu ni les nouveaux médias ni le CSS3 pour
s'imposer aux développeurs. Elles prenaient déjà tout leur sens sur des sites
particulièrement fournis et/ou sur des petits écrans 15 pouces.

### Les pourcentages '%'

On peut commencer par exprimer toutes les tailles en relatif. C'est ce que nous
avons déjà fait en utilisant des dimensions en `%`. [Rappelez
vous]({{site.baseurl}}/tp/tp4_html_css_avance2#exercices) que la largeur d'un
élément en `display:block` ou en `display:flex` se calcule par rapport à son
*containing block*, c'est-à-dire son plus proche ancêtre `block` ou `flex`. Par
défaut, les éléments en `block` ou `flex` prennent toute la largeur de leur
*containing block*. Et si on fixe une largeur en pourcentage, ce sera
relativement à la largeur du *containing block*.

<div class="exercise">

1. Tentez à nouveau de redimensionner la fenêtre et observez que le contenu de la page ne bouge pas.
1. Donnez à `<body>` la `width` de `100%`. Donnez à la propriété `margin` la valeur `auto` si ce n'est pas le cas.
1. Changez les dimensions de `<article>` et `<aside>` à respectivement `67%` et `33%`.
3. Tentez à nouveau de redimensionner la fenêtre.

</div>

*Oups ! Le redimensionnement fonctionne mais nous avons perdu notre affichage initial. Nous allons régler cela dans la prochaine section.*

**Note :** Si adapter les largeurs en pourcentage marche bien, ce n'est pas le
cas des hauteurs.  Cela est dû au fait que la largeur de la page est connue
(c'est la largeur de la fenêtre d'affichage du navigateur) mais sa hauteur ne
l'est pas encore... (puisque la page n'est pas encore affichée et que la
hauteur va dépendre de la quantité de contenu). Autrement dit, la hauteur de la
zone du navigateur où s'affiche la page (`viewport height`) n'est pas forcément
la hauteur de la page [^somesamplefootnote] (et c'est lié à la présence d'un
ascenseur à droite pour descendre dans la page).

[^somesamplefootnote]: L'unité `vh` permet maintenant de définir une taille de 0 à 100 relative au viewport.


### `max-width` et `min-width`


Les règles précédentes permettent d'avoir un rapport homogène, mais pas un rendu
optimal :

 - sur de petits écrans d'ordinateur, des éléments ne peuvent pas être
   correctement affichés (des images, des colonnes, ...)
 - sur de très grands écrans, le texte devient illisible : les yeux fatiguent à
   cause des lignes trop longues.
 
Pour contraindre les dimensions maximales et minimales, nous utiliserons
`max-width`, `max-height`, `min-width` et `min-height`, qui prennent le même
type de valeur que `width` et `height`.


<div class="exercise">
1. Nous voulons retrouver notre rendu précédent avec un body centré qui a une taille fixe, tout 
en autorisant le redimensionnement des éléments. Pour cela, ajoutez une limite maximum de largeur 
à `<body>` de `900px`.
2. Nous voulons que le contenu de notre page ne se redimensione plus en dessous d'une certaine taille. 
Pour cela, ajoutez une limite minimum de largeur à `<article>` et à `<aside>` de `200px` et `150px`.
</div>


### Overconstraint

Mais que se passe-t-il quand on mélange `min-width` ou `max-width` avec des tailles en
poucentage ? Prenons l'exemple suivant


```html
<div style="display:flex">
	<div style="width:50%;max-width:400px;">
		Div1
	</div>
	<div style="width:50%;">
		Div2
	</div>
</div>
```

qui s'affiche comme suit

<div style="display:flex;border:1px solid black;">
<div style="width:50%;max-width:400px;background-color:orange;">
Div1
</div>
<div style="width:50%;background-color: cornflowerblue;">
Div2
</div>
</div>

<br>

<div class="exercise">

**Remarquez** en changeant la largeur de votre fenêtre (celle du TP) que :

1. les deux `<div>` prennent toute la largeur quand `<body>` a une largeur
   inférieure à `800px` (donc le premier `<div>` a une largeur de moins de
   `400px`)
2. mais quand la largeur de `<body>` est supérieure à `800px`, alors les deux
   `<div>` ne remplissent plus toute la largeur de `<body>`. Div2 garde une
   largeur de 50% mais Div1 ne peut plus prendre les `50%` restant car il est
   contraint par sa largeur maximale de `400px`.

</div>


Nous allons utiliser `display:flex` pour mieux mélanger les tailles relatives et
les contraintes `min-width`/`max-width`. Nous avions déjà vu les règles de la
colonne de gauche de
[cette super page sur FlexBox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)
; c'était celles qui s'appliquaient au parent. Nous allons maintenant nous
pencher sur la colonne de droite qui s'applique aux balises enfants. Regardez
particulièrement les propriétés `flex-shrink` (valeur par défaut `1`),
`flex-grow` (valeur par défaut `0`). Pour l'instant, nous ne toucherons pas à
`flex-basis` (qui gardera donc son comportement par défaut `auto`).

<!-- Nous vous invitons à faire d'autres recherches pour mieux comprendre -->
<!-- `flex-shrink` et `flex-grow` si nécessaire. En particulier, le site du -->
<!-- [Mozilla Developer Network](https://developer.mozilla.org/fr/) est une mine -->
<!-- d'information. -->

<!-- Attention, le comportement de l'exercice précédent est déjà déformé par les
propriétés par défaut flex-grow:0; flex-shrink:1 -->

<div class="exercise">

1. Lisez la section sur `flex-shrink` et `flex-grow` dans [le guide de
   FlexBox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/) ou tout
   autre page Web. N'hésitez pas à parler de votre compréhension avec votre
   professeur.

1. Donnons un exemple d'utilisation de `flex-grow`. Votre boulot est de vérifier
   que vous comprenez son fonctionnement.

   Nous pouvons désormais résoudre le problème précédent avec `flex-grow:1;`.

   ```html
   <div style="display:flex">
   	<div style="width:50%;max-width:400px;">
   		Div1
   	</div>
   	<div style="width:50%;flex-grow:1;">
   		Div2
   	</div>
   </div>
   ```
   
   qui s'affiche comme suit
   
   <div style="display:flex;border:1px solid black;">
   <div style="width:50%;max-width:400px;background-color:orange;">
   Div1
   </div>
   <div style="width:50%;flex-grow:1;background-color: cornflowerblue;">
   Div2
   </div>
   </div>

   Maintenant que la largeur de `<body>` est supérieure à `800px`, alors le
   second `<div>` voit sa largeur augmenter grâce à `flex-grow:1;`. Donc les
   deux `<div>` remplissent toujours la largeur de `<body>`.

1. Nous souhaitons utiliser les propriétés `flex-grow` et `flex-shrink` au lieu d'utiliser 
des largeurs en pourcentages. Changez les largeurs de `<article>` et `<aside>` pour 
qu'elles soient de `300px` et `200px`. Mettez les propriétés `flex-shrink` et 
`flex-grow` pour ces deux éléments à `0`. Dans les prochaines questions, vous devrez
régler ces propriétés afin d'avoir le rapprot souhaité.

1. Nous souhaitons que quand l'écran est trop large, l'espace restant soit
   réparti entre `<article>` et `<aside>` de telle sorte que l'espace gagné par
   `<article>` soit 3 fois plus grand que celui gagné par `<aside>`.  
   **Quelle propriété** CSS devez-vous utiliser pour avoir ce comportement ?
   Implémentez ce comportement.

1.  Nous souhaitons que quand l'écran est trop petit, `<article>` diminue de
    deux tiers de la largeur à supprimer et `<aside>` diminue du reste.  
   **Quelle propriété** CSS devez-vous utiliser pour avoir ce comportement ?
   Implémentez ce comportement.
   
1. Redimensionnez votre fenêtre pour observer que les éléments bougent et se 
redimensionnent selon la taille de la feneêtre.
</div>

À ce stade, vous devriez avoir un rendu similaire à celui de la fin du dernier TP 
quand la fenêtre est affichée dans sa taille normale. La seule différence est que le contenu
s'adapte maintenant à la taille de la fenêtre quand celle-ci est redimensionnée.
Nous avons vu une méthode qui permettait de faire cela en exprimant les largeurs du contenu 
en pourcentages, au début du TP, mais dans notre cas, nous avons préféré utiliser une autre méthode 
mettant à profit le `display:flex`.


### Problèmes plus complexes


Il arrive un moment où diminuer encore la taille n'a plus de sens. Il faut
prendre des mesures draconiennes, par exemple passer `<aside>` sous `<article>`
ou carrément supprimer `<aside>`.

Les règles CSS déjà vues en TPs ne permettent pas de coder ce genre de
comportement. Il nous faut une façon d'écrire du CSS qui ne sera valide que dans
des cas précis. Nous verrons dans la prochaine section comment cela est possible
en CSS3.

## Le site de l'école Georges Pompidou sur mobile

### Les outils pour travailler ?

Jusqu'ici on pouvait considérer que tous les outils de développement d'Internet
Explorer / Firefox / Chrome étaient égaux. En fait celui de Chrome était déjà un
peu meilleur :

  * auto complétion des règles CSS ajoutées dynamiquement,
  * liste déroulante des valeurs possibles des champs,
  * plus rapide, plus stable (un processus par onglet)
  * etc.

En tout cas, pour le *reponsive design* il n'y a pas photo : Chrome (ou son
pendant libre Chromium) est <strong>vraiment</strong> votre "best-friend-ever".

### Que fait mon navigateur Web sur téléphone par défaut pour un site ?

Comment peut-on rendre un site internet compatible mobile à moindre coût ?

Voici l'algorithme (simplifié) opérant par défaut :

 * Générer le site sur une taille d'écran virtuel, disons d'une largeur de `980px` ;
 * Faire un zoom arrière de manière à faire rentrer le site dans l'écran du
   smartphone ; (oui, cela fait de petits éléments)
 * Supposer que l'utilisateur connaît le *pinch to zoom* pour naviguer dans le site :
 <img src="{{site.baseurl}}/assets/pinch_zoom.png " alt="Pinch to zoom schema"
style="margin: 0 auto;height:100px;vertical-align:middle;">

Et ça marche ! De fait, c'est ce que font par défaut les smartphones quand ils
tombent sur un site non responsive.

<div class="exercise">

1. Dans les outils développeurs (`F12`) de Chrome/Chromium, passez dans le
device mode 
<img src="{{site.baseurl}}/assets/phone-responsive.png" alt="Outil pour mobile" style="margin: 0 auto;width:45px;vertical-align:middle;">
*"Samsumg Galaxy S5"* sous Chrome/Chromium et rechargez votre page. Constatez
que le site s'affiche en tout petit.

1. Vérifiez que la taille de l'élément `<html>` est de `980px`, ce qui signifie que
   l'algorithme précédent a été utilisé pour l'affichage.  
   Remarquez aussi que la largeur de l'affichage est de `360px`, ce qui signifie
   d'un zoom arrière est effectué.

</div>

Même si cela marche, on ne peut pas dire que cela soit optimal. L'utilisateur
mobile n'a pas la même attente que l'utilisateur sur ordinateur, il veut avoir
accès rapidement aux informations essentielles, sans fioritures.  On imagine que
sur une smart watch par exemple un site comme méteo france serait largement plus
dépouillé (sur une smartwatch elle afficherait un nuage ou un soleil et la
température par exemple).

Typiquement nous voulons enlever des parties entières du site suivant la taille
de l'écran.

La première chose à faire est donc de demander aux navigateurs de ne plus faire
l'algorithme précédent (puisqu'on va le gérer nous-mêmes) dans la balise
`<head>` :

```html
 <meta name="viewport" content="width=device-width, initial-scale=1">
```

<div class="exercise">

Ajouter cette instruction au site de l'école (aux deux pages) et visualisez avec Chrome en
choisissant un smartphone. Inspectez la largeur de `<body>`. Que constatez-vous ?

</div>

Vous devez constatez que l'algorithme précédent ne s'applique plus. En gros le
navigateur n'essaie plus d'être intelligent : il vous laisse prendre le relai.

## La solution technique CSS3 :  les media queries

Les media queries sont un jeu d'options ajoutées à la norme CSS3 et qui permettent
de définir des règles CSS qui ne s'appliqueront que sous certaines conditions
spécifiques.

Il existe deux manières différentes de faire appel à une *media query* :

* Soit vous souhaitez un fichier CSS spécifique en entier, mais uniquement dans
  certaines conditions. Alors il faut ajouter à l'en-tête `<head>` de la page
  web une déclaration de fichier CSS standard, à laquelle on rajoute l'attribut
  `media` et une condition spécifique.

  ```html
  <link rel="stylesheet" media="condition" href="mon_css_special.css"/>
  ```
  
  N'oubliez pas que le dernier CSS chargé prend le pas sur les
  précédents. Pensez donc à toujours déclarer vos media-queries en dernier,
  sinon elles seront systématiquement écrasées par votre CSS *“standard"*.

* Soit vous souhaitez que juste certaines règles s'appliquent sous
  certaines conditions. Alors vous englobez vos règles avec la syntaxe suivante :

  ```css
  @media(ma_condition) {
    div {background-color:white;}
     ...
  }
  ```

Une media query fonctionne de la manière suivante : la condition est évaluée et
retourne une valeur “vrai” ou “faux”. Si la valeur est vraie, le fichier CSS/ la
règle CSS (selon la méthode employée) est appliquée.

Chaque condition est formée à partir d'une ou plusieurs conditions de
base. Parmi
[l'ensemble des conditions possibles](https://developer.mozilla.org/fr/docs/Web/CSS/Media_queries),
nous allons nous intéresser particulièrement aux suivantes :

* `min-width`, `max-width`, `min-height` et `max-height` : permettent de
  renseigner une dimension minimale/maximale à remplir pour que la condition
  soit vraie. Par exemple,

  ```css
    @media(min-width:100px) {
      div {background-color:white;}
    }
  ```
  
  Ici, le style défini pour les éléments `<div>` ne sera appliqué que si la largeur de la page est 
  supérieure ou égale à `100px`.
  
* `orientation` : prend les valeurs `landscape` (écran horizontal) ou `portrait`
  (écran vertical)


Les conditions de base peuvent être combinées ensemble pour former des
conditions complexes en utilisant les opérateurs logiques :

* “and” (ET) : les deux conditions de base doivent être vraies pour que la
  condition soit vraie
* “,” (OU) : au moins l'un des conditions de base doit être vraie pour que la
  condition soit vraie
* “not” (NON) : la condition de base qui suit le not doit être fausse pour que la
  condition soit vraie

**Exemple :** la règle `(min-width: 500px) and (min-height: 800px)` n'est
vraie que si la largeur de l'affichage est supérieure (ou égale) à `500px` et la
hauteur supérieure à `800px`.


<div class="exercise">

* Allez sur le site [Bootstrap](http://getbootstrap.com/) et constatez qu'il y a
  2 largeurs pour laquelle la mise en page change.
* Utilisez le *device mode* pour afficher les *media queries* (cliquer sur les 3
  points verticaux du *device mode* pour afficher ces *media queries*).
* Que se passe-t-il visuellement dans le menu lorsque vous redimensionnnez la
fenêtre autour du point de rupture situé à `768px` ?

</div>


### Les points de ruptures.

Afin d'organiser nos *media queries*, on peut par exemple se baser sur 3 à 4 valeurs de largeur d'écrans : 
 
 * `480px` (Smartphone)
 * `768px` (Tablette)
 * `992px` (écran d'ordinateur "Standard")
 * `1200px` (écran d'ordinateur "Large")
 
On peut bien sûr aussi utiliser des valeurs customisées, selon le design de notre site.

<div class="exercise">
 1. En dessous de 900px ne plus afficher la table (et le titre de section) des maîtrise des sorts 
 (de toute façon on sait tous qu'Albus Humblebundledore est le meilleur).
 2. L'image de Georges Tuseki dans la page `index.html` et celle d'Humblebundledore dans `inscription.html` prennent 
 trop de place. Faire en sorte ne plus les afficher en dessous de 768px.
 3. En dessous de 480px faire en sorte qu'`<aside>` et `<article>` soient en
    colonne et plus en ligne et aient une largeur de `100%`. Faire aussi en sorte qu'`<aside>` n'ai plus de marge à gauche.

</div>


### Mettez-moi un burger au menu !

Quand la taille de l'écran est limitée, une bonne pratique en *responsive design*
est de changer l'affichage du menu pour un bouton burger :

<img alt="Burger button, three horizontal lines, (two corresponding to the
bread, and the one for the meal) " src="{{site.baseurl}}/assets/burger.png"
style="margin:0 auto;display: block;">

Lorsque l'on cliquera dessus, le menu apparaîtra. Cela permet de ne pas perdre
de place sur la page lorsque le menu est fermé. Pour fixer les idées, nous
voulons un menu qui apparaît latéralement à la manière des exemples suivants :
 
 * [http://codepen.io/gungorbudak/pen/XbazEX](http://codepen.io/gungorbudak/pen/XbazEX)
 * [http://codepen.io/drewr/pen/uxvdt](http://codepen.io/drewr/pen/uxvdt)

Dans l'exercice suivant, nous allons coder un menu burger HTML/CSS (donc sans
JavaScript) qui apparait quand la souris passe au dessus du burger (la gestion
du clic nécessiterait du JavaScript).  (Notez au passage que
[codepen.io](http://codepen.io/) est un très bon outil pour découvrir de
nouvelles techniques !)

<div class="exercise">

Nous allons coder un deuxième menu, identique au premier dans son contenu, mais
avec une mise en page différente. Nous allons afficher l'un ou l'autre des menus
en fonction de la taille de l'écran.

1. Ajouter le `<div>` suivant (dans les deux pages) juste avant le menu `<nav>` :

     ```html
     <div class="burger">
       <img src="images/burger.png" alt="burger" width="50">
       <div id="menu2">
         <div><a href="./index.html">Accueil</a></div>
         <div><a href="./inscription.html">Inscription</a></div>
         <div><a href="./news.html">Actualités</a></div>
         <div><a href="./reglement.html">Règlement</a></div>
      </div>
     </div>
	```

1. Faites en sorte que le menu `<div class="burger">` n'apparaisse pas par défaut.

1. Positionnez le menu par rapport à la fenêtre d’affichage (quelle valeur de `position` faut-il mettre ?), tout en haut à gauche.

1. Faites en sorte qu'il soit visuellement au-dessus des autres éléments du site (cherchez sur le Web la propriété **z-index**)

1. À partir du point de rupture 'Smartphone', faites disparaître l'ancien menu `<nav>`
et faites apparaître le `<div class="burger">`.

1. Cachez par défaut en CSS le `menu2`. Au survol du `<div class="burger">`,
   faites-le réapparaître.

</div>

**Note :** Le hover sur les sous-menus n'a pas de sens sur téléphone
  portable. Il faudra gérer le clic avec du JS. La bonne solution est
  ... suspense, vous la verrez en 2ème année.


### La mobilité en général

Les contraintes liées à la mobilité ne se limitent pas au responsive design.
Pour vous donner une idée plus complète, voici d'autres exemples de contraintes
fortes qui viennent s'ajouter :

 * débit du réseau
 * faible capacité du média (processeur, mémoire vive,...)
 * mode offline (on peut passer sous un pont... il faut prévoir pour le cas échéant un cache local qui stocke les opérations courantes, afin de les consommmer lorsque le réseau revient) 
 * changement de paradigme de l'interface homme machine (mouse over, menu déroulant,... )
