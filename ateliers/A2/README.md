# Atelier A2 : Le Jeu de Poker

  * Auteur : [Sébastien Mosser](mosser@i3s.unice.fr)
    * la version française de la description du problème à été écrite par Philippe Collet. 
    * Relecture: Charline David
  * Version : 2019.1
  * Durée : 3 sessions de 2h (dont une non encadrée)

### Objectifs

  1. Analyser un code Java pour en extraire un diagramme de classes et un diagramme de séquence;
  2. Identifier les responsabilités des objets sur un problème simple (_S_ de _SOLID_);
  3. Proposer un système ouvert à l'extension et fermé à la modification (_O_ de _SOLID_).

### Description du problème

Le problème du _Jeu de Poker_ est un exercice de programmation assez classique, décrit sur le site [Coding Dojo](http://codingdojo.org/kata/PokerHands/). 

  * Une main de poker comprend 5 cartes tirées d’un seul jeu de 52 cartes. Chaque carte à : 
    * une `couleur`, Trèfle, Carreau, Coeur, Pique (dénotée `C`, `D`, `H`, `S`), et 
    * une valeur parmi 2, 3, 4, 5, 6, 7, 8, 9, 10, valet, dame, roi, as (dénotée `2`, `3`, `4`, `5`, `6`, `7`, `8`, `9`, `T`, `J`, `Q`, `K`, `A`). 
  * Pour le calcul du score, toutes les couleurs ont le même niveau, par exemple l’as de carreau n’est pas battu par l’as de pique, ils sont égaux. 
  * Les valeurs sont ordonnées comme définies précédemment, le 2 étant la plus petite valeur et l’as la plus grande.
  * Une main de poker est faite de 5 cartes. 

Le croupier va saisir les deux mains successivement, en séparant chaque main par un retour chariot. Les mains sont saisie sous la forme de chaine de caractères, chaque carte séparée par un ou plusieurs espaces. Par exemple, `2C 6D 7D 8C AS` représente la main composée du 2 de trèfle, du 6 de carreau, du 7 de carreau, du 8 de trèfle et de l'as de pique. 

Une fois les deux mains saisies, le système affiche le nom du joueur gagnant (parmi `PLAYER_1`, `PLAYER_2`), ou `TIE` en cas d'égalité entre les deux mains.

Dans le texte ci-dessous, les mains sont classées de la plus faible à la plus forte :

  * _Plus haute carte_ : les mains qui ne correspondent à aucune autre catégorie sont classées par la valeur de leur plus haute carte. Si les plus hautes cartes ont la même valeur, les mains sont classées par la plus haute suivante et ainsi de suite.
  * _Paire_ : 2 des 5 cartes de la main ont la même valeur. Deux mains qui contiennent une paire sont classées par la valeur des cartes formant la paire. Si les valeurs sont les mêmes, les mains sont classées par les cartes hors de la paire, en ordre décroissant.
  * _Deux paires_ : La main contient deux paires différentes. Les mains qui contiennent deux paires sont classées par la valeur de la paire la plus élevée. Deux mains avec la paire la plus élevée de même valeur sont classées par l’autre paire. Si ces valeurs sont les mêmes, les mains sont classées par la valeur de la carte restante.
  * _Brelan_ : 3 cartes dans la main ont la même valeur. Deux mains avec un brelan sont classées par la valeur des 3 cartes.
  * _Suite_ : 5 cartes de valeurs consécutives. Deux suites sont classées par la valeur de leur carte la plus élevée.
  * _Couleur_ : La main contient 5 cartes de la même couleur. Deux mains “couleur” sont classées par les règles de la carte la plus élevée.
  * _Full_ : La main contient  3 cartes de la même valeur avec les 2 cartes formant une paire, le classement se fait par la valeur des 3 cartes.
  * _Carré_ : 4 cartes de la même valeur, classement par la valeur des 4 cartes.
  * _Quinte Flush_ : 5 cartes de la même couleur avec des valeurs consécutives, classement par la carte la plus élevée dans la main.

## Étape 1 : Récupérer le code sur Classroom

  * Rendez vous à l'adresse suivante pour récupérer le code de démarrage:
      * [TODO]() 
  * Assurez vous que le code compile dans votre environnement en utilisant la commande :
    * `~/tp2 mosser$ mvn clean package`
  * Assurez vous que le projet s'exécute dans un terminal : 
    *  `~/tp2 mosser$ mvn exec:java`
  * Importez le projet dans votre environnement de développement préféré (p. ex, IntelliJ, Eclipse, Visual Code, Netbeans).


## Étape 2 : Comprendre la conception existante

Le code que vous avez récupéré à l'étape précédente contient les classes suivantes : 

  * `Card` représente une carte du jeu, en associant une valeurs (prise dans l'énumération `Values`) et une couleur (prise dans l'énumération `Suits`). 
      * Elle définit une méthode `compareTo` qui permet de définir une relation d'ordre sur les cartes pour les comparer.
  *  `Hand` représente la main d'un joueur, composée d'un ensemble de 5 cartes.
      *  Elle définit une méthode `isValid()` permettant de s'assurer que la main contient bien 5 cartes.
  *  `HandBuilder` est une _fabrique_ de main de poker, qui, sur la base d'une chaine de caractères conforme à la spécification, produit l'instance de `Hand` correspondante.
  *  `PokerController` définit la partie en interaction avec le croupier, en définissant la méthode `main` du système.

### Travail à faire 


  * A l'aide de votre environnement de modélisatio préféré (ceci incluant papier et crayon),
    1. Dessinez le diagramme de classe de l'application actuelle, en omettant ce qui relève du détail d'implémentation; 
    2. Dessinez le diagramme de séquence principal de l'application, en omettant ce qui relève du détail d'implémentation.

  * Discussion sur la conception actuelle : 
    1. Construction de la main avec un Builder / dans le constructeur
    2. Clone du set de cartes dans la Main pour accéder au contenu
    3. Tolérance aux erreurs dans la construction des mains
    4. Composition / association entre `Hand` et `Card`
    5. Multiplicité de `contents` dans `Hand`
    6. PokerController en tant que Main

  * Pour l'instant, la méthode `isValid` de la classe `Hand` n'est pas utilisée.
    1. Identifiez les endroits où cette méthode pourrait être appelée pour garantir la validité des mains saisies.
    2. Quel est l'impact de choisir l'un ou l'autre de ces endroits dans le code pour vérifier la validité ? 


## Étape 3 : Détection des Combinaisons

On s'intéresse ici aux principes de (i) responsabilité unique (_Single responsibility_) et (ii) d'ouverture à l'extension / fermeture à la modification (_Open / closed_). 

L'idée est de proposer un système qui permettra facilement l'ajout de nouvelle combinaisons dans le système, et de démontrer son utilisation en développant deux combinaisons dans le système : _Plus Haute Carte_ (_Highest Card_) et _Paire_ (_TwoOfAKind_).

Le système doit être capable de détecter, pour une main donnée, toutes les combinaisons présente dans celle-ci. En effet, certaines combinaisons s'incluent mutuellement : un _Carré_ inclue une _Double Paire_, un _Brelan_ et quatre _Paires_. 

### Travail à faire 

  1. Identifiez les classes (leur structure _ET_ leur comportement) permettant de représenter les bonnes abstractions pour ce problème;
  2. Montrez à l'aide d'une diagramme de séquence comment les combinaisons sont détectées dans une main;
  2. On doit pouvoir ajouter de nouvelles combinaisons facilement. Comment votre conception permet-elle cela ? 
  3. Proposez une implémentation en Java de votre travail.

## Étape 4 : Détection du Vainqueur

Sur la base des détections de l'étape précédente, la plus haute combinaison parmi celle détectées est calculée pour chaque main, puis une décision d'arbitrage est rendu pour identifier quelle main gagne parmi les deux soumises (ou égalité).

Java propose l'interface `Comparable`, déjà utilisée dans la classe `Card` pour permettre de comparer deux instances de la même classe. 

### Travail à faire

  1. Implémentez l'interface `Comparable` dans votre abstraction des combinaisons;
  2. Identifiez les responsabilités nécéssaire à la réalisation de l'arbitrage;
  3. Modifiez le diagramme de séquence global pour intégrer la prise de décision dans le système;
  4. Implémentez cette modification dans votre code Java.


## Étape 5 : Détection de la triche (Optionnel)

Pour l'instant, on fait l'hypothèse que les mains fournie sont exempte de triche, et on se contente de vérifier qu'elles sont syntaxiquement valide (5 cartes distinctes). 

Or, un tricheur pourrait utiliser une carte de sa manche plutôt qu'une carte du jeu original, et on pourrait se retrouver avec 2 cartes identique, une dans chaque main. La detection de la triche dépasse le simple problème de lecture d'une main.

### Travail à faire

  1. Identifiez les responsabilités nécéssaire à la réalisation de la detection de triche;
  2.  Modifiez le diagramme de séquence global pour intégrer la detection de la triche dans le système;
  4. Implémentez cette modification dans votre code Java.




