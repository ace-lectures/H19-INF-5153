# TP2 - Produit Minimal Viable (PMV)


## Consigne de remise

- A la racine de votre dépôt, vous devez livrer un rapport au format PDF, nommé `Rapport_XX_YY_ZZ_TT.pdf`, où XX, YY, ZZ et TT correspondent aux codes permanents des étudiants ayant participé au rendu.
- Le code rendu doit compiler et les tests d'acceptation s'exécuter avec la commande `mvn clean package` lancée à la racine de votre dépôt.
  - Si vous ne changez pas la structure donnée, c'est déjà le cas.


Votre rapport (format Letter, 10 pages max, police type Times en 11 pts) doit contenir les informations suivantes :

- Les modèles importants (p.ex., cas d'utilisation, classes, séquence, composants, déploiement), en identifiant pourquoi vous considérez que ces modèles sont importants pour l'application conçue;
- Une justification des choix de conception que vous avez faits;
  - Positionnement par rapport à GRASP et SOLID; 
  - Vous porterez une attention particulière sur les patrons de conception utilisé (mais aussi ceux que vous avez écartés). Qu'est-ce qu'ils apportent à votre conception, que se passerait-il si ils n'étaient pas utilisés, pourquoi ne pas avoir utilisé tel patron, ...
- Une identification des limites (points fixes et points de variations) de votre conception : qu'est-ce qu'il sera facile de faire évoluer, au contraire, qu'est-ce qui est figé ?
- Un court paragraphe de gestion de projet explicitant comment vous avez développé le projet, et qui a fait quoi.

L'exercice d'écriture du rapport est un exercice de synthèse, la contrainte des 10 pages max (tout compris) est ferme. Vous pouvez vous inspirer des questions de recul de la première partie du TP pour vous aider sur le contenu (et vous avez aussi les heures de dispos sans rendez vous, les démos et le slack pour échanger à ce propos).

## Travail à réaliser

Suite à la première phase d'expérimentation, _La Fabrique de Biscuits_ souhaite ajouter les trois fonctionnalité suivantes dans le système. 

Il est attendu de chacune des fonctionnalités d'être _(i)_ accessible depuis l'interface en ligne de commande et _(ii)_ livrée avec un (ou plusieurs) scénario d'acceptations démontrant son usage. 

Il est attendu de l'équipe de développement de produire un code conforme aux bonnes pratiques de conception (GRASP, SOLID, patrons, ...) vue en cours.

### Sélection du point de cueillette

Le client doit pouvoir spécifier lors de sa commande dans quel point de vente de _La Fabrique de Biscuits_ il souhaite récupérer ses biscuits, et à quelle heure. Cette horaire doit être compatible avec les horaires d'ouverture du point de cueillette (les horaires peuvent varier en fonction des boutiques), et on n'acceptera pas une commande avec moins d'une heure entre la commande et la récupération.

### Personalisation des biscuits

En plus des recettes prédéfinies déjà en vente dans le système, on souhaite permettre aux clients de personaliser leurs recettes. Ils peuvent ainsi composer leurs propres biscuits (selon les contraintes définies au démarrage du projet), et le prix de la recette personnalisée est égale à la somme du prix de ses ingrédients. 

### Client Privilégié

Les clients réguliers deviennent des clients privilégiés dès qu'ils ont dépensés _42$_ sur le système de vente de _Biscuit à la Demande_. Une fois obtenu ce status, ils ont le droit de ne pas payer leur commande en ligne, mais plutôt de la régler en boutique. Ils obtiennent aussi un rabais de 10% sur leur commande, toutes les 10 commandes.

## Travail à NE PAS réaliser

  * Il n'est pas demandé de se connecter à une base de données, ou quoi que ce soit d'autre relatif à l'initialisation des données. Vous devez fournir un système _minimal_ (avec des initialisation en dur pour les prix des ingrédients, les boutiques, leurs horaires, ...), et qui pourra évoluer vers un vrai système par la suite.
  * Identification unique des clients : tous les clients du système ont la bonne propriété d'avoir tous des noms différents, qui leur permette d'échanger avec le système. (En vrai on pourrait considérer que le `name` de la Facade est un `login` unique).
  * Il est possible qu'un client fabrique de manière personnalisée une recette de biscuit correspondant à une recette prédéfinie, et qu'il le paye plus cher que s'il avait choisi la recette toute faite. La vie est injuste, tant pis pour lui.