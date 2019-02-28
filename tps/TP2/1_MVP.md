# TP2 - Produit Minimal Viable (PMV)

  * Date : 28 février 2019 - 24 mars 2019
  * Durée : 3 semaines (ateliers + travail perso)

## Consignes de remise

A date, votre dépôt sera automatiquement cloné et son contenu récupéré.

  - Votre code doit compiler sans erreur (terminer avec `BUILD SUCCESS`) avec la commande suivante lancée à la racine de votre projet :
    - `mvn clean package -DskipTests`
  - Vos scénarios d'acceptations doivent se lancer depuis la console avec la commande suivante (lancée depuis la racine de votre projet), et se terminer sans erreur :
    - `mvn -q test`   
  - Les réponses aux questions du TPs doivent se trouver dans un fichier `README.md` à la racine de votre dépôt. 

Pour le code, si votre projet est dans l'état `build passing` sur Travis, tout est correct.


## Travail a réaliser

### Étape 1 : Exécution du code fourni

Vous disposez d'un code de démarrage qui vous est fourni quand vous acceptez le travail à faire sur Github Classroom.

**DANS UN TERMINAL**, compilez le code fourni et lancez son execution avec les commandes suivantes :

```
azrael:H19-TP2-skel mosser$ mvn clean package
[INFO] Scanning for projects...
[INFO] 
[INFO] ---------------------< uqam.info.ace.inf5153:tp2 >----------------------
[INFO] Building UQAM :: INF-5153 :: TP2 1.0-SNAPSHOT
[INFO] --------------------------------[ jar ]---------------------------------

...

[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  4.344 s
[INFO] Finished at: 2019-02-27T19:08:09-05:00
[INFO] ------------------------------------------------------------------------

azrael:H19-TP2-skel mosser$ mvn -q exec:java

Starting Cookie on Demand by The Cookie Factory
Interactive shell started. ? for help.

CoD > ?
  - bye: Exit the Cookie on Demand system
  - recipes: List the contents of the cookie menu
  - list: list cart contents (list CUSTOMER_NAME)
  - order: Add (or remove) cookies in a cart (order CUSTOMER_NAME COOKIE_NAME QUANTITY)
  - process: process cart contents (process CUSTOMER_NAME)
  - start: create an order for a customer (start CUSTOMER_NAME)

CoD > bye

Exiting Cookie on Demand by The Cookie Factory

azrael:H19-TP2-skel mosser$

```

Vous pouvez _jouer_ avec les commandes fournies dans le _shell_ interactif. Pour l'instant, le système ne fait absolument rien et se contente d'afficher ce que vous lui avez demandé de faire.

```
azrael:H19-TP2-skel mosser$ mvn -q exec:java

Starting Cookie on Demand by The Cookie Factory
Interactive shell started. ? for help.

CoD > start seb
Feb 27, 2019 7:11:11 PM uqam.info.inf5153.tp2.cod.NaiveCoD createEmptyCart
INFO: creating an empty cart for seb

CoD > recipes
Feb 27, 2019 7:11:28 PM uqam.info.inf5153.tp2.cod.NaiveCoD getAvailableRecipes
INFO: retrieving available cookies recipes 

CoD > order seb CHOCOLALALA 3
Feb 27, 2019 7:11:48 PM uqam.info.inf5153.tp2.cod.NaiveCoD addToCart
INFO: ordering [CHOCOLALALA, 3] for seb

CoD > order seb CHOCOLALALA -1
Feb 27, 2019 7:12:22 PM uqam.info.inf5153.tp2.cod.NaiveCoD addToCart
INFO: ordering [CHOCOLALALA, -1] for seb

CoD > process seb
Feb 27, 2019 7:12:37 PM uqam.info.inf5153.tp2.cod.NaiveCoD sendToKitchen
INFO: sending to kitchen seb's order

CoD > bye

Exiting Cookie on Demand by The Cookie Factory
```

Vous pouvez maintenant importer ce code dans votre _IDE_ favori. Si votre IDE support Cucumber, il serait interessant d'installer le plug-in associé.

### Étape 2 : Scénarios d'acceptation

Regardez plus en détail ce qui se passe quand vous compilez votre projet, plus précisément durant la phase de tests : 

```
azrael:H19-TP2-skel mosser$ mvn -q test

-------------------------------------------------------
 T E S T S
-------------------------------------------------------
Running RunCucumberTest
...............................P
Pending scenarios:
OrderCookie.feature:33 # "As Carter, I want to send my cart to the system so that I'll pick up my cookies at some point"

5 Scenarios (1 pending, 4 passed)
32 Steps (1 pending, 31 passed)
0m0.217s

cucumber.api.PendingException: Change me!
	at steps.OrderCookieSteps.carter_has_a_receipt_available(OrderCookieSteps.java:66)
	at ?.Carter has a receipt available(OrderCookie.feature:38)


Tests run: 5, Failures: 0, Errors: 0, Skipped: 1, Time elapsed: 0.458 sec

Results :

Tests run: 5, Failures: 0, Errors: 0, Skipped: 1
```

A chaque compilation, lors de la phase de tests, les fichiers `*.feature` stockés dans le repertoire `src/test/resources` sont exécutés. Pour le moment, il y a un seul fichier, `OrderingCookies.feature`. 

Ce fichier contient un `Background`, qui est commun à tous les scénarios. Dans notre cas, il initialise un nouveau système _BalD_, et déclare un nouveau client appelé _Carter_

```cucumber
Background: This context is true for all the upcoming scenarios
  Given a fresh CoD system
    And a customer named Carter who want to buy a cookie
```

