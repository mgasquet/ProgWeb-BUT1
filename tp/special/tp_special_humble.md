---
title: TP Special &ndash;Blog du fabuleux Albus Humblebundledore
subtitle: Mise en pratique HTML / CSS avancé et formulaires
layout: tutorial
---

Dans ce TP spécial, vous allez mettre en pratique tout ce que vous avez appris lors des TPs 3, 4 et 5.

Le but est de produire la page d'accueil du blog du **fabuleux Albus Humblebundledore**, avec pour objectif [ce résultat]({{site.baseurl}}/assets/special/tp_spe_2/target_tp_special_2_humble.png).

Comme l'objectif de ce TP est avant tout d'évaluer vos compétences, il y aura moins d'indications que d'habitude. Néanmoins, rien ne vous empêche d'aller consulter vos travaux antérieurs ou les consignes des TPs précédents.

## Rendu final 

Pour ce TP, les éléments de base du site vous sont fournis. Commencez par télécharger [l'archive du site]({{site.baseurl}}/assets/special/tp_spe_2/bloghumble.zip).

Tout d'abord, commencez par **extraire l'archive** sur votre odinateur. Votre objectif sera de travailler sur les deux fichiers **index.html** et **styles.css** (qui se trouve dans le sous-dossier css) et de les compléter en suivant les consignes des différents exercices.

L'usage de l'attribut ou de la balise HTML `style` est interdit.

A la fin du TP, replacez le contenu du site produit dans une archive, puis déposez-là sur **Teams**.

## Réalisation du site

### Eléments de base

<div class="exercise">

1. Donnez le titre **Le blog du fabuleux Albus Humblebundledore** à la page.

2. Donnez une largeur de `1200px` à la page.

3. Donnez la couleur de fond `#333232` à la page.

4. Faites en sorte que le texte de la page soit de couleur blanche.

5. La hauteur des lignes doit être de `150%`.

6. Le body doit être centré.
</div>

<div class="exercise">

1. Ajoutez l'image du directeur (qui se situe dans `images/albus.png`) en dessous du titre `<h1>` **Albus Humblebundledore**.

2. Faites en sorte que cette image ait une largeur de `60%`.

3. Regroupez le titre **Albus Humblebundledore** et l'image du directeur dans un élément `<div>` et faites en sorte que son contenu (le titre et l'image) soit centré horizontalement.

</div>

<div class="exercise">
1. Dans le body, ajoutez un `<footer>`, au bon emplacement, contenant le texte : **© Copyright Albus Humblebundledore**.

2. Faites en sorte que le texte de ce footer soit centré horizontalement.

3. Ajoutez du **margin vertical** de `20px` au footer.
</div>

### Tableau

<div class="exercise">
1. Dans la partie `<article>` du `<main>`, ajoutez un élément `<table>` juste après le titre : **Comparatif des maisons selon le directeur**.

2. Donnez à ce tableau la valeur de votre choix pour l'attribut **id**.

3. Les noms de colonnes de ce tableau sont : **Maison, Intelligence, Assuidité, Travail et Courage**.

4. Commencez par définir les lignes du tableau comme ceci :
	 * Nintendor, Oui, Oui, Oui, Oui
     * Playstachouffle, Non, Non, Non, Non 
     * Pécéairdaigle, Non, Non, Non, Non
     * Xboxard, Non, Non, Non, Non

5. Donnez une largeur de `100%` au tableau.

6. Faites en sorte que le **texte** contenu dans le tableau soit **centré** et de couleur **noire**.

7. **Sans modifier le HTML**, faites en sorte que la couleur de fond de la ligne d'en tête soit **orange**.

8. **Sans modifier le HTML**, faites en sorte qu'une **colonne** sur deux ait une couleur de fond **blanche** et l'autre `#CCC`.

9. Faites en sorte qu'il ne reste qu'un seul **Oui** dans la colonne Nintendor et qu'il s'affiche en gras.

10. Faites en sorte que chaque **Non** des autres lignes s'affichent sur 3 lignes.

</div>

### Formulaire

<div class="exercise">

*Conseil : Ajustez l'espacement entre les champs en utilisant des `<div>` et des `<br>`*

1. Dans la partie `<main>`, ajoutez un élément `<aside>` après `<article>`.

2. Dans cette partie, ajoutez un titre `<h2>` : **Recherche d'articles**.

3. Dans cette partie, ajoutez un formulaire qui enverra une requête vers **recherche.php**. 
Ce formulaire sert à rechercher des articles sur le blog, sélectionnez donc la valeur appropriée pour l'attribut `method`.

4. Dans le formulaire, ajoutez un champ d'entrée permettant de rentrer du texte, libellée **Mots-clés**. Ce champ doit être **obligatoirement** complété.

5. Dans le formulaire, ajoutez un fieldset nommé **Caractéristiques avancées**, contenant :

	* Un champ **Catégorie d'article** permettant de sélectionner une valeur dans une liste déroulante parmi : **Classique**, **Magique**, **Blague du jour**, **Nintendor**.
	* Un champ **Note de l'article** permettant de sélectionner une valeur numérique entre 1 et 5.
	* Deux champs radio permettant de sélectionner une valeur entre **Publié** et **Archivé**.
	
