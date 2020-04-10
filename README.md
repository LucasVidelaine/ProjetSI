# Projet Synthèse SI
Projet final de Licence Informatique : Développement d’un langage spécifique pour des animations graphiques simples.

On désire développer un prototype de moniteur pour un système de commande pour des éléments
représentés graphiquement. Dans sa version minimale, un élément visuel est une forme géométrique
basique (rectangle, ellipse, ligne, texte…). Le moniteur permet de les installer dans un conteneur et
de les animer.

Le développement se fait en Java sous Eclipse.

***
## Sommaire : 
Le projet se constitue d’un ensemble d’exercices de difficulté croissante. Nous avons un total de 5 exercices déclinés, pour certain, en sous exercice :

* [Exercice 1 : Prise en main de la couche graphique](#exercice-1--prise-en-main-de-la-couche-graphique)
* [Exercice 2 : Première version d’un interpréteur de script](#exercice-2--première-version-dun-interpréteur-de-script)
  * [Exercice 2.1 : Script de configuration](#exercice-21--script-de-configuration)
  * [Exercice 2.2 : Script d’animation](#exercice-22--script-danimation)
* [Exercice 3 : Introduction des commandes](#exercice-3--introduction-des-commandes)
* [Exercice 4 : Sélection et exécution des commandes](#exercice-4--sélection-et-exécution-des-commandes)
  * [Exercice 4.1 : Référencement des objets et enregistrement des commandes](#exercice-41--référencement-des-objets-et-enregistrement-des-commandes)
  * [Exercice 4.2 : Ajout et suppression dynamique d’éléments graphiques](#exercice-42--ajout-et-suppression-dynamique-déléments-graphiques)
  * [Exercice 4.3 : Ajouter des éléments à des conteneurs](#exercice-43--ajouter-des-éléments-à-des-conteneurs)
  * [Exercice 4.4 : Création et exécution de scripts](#exercice-44--création-et-exécution-de-scripts)
* [Tests finaux](#tests-finaux)
* [Bonus](#bonus)
* [Bilan critique](#bilan-critique)
  
***

## Exercice 1 : Prise en main de la couche graphique

L'objectif de cet exercice était de programmer le déplacement de carré au sein d'une fenêtre, tout en le faisant changer de couleur de manière aléatoire.

La difficulté de l'exercice est la prise en main de l'environnement graphique et des classes existantes. Il faut un peu de temps pour découvrir les méthodes que nous avons à disposition.

Le déplacement du carré devait pouvoir s'adapter au redimensionnement dynamique de la fenêtre (par l'utilisateur).

Le résultat de l'exercice :

![Exécution de l'Exercice 1](/exercice_1.gif)

***

## Exercice 2 : Première version d’un interpréteur de script
### Exercice 2.1 : Script de configuration

Ce deuxième exercice avait pour but d'introduire la notion de script de commande a exécuter.
Le second exercice a pour objectif de mettre en place l'utilisation de commande, que l'utilisateur peut exécuter pour alimenter sa fenêtre.
La commande à exécuter dans cet exercice était la suivante :
```
(script
	(space color black)
	(robi color yellow) )
```
Cet exercice ne m'a pas posé de problème particulier.

Le résultat de l'exercice :

![Exécution de l'Exercice 2-1](/exercice_2_1.PNG)

### Exercice 2.2 : Script d’animation

Dans la seconde partie de l'exercice, la commande à exécuter a évoluée afin de permettre une animation.

La commande à exécuter dans cet exercice était la suivante :

```
(script
	(space color white)
	(robi color red)
	(robi translate 10 0)
	(space sleep 100)
	(robi translate 0 10)
	(space sleep 100)
	(robi translate -10 0)
	(space sleep 100)
	(robi translate 0 -10) )
```

Ce script introduisait les commandes suivantes :

- Translate : Permet de déplacer un élément sur un axe grâce à des coordonnées X et Y.
- Sleep : Permet de mettre en sommeil le programme pendant un temps donnée en millisecondes

Cet exercice ne m'a pas posé de problème particulier.

Le résultat de l'exercice :

![Exécution de l'Exercice 2-2](/exercice_2_2.gif)

***

## Exercice 3 : Introduction des commandes

L'objectif de cet exercice était de faire évoluer la structure du programme en créant une classe Command contenant une méthode unqiue run(). Nos autres classes hériteront de cette classe Command tout en redéfinissant la méthode run(). Nous aurons ainsi une classe par commande exécutable.

Cette évolution nous simplifiera grandement la tâche lors de futurs ajouts de commande.

La commande à exécuter dans cet exercice était la suivante :

```
(script
	(space setColor yellow)
	(robi setColor red)
	(robi translate 10 0)
	(space sleep 100)
	(robi translate 0 10)
	(space sleep 100)
	(robi translate -10 0)
	(space sleep 100)
	(robi translate 0 -10) )
```

Cet exercice ne m'a pas posé de problème particulier.

Le résultat de l'exercice :

![Exécution de l'Exercice 3](/exercice_3.gif)

***

## Exercice 4 : Sélection et exécution des commandes
### Exercice 4.1 : Référencement des objets et enregistrement des commandes

L'objectif de cet exercice était de faire évoluer une nouvelle fois la structure globale de notre programme en ajoutant une classe Reference et une classe Environment. Ces deux nouvelles classes ont pour but de simplifer encore plus l'ajout de commandes.

Lorsque nous ajoutons un element, celui-ci possède une référence liée à des commandes et un environnement.

La commande à exécuter dans cet exercice était la suivante :

```
(space sleep 1000)
(robi setColor yellow)
(space sleep 500)
(space setColor red)
(space sleep 500)
(robi translate 30 30)
```

Cet exercice ne m'a pas posé de problème particulier.

Le résultat de l'exercice :

![Exécution de l'Exercice 4.1](/exercice_4_1.gif)

### Exercice 4.2 : Ajout et suppression dynamique d’éléments graphiques

L'objectif dans cet exercice était d'implémenter les classes AddElement et DelElement qui nous permettent d'ajouter ou de supprimer des éléments dans notre environnement.

Cette partie a requis un certain temps de compréhension, puisqu'il a fallu se plonger plus profondément dans les bibliothèques afin de voir comment chaque classe était gérée (GRect, GOval etc sont des GBounded, donc des GElement).

Le résultat de l'exercice :

![Exécution de l'Exercice 4.2](/exercice_4_2.gif)

### Exercice 4.3 : Ajouter des éléments à des conteneurs

L'objectif de cette exercice était de pouvoir ajouter des éléments au sein de rectangle. 

La solution choisie pour mettre en place cette possibilité est l'ajout d'un environnement dans la référence de l'élément parent afin de contenir les éléments enfant.

Lors de la création d'un élément on instancie un nouvel environnement "enfant".

Désormais, la référence space est contenu dans un environnement, permettant de l'appeler et contient elle-même un environnement permettant d'y disposer les éléments.

Pour simplifier les commandes nous avons également mis en place une notation pointée.

La commande à exécuter dans cet exercice était la suivante :

```
(space sleep 1000)
(space setDim 1000 1000)
(space sleep 500)
(space add robi (Rect new))
(space sleep 500)
(space.robi setDim 800 800)
(space sleep 500)
(space.robi setColor red)
(space sleep 500)
(space.robi add robi (Rect new))
(space sleep 500)
(space.robi.robi setDim 700 700)
(space sleep 500)
(space.robi.robi add img (Image new trex.jpg))
(space sleep 500)
(space.robi.robi.img translate 50 50)
(space sleep 500)
(space.robi del robi)
(space sleep 500)
(space.robi add robi (Oval new))
(space sleep 500)
(space.robi.robi setColor yellow)
(space sleep 500)
(space.robi.robi setDim 300 300)
```

La gestion des environnements n'a pas été facile puisqu'il a fallu réfléchir à une manière optimale pour l'ajout de nos éléments. En effet, utiliser un seul environnement était contre productif puisque si ce dernier était supprimé nous perdions tous nos éléments.

Le résultat de l'exercice :

![Exécution de l'Exercice 4.3](/exercice_4_3.gif)

### Exercice 4.4 : Création et exécution de scripts

***

## Tests finaux

Pour chaque exercice, la classe Main() déclenche un scénario de test. Puis une fois que le scénario est terminée, on récupère la main sur le terminal pour faire des entrées manuelles si on le souhaite.
Pour le dernier exercice (exercice 4.4) il y a deux classes Main() :
- Exercice4_4.java : Contenant la fonction MainLoop() classique.
- Exercice4_4_Tests.java : Contenant la fonction MainTests() qui inclut des 3 scénarios différents et qui fini par nous rendre la main sur le terminal.

***

## Bonus

Les images au format GIF n'était pas animé dans notre programme, et pour remédier à cela nous avons créé une nouvelle classe GGif.java au sein du package GraphicLayer et nous avons modifié la classe NewImage.java.

Dans la classe GGif, on implémente ImageObserver permettant de passer cette classe en paramètre de la méthode drawImage de Graphics2D. La méthode imageUpdate de l'interface, une fois redéfinie, nous permet de "repaint" le container à chaque mise à jour de l'image (dépendant du framerate du Gif)

L'instanciation du fichier a également été modifiée dans la classe NewImage. On vérifie le type de fichier image, et dans le cas d'un fichier Gif on procède ainsi :

```
	URL url = null;
	File monGif = null;
	try {
		monGif = new File(file);
	}catch(NullPointerException e) {
		System.out.println("Nom de fichier invalide : " + e);
	}

	try {
		url = monGif.toURI().toURL();
	} catch (MalformedURLException | IllegalArgumentException | SecurityException e ) {
		System.out.println("Erreur : " + e);
	}
	Image image = new ImageIcon(url).getImage();
	GGif img = new GGif(image);
```

Le résultat du bonus :

![Exécution du Bonus](/canard_hi.gif)

***

## Bilan critique

Ce projet m'a permis d'apprendre à utiliser des environnemnts 2D et des Frames au travers de nouvelles bibliothèques.

J'ai également appris à développer un semblant de langage objet au sein de Java.

La gestion des erreurs a été d'une grande importance afin que l'ensemble soit fontionnel et flexible.

Enfin j'ai pu m'investir et organiser mon temps afin de travailler de manière efficace sur chaque partie du projet.