Chaque étape du scénario est apparié à du code, sur la base d'une expression rationnelle (ici dans la classe `steps.OrderCookieSteps` : 

```java
private CookieOnDemand cod;

@Given("^a fresh CoD system$")
public void initializeSystem() {
    cod = CookieOnDemand.build();
}

@Given("^a customer named (.*) who want to buy a cookie$")
public void initializeCustomer(String customerName) {
    cod.createEmptyCart(customerName);
}    
```

Pour l'instant, les assertions (les `@Then`) ne sont pas vérifiée, on y viendra plus tard.

Travail a faire : 

 - Lisez le code des scénarios d'acceptation et celui des étapes associée en Java
 - Ajoutez un scénario d'acceptation de votre choix qui réutilise les étapes existantes
 - Vérifiez sa bonne exécution.

### Étape 3 : Implémentation de _BalD_

La spécification du système _BalD_ est décrite dans l'interface `CookieOnDemand` du package `uqam.info.inf5153.tp2.cod`. Le système actuel est implémenté dans la classe `NaiveCoD`, qui fait simplement appel à un _logger_.


Votre mission est maintenant de concevoir et d'implémenter un système objet qui permette de répondre à cette spécification, dans le respect des principes _GRASP_ et _SOLID_.


Travail à réaliser : 

  - Définissez une architecture orientée objet pour supporter le métier de la vente de biscuit;
  - Créez une nouvelle classe implémentant l'interface `CookieOnDemand` et qui utilise votre système objet;
  - Modifiez la méthode statique `build` de l'interface `CookieOnDemand` pour qu'elle retourne une instance de votre classe et plus une instance de `NaiveCoD`
    - Quel patron de conception est utilisé ici ? Quel est son utilité ? 
  - Modifiez les assertions faites dans les tests d'acceptation pour que les scénarios valident votre système
  - Écrivez de nouveaux scénarios d'acceptation (et si nécessaire ajoutez des étapes) qui vérifie les cas d'erreurs des spécifications.

### Étape 4 : Modification de l'interface utilisateur

L'interface en ligne de commande est implémentée dans le package `cli` (_command line interface_). Chaque commande disponible implémente étend la classe `Command`, et travaille sur une instance de `CookieOnDemand`.

  - Quel patron de conception est utilisé ici (indice : c'est marqué dessus)? Le patron n'est pas complètement respecté ... 
    - Quelles sont les déviations par rapport au patron "standard" ?
    - Pourquoi sont-elles présente ?

Il n'est pour l'instant pas possible avec la CLI d'obtenir le reçu une fois la commande envoyée à la cuisine.

Travail à réaliser : 

  - Rajoutez une nouvelle commande dans le paquetage `cli.commands` qui permette la récupération du reçu
  - Enregistrez cette nouvelle commande dans la classe `InteractiveClient` afin de la rendre disponible
  - Relancez l'application en ligne de commande et vérifiez la bonne execution de votre nouvelle commande

#### Pour aller plus loin (facultatif, non évalué, mais fun à faire)

On a du _modifier_ la classe `InteractiveClient` pour rendre disponible la nouvelle commande ... c'est pas très conforme avec le principe _ouvert/fermé_. Comment pourrait on faire en sorte d'enregistrer automatiquement toutes les classes qui héritent de la classe `Command` ? (Indice : regardez l'API de réflexivité de java comme celle fournie par la bibliothèque [reflections](https://github.com/ronmamo/reflections))

### Étape 5 : Une nouvelle fonctionnalité, le paiement

Le modèle d'affaire de _BalD_ n'est pas correct, on ne peux pas faire d'argent avec, puisque les clients ne peuvent pas acheter les biscuits ! 

On accepte les paiements par carte de crédit, en envoyant au système le nom du client, son numéro de carte de crédit, et le montant a payer. 

Travail à réaliser : 

  - Ajoutez la possibilité de donner un prix fixe à une recette de biscuit;
  - Étendez l'interface `CookieOnDemand` pour permettre : 
    - le calcul du prix d'un panier
    - le paiement d'un panier;
  - Étendez les scénarios d'acceptations pour valider votre nouvelle fonctionnalité

### Étape 6 : Validation des commandes

On ne peut envoyer en cuisine que les commandes qui ont été préalablement payée, et on ne peut plus modifier une commande une fois son envoi en cuisine. 

  - Quel patron de conception est adapté a la mise en place de cette fonctionnalité ?

Travail à réaliser : 

  - Modifiez votre architecture objet pour supporter cette nouvelle fonctionnalité
  - Écrivez des scénarios de validation qui permette de la valider. 
 
### Étape 7 : Ré-usinage fonctionnel

L'interface `CookieOnDemand` est peu cohésive, elle regroupe pleins de fonctionnalité différentes. Pourtant son rôle est essentiel pour servir de zone tampon isolant le monde extérieur (ici la CLI) de votre architecture objet.

  -  Quel patron de conception est ici mis en oeuvre ?

Travail à réaliser : 

  - En appliquant le principe de ségrégation des interfaces, proposez de nouvelles interfaces qui soient plus cohésives pour regrouper les fonctionnalités;
  - Ré-usinez votre code en déplaçant des méthodes pour définir les classes implémentant ces nouvelles interfaces;
  - Modifiez votre classe implémentant `CookieOnDemand` pour qu'elle fasse le pont vers vos nouvelles classes;


#### Pour aller plus loin (facultatif, non évalué, mais fun à faire)

Ces nouvelles classes et interfaces sont en fait des _composants logiciels_ au sens d'UML. Arrivez vous a faire le lien entre votre code et un diagramme de composants ?