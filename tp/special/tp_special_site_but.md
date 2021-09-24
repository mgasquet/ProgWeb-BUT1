---
title: TP Special &ndash; Site du B.U.T
subtitle: Mise en pratique HTML / CSS de base
layout: tutorial
---

Dans ce TP spécial, vous allez mettre en pratique tout ce que vous avez appris lors des deux premiers TPs.

Le but est de produire un petit site pour présenter le B.U.T Informatique, avec pour objectif [ce résultat]({{site.baseurl}}/assets/special/tp_spe_1/target_tp_special_1_but.png).

Comme l'objectif de ce TP est avant tout d'évaluer vos compétences, il y aura moins d'indications que d'habitude. Néanmoins, rien ne vous empêche d'aller consulter vos travaux antérieurs ou les consignes des TPs précédents.

## Rendu final 

Le rendu final sera le dossier complet de votre site, contenant :

1. Une page `index.html`.
2. Un dossier `css` contenant un fichier `styles.css`.
3. Un dossier `images`, contenant les différentes images affichées sur le site.
4. Un dossier `fichiers`, contenant les différents fichiers à faire télécharger à l'utilisateur du site.

Concernant le `css`, il faut utiliser un fichier `styles.css` et le relier à `index.html` comme nous l'avons vu.

L'usage de l'attribut ou de la balise HTML `style` (au lieu du fichier) est interdit.

## Cahier des charges - Indications

### Contenu de base de la page HTML

<div class="exercise">

1. Le titre de la page est **"Le site du B.U.T Informatique de Nevers"**.

2. Tous les titres en gras [sur la maquette]({{site.baseurl}}/assets/special/tp_spe_1/target_tp_special_1_but.png) sont des titres de sections (h2) 
à l'exception de "Premier semestre" et "Second semestre" qui sont des titres de sous-section (h3).

3. La **favicon** du site doit être [cette image]({{site.baseurl}}/assets/special/tp_spe_1/iut.jpg) (n'oubliez pas de placer vos images dans un sous-dossier `images`).

4. Il faut placer [cette image]({{site.baseurl}}/assets/special/tp_spe_1/logo_BUT.PNG) après le titre **"Le B.U.T Informatique de Nevers"**.

5. Il faut placer [cette image]({{site.baseurl}}/assets/special/tp_spe_1/univ.png) puis [cette image]({{site.baseurl}}/assets/special/tp_spe_1/keyboard.png) après le titre **"Présentation"**.

6. Juste après ces images, il faut écrire le **paragraphe** de présentation :

		Le B.U.T est un diplôme national qui se déroule en IUT, en 3 ans, venant remplacer le D.U.T et les licences professionnelles.
		Il sanctionne une formation générale et technologique dans un domaine professionnel et confère le grade de licence.
		Un BUT Informatique a ouvert ses portes à Nevers, au sein de l'ISAT
		
7. Dans le texte du paragraphe, **l'ISAT** doit être un lien renvoyant vers l'URL [https://www.isat.fr/](https://www.isat.fr/). 

8. La liste (numérotée) des lieux importants est :

    1. Salle de cours
    2. Restaurant universitaire
    3. Bibliothèque
	
9. La liste (non numérotée) des ressources externes est :

	* Règlement intérieur
	* Site de L'IUT de Dijon-Auxeres
	* Un fichier top secret que personne ne peut dévérouiller...?

10. L'item **Règlement intérieur** est un lien renvoyant vers [ce fichier]({{site.baseurl}}/assets/special/tp_spe_1/reglement.pdf), en interne (que vous aurez placé au préalable dans le sous-dossier `fichiers`).

11. L'item **Site de L'IUT de Dijon-Auxeres** est un lien renvoyant vers [https://iutdijon.u-bourgogne.fr/www/](https://iutdijon.u-bourgogne.fr/www/).

12. L'item **Un fichier top secret que personne ne peut déverrouiller...?** est un lien renvoyant vers [ce fichier]({{site.baseurl}}/assets/special/tp_spe_1/secret.zip), en interne.

13. La liste (non numérotée) des modules du premier semestre est :

    * Initiation au Dev
    * Dev. Interfaces Web
    * Maths discrètes
    * Introduction BD
	
14. La liste (non numérotée) des modules du second semestre est :

    * Dev. objets
    * Dev. d'apps avec IHM
    * Exploitation BD
    * Graphes
	
</div>

### Le style

<div class="exercise">

Pour cette partie, il vous faudra créer une feuille de style et la placer dans un sous-dossier `css`.

1. La couleur de fond de la page doit être `#c2d4f0`.

2. La largeur de la page doit être de `400px`.

3. La police utilisée pour la page doit être `Arial` (pas besoin de l'importer avec `@font-face`, votre navigateur la connaît déjà).

4. La hauteur des lignes de la page doit être de `120%`.

5. L'image du BUT Informatique doit avoir une largeur de `400px` et une hauteur de `200px`.

6. Le logo de l'université (uB) et aussi l'image du clavier doivent avoir une largeur de `80px` et une hauteur de `60px`.

7. Les titres de sections doivent être centrés et leur couleur de fond doit être `yellow`.

8. Les liens ne doivent pas avoir de décoration (ne doivent pas être soulignés).

9. Les liens déjà visités doivent être de couleur `magenta`.

10. Le titre et la liste des modules du premier semestre doivent êtres alignés à gauche.

11. Le titre et la liste des modules du second semestre doivent êtres alignés à droite.

12. Quand on survole le titre des sections (et aussi celui des sous-sections), le texte doit s'afficher en `green`.

13. Dans la page, il faut que les **lettres suivantes** aient un style particulier :

	* Le **g** de "générale" dans le paragraphe d'introduction.
	* Le **u** de "Ressources" dans "Ressources externes"
	* Le dernier **e** de "semestre" dans "Premier semestre"
	* Le premier **s** de "semestre" dans "second semestre"
	* Le **a** de "Restaurant" dans "Restaurant universitaire"
	* Le **f** de "fichier" dans "fichier top secret"
	* Le premier **r** de "déverrouiller" dans "que personne ne peut déverrouiller"
	
	Le style appliqué doit être une couleur **rouge** pour le texte, en **gras**, et avec une **taille de police** de `150%`.

	Ce style doit s'appliquer **seulement** quand on **survole les lettres en question**, ou aussi quand on **clique** n'importe où dans la page HTML.
	
	Je me demande bien à quoi ça sert tout ça... :D
	
14. Quand on clique n'importe où dans la page HTML, la police du **body** doit se changer en `Calibri` (elle aussi est déjà chargée dans le navigateur).
</div>