6. Enfin, toujours dans le formulaire, ajoutez un bouton pour valider le formulaire, affichant **Rechercher**.

7. Ajotuer une étoile \* rouge à côté du libellé du champ **Mots-clés** pour signfiier qu'il doit être obligatoirement complété.
</div>

### Menu de navigation

<div class="exercise">
1. Dans le body, ajoutez un `<header>` au bon emplacement.

2. Dans ce `<header>`, ajoutez un élément `<nav>` contenant le code suivant :

```html
<a href="index.html">Accueil</a>
<a href="shop.html">Boutique</a>
<a href="faq.html">FAQ</a>
<a href="contact.html">Contact</a>
<div id="menuDroite">
	<a href="./connexion.html">Connexion</a>
	<a href="./inscription.html">Inscription</a>
</div>
```
	
3. Donnez une couleur de fond `#111` au menu de navigation.

4. Donnez une hauteur de `50px` au menu de navigation.

5. En utilisant le **display approprié**, faites en sorte de centrer tous les éléments du menu de navigation.

6. Pour tous les liens du menu de navigation, supprimez la décoration du lien, mettez le texte en **blanc** et ajoutez `17px` de **padding** vertical et horizontal.

7. Quand un lien du menu de navigation est survolé, faites en sorte que sa couleur de fond devienne `#2b2727` et la couleur du texte `#c95212`.

8. En utilisant le **display** appropié et un **positionnement** adapté, faites en sorte que le `<div>` contenant les liens de connexion et d'inscrption se place par rapport à son plus proche ancêtre et se positionne tout à droite du menu de navigation.

*Conseil : Il vous faudra aussi **positionner** `<nav>` pour que la partie de droite se place correctement*.
</div>


### Design avancé

<div class="exercise">
1. Donnez la couleur de fond `#635f5f` et un padding **gauche**, **droite** et **bas** de `2%` aux éléments `<article>` et `<aside>`.

2. En utilisant le **display approprié**, faites en sorte que, dans le `<main>`, `<aside>` se place à droite de `<article>`.

3. Donnez une largeur de `67%` à `<article>` et une largeur de `33%` à `<aside>`.

4. Ajoutez du **margin gauche** de `10%` et une hauteur de `100%` à `<aside>`.
</div>

<div class="exercise">

On souhaite obtenir [ce comportement]({{site.baseurl}}/assets/special/tp_spe_2/demo_form.gif) pour le formulaire du `<aside>`.

1. Au niveau du formulaire **"Recherche d'articles"**, ajoutez une case à cocher libellée **Recherche avancée**. Il faut que cet élément soit un enfant direct de `<form>` (pas dans une sous div, etc...).

2. Faites en sorte que, par défaut, le `<fieldset>` **Caractéristiques avancées** ne s'affiche pas.

4. En utilisant la pseudo-classe `:checked` (qui est active quand l'élément selectionné est coché, comme une case à cocher) faites en sorte que le `<fieldset>` caché du formulaire ré-apparaisse quand la case **"Recherche avancée"** est cochée.
</div>

<div class="exercise">

On souhaite obtenir [ce comportement]({{site.baseurl}}/assets/special/tp_spe_2/demo_connexion.gif) au niveau du lien **Connexion** du `<nav>`.

1. Dans `<nav>`, remplacez l'élément `<div>` avec l'identifiant `menuDroite` par :

```html
<div id="menuDroite">
	<div id="menuConnexion">
		<div>
			<a href="./connexion.html">Connexion</a>
		</div>
		<div id="connexionForm">
								
		</div>
	</div>
	<div>
		<a href="./inscription.html">Inscription</a>
	</div>
</div>
```

2. Dans le `<div>` d'indentifiant `connexionForm` ajoutez un formulaire de connexion contenant :

	* Un champ texte : **Login**, qui doit être obligatoirement complété par l'utilisateur.
	* Un champ pour rentrer un mot de passe : **Mot de passe**, qui doit aussi être obligatoirement complété.
	* Un bouton pour valider le formulaire, affichant **Connexion**.
	
	Ce formulaire devra envoyer une requête vers `connexion.php`. Sélectionnez la valeur apprioriée pour l'attribut `method`.
	
	Ajoutez la même indication visuelle (étoile rouge) que sur le formulaire précédent pour indiquer que les deux champs sont obligatoires.

3. En utilisant un procédé similaire à celui utilisé à la fin de l'exercice 6, faites en sorte de placer le `<div>` **connexionForm** par rapport à son ancêtre (la zone "menuConnexion").

4. Faites en sorte que le `<div>` **connexionForm**  ait :
	* Un padding vertical et horizontal de `10px`.
	* `#111` comme couleur de fond.
	* Une hauteur de `180px` et une largeur de `188px`.

5. Décallez **connexionForm** de `37px` vers le bas.

6. Faites en sorte que, par défaut, **connexionForm** ne s'affiche pas et qu'il ré-apparaisse seulement quand on survole le lien **Connexion**.
</div>
