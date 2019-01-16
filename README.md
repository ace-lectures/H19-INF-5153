# INF5153 - Génie logiciel: Conception

## Informations Générales

  * Équipe : 
    * Professeur : [Sébastien Mosser](https://mosser.github.io)
    * Démonstrateur : Charline David 
  * Horaire du groupe `030`, session d'hiver 2019:
    * Cours : Mercredi, 18h - 21h, local PK-R605
    * Atelier : Jeudi, 18h - 20h, local PK-S1540 (mais va surement bouger en S1555)
  * Communication : 
    * Disponibilité sans rendez-vous : Mercredi, 15h45 - 17h45, local PK-4820
    * Slack : [https://inf5153-h19.slack.com/signup](https://inf5153-h19.slack.com/signup) 
      * (**politique zéro courriel stricte**)

### Description du cours 

_Sensibiliser l'étudiant aux difficultés de la conception et lui permettre d'élaborer des solutions réutilisables, maintenables et extensibles. Problématique du processus de conception. Critères et architecture. Conception comme activité créatrice. Outils d'aide à la conception. Intégration et essais système. 
Conception orientée objet. Cadres d'application et patrons de conception. Documentation de conception. Rétro ingénierie._

  * Préalables académiques
    * [INF-5151](https://etudier.uqam.ca/cours?sigle=INF5151), Génie logiciel: analyse et modélisation ; 
    * [INF-3135](https://etudier.uqam.ca/cours?sigle=INF3135), Construction et maintenance de logiciels.

### Évaluation & Planning de rendus

| Date(s)  | Travail à rendre | Objectif | Poids |
| :---:   | :---   | :---    | :---: |
| 16.01 ➝ 10.02 | TP1 |  Conception guidée, en lien avec l'implémentation | 10% |
| 20.02 | :notebook: **Examen intra** | Principes fondamentaux de la conception | 20% |
| 21.02 ➝ 17.03 | TP2 - PMV | Concevoir et développer un produit minimal & viable  | 10% |
| 18.03 ➝ 28.04 | TP2 - Complet | Corriger une conception, intégrer des évolutions  | 20% |
| 24.04 | :notebook: **Examen final** | Principes fondamentaux & avancés de la conception | 40% |


Pour les Travaux Pratiques, le rendu se fait à travers la plateforme GitHub Classroom. Les TPs sont a réaliser par équipe. Les dépôts de code seront clonés automatiquement par un script, et tout travail non rendu via ce biais ou hors délais ne sera pas évalué.  La couverture _fonctionelle_ de vos TPs est automatiquement vérifiée par la bonne exécution de scénarios _Cucumber_.

L'examen _intra_ portera sur les séances des semaines #2 à #7. L'examen _final_ portera sur les séances des semaines #2 à #15. La séance de la semaine #16 est une ouverture pour votre culture générale. Pour les examens, vous avez le droit à une feuille de notes manuscrites (format _Letter_, recto-verso).

## Agenda des séances

En régime régulier, les cours ont lieu le mercredi et les ateliers le jeudi. Les exceptions à la règle sont listées ci-dessous :

  - Semaine #6 : Déplacement pro (conférence). Le cours est remplacé par un atelier (_local & horaire à définir_).
  - Semaine #7 : L'atelier est remplacé par un cours pour rattraper la semaine 6 (_local & horaire à définir_)

| #Semaine | Cours (Mercredi, 3h) | Ateliers (Jeudi, 2h) |
| :---:   | :---   | :---    |
| #2      |  [Introduction: Socle Technique & Principes de Conception Objet](./cours/02) |   |
| #3      |  Rappels sur UML, Propriétés architecturales | (A1) Boite à outils  |
| #4      |  Responsabilisation : GRASP & SOLID | (A1) _suite_ |
| #5      |  UML pour la conception détaillée | (A2) Conception & Implémentation |
| #6      |  (A2) _suite_ | (A2) _suite_   | 
| #7      |  Retours sur le TP1, Révisions|  Patrons de conceptions GoF (_initié_) |
| **#8**  | **Examen intra**   |   |
| _#9_    | _Semaine de relâche_   |   |
| #10     |  Patrons de conceptions GoF (_padawan_) | (A3) Patrons & Mise en oeuvre  |
| #11     |  Patrons de conceptions GoF (_chevalier_) | (A3) _suite_ |
| #12     |  Patrons de conceptions GoF (_maitre_) |  (A3) _suite_  |
| #13     |  Anti-patrons | (A4) Détection d' (anti-)patrons  |
| #14     |  Maintenance et réusinage (_refactoring_) | (A4) _suite_  |
| #15     |  Principes du _Domain-Driven Design_  |  Finalisation TP  | 
| #16     |  _(culture)_ Architectures Hexagonales |  Finalisation TP  |
| **#17** |  **Examen final** |  |


## Travaux

### Ateliers (encadrés)

  * A1 : Micro-brasserie interactive
    * Objectifs : Maitriser l'outillage de base (GitHub classroom, travis-CI, maven, git, junit, visual paradigm & cucumber).
  * A2 : Le jeu de Poker
    * Objectifs : Concevoir et développer une application orientée objet.
  * A3 : Simulateur de _Bestioles_
    * Objectifs : Intégrer des patrons de conception dans une application orientée objet.
  * A4 : Détéction et réparation d'anti-patrons
    * Objectif : Initiation à la rétro-ingénierie des applications objets.

### Travaux pratiques (à rendre)

Les travaux pratiques sont a faire en équipe de 3 à 4 étudiants. Vous êtes fortement encouragés à utiliser Slack et les disponibilités sans rendez vous pour obtenir des retours sur vos
travaux pratiques avant les livraisons finales. 

  * TP1 : Bibliothèque Universitaire 
  * TP2 : La Fabrique de Biscuits 
    * Version intermédiaire : _Produit Minimal & Viable_ 
    * Version finale : _Produit Complet_  

_Il est possible d'obtenir des créneaux de rendez-vous pendant les temps d'atelier avec le professeur pour discuter des 
Travaux Pratiques à rendre **si vous êtes en situation d'emploi et ne pouvez pas venir sur le créneau sans rendez-vous précédant le cours**._

## Bibliographie

  * _UML@Classroom_, Springer Verlag, 2015.
    * Martina Seidl, Marion Scholz, Christian Huemer & Gerti Kappel. 
  * _Software Systems Architecture: Working With Stakeholders Using Viewpoints and Perspectives_, Addison Wesley, 2011.
    * Nick Rozanski & Eoin (_pronounced “Owen”_) Woods. 
  * _Implementing Domain-Driven Design_, Addison-Wesley Professional, 2013.
    * Vaughn Vernon 
  * _Design Patterns: Elements of Reusable Object-Oriented Software_, Addison Wesley, 1994.
    * Erich Gamma, Richard Helm, Ralph Johnson & John Vlissides.
  * _Refactoring: Improving the Design of Existing Code_, Addison Wesley, 2018 (2nd edition)
    * Martin Fowler.  

