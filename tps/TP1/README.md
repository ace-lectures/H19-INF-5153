# TP1 : La Bibliothèque Universitaire

  * Auteurs : Philippe Collet, Benjamin Benni & Sébastien Mosser
  * Version : UQAM-H19
  * Durée : 3,5 semaines
 
 
## Informations Importantes

  * Travail a réaliser par groupe de 3 à 4 étudiants;
    * Les groupes ne respectant pas cette contrainte ne seront pas évalués.
    * Le premier étudiant créé l'équipe sur _Classroom_, puis les autres rejoignent cette équipe. Ce sont les informations présentes dans _Classroom_ qui feront foi pour l'évaluation, faite attention.
  * Récupérez le travail sur Github Classroom:
    * TODO []() 
  * Par modèle, on entend dans ce travail les trois types de modèles UML suivants : cas d'utilisation, classes et séquence. 


### Dates importantes[^dates]

  * Date de formation des équipes : 22.01.19, 23h50
  * Date de rendu des travaux : 10.02.19, 23h50
  * Date maximale de rendu des notes : 17.02.19, 23h50 (donc avant l'intra)

**Aucun rendu ne sera accepté après la date de clôture automatique des dépôts**.
 
### Évaluation
 
  * Rapport : 40 points 
  * Qualité du code objet : 30 points
  * Scénarios d'acceptations : 30 points

Le rapport peut être rédigé en français ou en anglais, selon le choix des équipes. Un rapport de mauvaise qualité (forme, orthographe, grammaire, ...) se verra attribué un malus.

Votre participation sur le Git sera utilisée pour pondérer votre note en fonction de l'effort de développement mis dans le projet. Assurez vous de régler votre environnement pour que vos _commits_ soit reliés à votre véritable identité (voir atelier `A1`).
 
## Description du problème

On souhaite informatiser la bibliothèque universitaire de l'UQAM, et on fait l’hypothèse qu’il n’y a pas déjà de système existant. 

Cette bibliothèque propose aux étudiants de l’Université des livres à emprunter. 

Chaque document est identifié par un numéro unique. Un livre est caractérisé par un titre, un nom d’éditeur et un ou plusieurs auteur(s). Un livre peut être emprunté ou consulté sur place.

Les étudiants sont identifiés par les informations associées à leur carte UQAM : leur code permanent, un nom, un prénom et une adresse. Ils peuvent consulter sur place, effectuer des recherches de documents par titre ou nom d'auteur en utilisant le système d'information de la bibliothèque.

Chaque livre emprunté par un étudiant précis est connu du système d’information de la bibliothèque : l’étudiant donne le livre à emprunter à la bibliothécaire à la caisse de sortie, avec sa carte UQAM. Pour rendre un livre, un étudiant le place simplement sur des étagères spécifiques à la caisse et régulièrement, les bibliothécaires utilisent le système pour remettre le livre dans le fond de la bibliothèque, puis physiquement dans la bonne étagère de présentation.
 
 
## Première itération : Produit minimal et viable

  1. Définir le glossaire du domaine (en considérant uniquement le périmètre simplifié qui vient de vous être donné)
  2. Définir un premier ensemble  : 
    - d’acteurs et cas d’utilisation, sans forcément les relier entre eux pour l’instant
    - de concepts du domaine qui pourraient former des classes dans un diagramme de classes
  3. Faire un premier diagramme de cas d’utilisation qui couvre les acteurs et les cas déterminés (ne cherchez pas à faire compliqué pour le moment)
  4. Prendre le cas d’utilisation que vous considérez le plus important et définir un diagramme de classes et un diagramme de séquences correspondant et cohérent.
  5. Procéder cas par cas pour arriver à un à un diagramme de classes et aux diagrammes de séquence correspondants, tous cohérents avec le diagramme de cas d’utilisation de l’étape 3.
  6. Développer le code (métier, tests unitaire et tests d'acceptation) qui supportent cette conception.

## Seconde itération : Complexification métier

Après plusieurs réunions avec des représentants des bibliothèques universitaires, plusieurs besoins additionnels doivent être intégrés :
  
  * La bibliothèque propose aux étudiants et aux enseignants de l’université des livres et des revues. 
  * Ces livres comme ces revues sont acquis auprès d’éditeurs qui proposent leurs nouveautés par l'intermédiaire de catalogues. 
  * Les choix d'acquisition ou d'abonnement sont pris en fonction du budget de la bibliothèque et des demandes des enseignants des différents départements de l’université.
  * Chaque document est identifié par un numéro unique. Un livre est caractérisé par un titre, un nom d’éditeur et un ou plusieurs auteur(s). Les revues sont caractérisées par un titre et la périodicité de leur parution. 
  * S’il existe plusieurs exemplaires d’un livre, chaque exemplaire a une cote qui lui est propre. Les revues sont consultables sur place uniquement et la bibliothèque ne dispose que d’un seul exemplaire de chacun des numéros de revue.
  * Un livre peut être emprunté ou consulté sur place.
  * Les étudiants et enseignants qui souhaitent emprunter des livres sont identifiés par un numéro, un nom et une adresse (département d’appartenance pour les enseignants). 
  * Il peuvent consulter sur place, effectuer des recherches de documents par titre ou nom d'auteur en utilisant le système d'information de la bibliothèque. Lorsque le résultat de la requête porte sur un numéro de revue, son sommaire (liste des titres des principaux articles) est affiché.
  * On ne peut pas emprunter plus de 3 livres en même temps, et la durée maximum d’un prêt est de 15 jours pour un étudiant et de 1 mois pour un enseignant. 
  * Si un livre n’est pas disponible, il peut le réserver. 
  * Les enseignants sont relancés par courrier électronique lorsqu’ils ne rendent pas leurs livres dans les délais. Les étudiants, relancés par courrier et par sms, qui n’ont pas rendu les livres qu’ils ont empruntés dans les délais ne peuvent pas emprunter de livres pour une durée égale au dépassement du délai, et cela à partir de la date de restitution des livres.

### Travail à réaliser 

  * Identifier dans ces nouvelles spécifications ce qui fait partie de votre système et ce qui n'en fait pas partie;
  * Faite évoluer vos modèles et votre code pour permettre de supporter ces nouvelles fonctionalités

## A Rendre

  * Avant la date de clôture, vous poserez sur le _commit_ correspondant à votre rendu le tag `final` (n'oubliez pas de pousser ce tag sur le dépôt, par exemple avec la commande `git push --tags`);
  * A la racine de votre dépôt, vous devez livrer un rapport au format PDF, nommé `Rapport_XX_YY_ZZ_TT.pdf`, où `XX`, `YY`, `ZZ` et `TT` correspondent aux codes permanents des étudiants ayant participé au rendu.

  
Votre rapport (format Letter, 10 pages max, police type Times en 11 pts) doit contenir les informations suivantes : 

  * Les modèles _importants_ correspondant à la version finale,
    * en identifiant ce qui a du être modifié entre la première itération et la seconde;
    * en identifiant pourquoi vous considérez que ces modèles sont _important_ pour l'application conçue;
  * Une justification des choix de conception que vous avez fait pour la version finale;
  * Une identification des limites (points fixes et points de variations) de votre conception : qu'est-ce qu'il sera facile de faire évoluer, au contraire, qu'est-ce qui est figé ?
  * Un court paragraphe de gestion de projet explicitant comment vous avez développé le projet, et qui a fait quoi.


## Pour aller plus loin : Itération Bonus

Pour les équipes intéressées pour aller plus loin, vous pouvez considérer les évolutions de spécification suivantes. Attention, ce travail ne sera pris en compte que si le reste du travail rendu à une note > 75. Il pourra donner un bonus de 10 points maximum sur la note totale du travail, la note maximale restant 100.

  * Un adhérent qui ne rend pas le livre qu’il a emprunté à la date prévue est relancé 2 fois, à une semaine d’intervalle.
  * Sur un même livre, il ne peut pas y avoir plus de réservation que de nombre d’exemplaires de ce livre. Les réservations sont évidemment ordonnées.
  * Lors d’une réservation, une date potentielle de disponibilité est donnée : elle est calculée en fonction de :
    * la date d’emprunt de l’exemplaire qui correspond à sa place dans la liste d’attente (si on est 4ème, c’est la date d’emprunt du 4ème exemplaire plus ancien qui est utilisée);
    * couplée à la durée moyenne de prêt de ce livre, calculée sur les deux dernières années.
  * Si le livre n’est toujours pas rendu 1 semaine après la dernière relance, il est considéré comme perdu (jusqu’à ce qu’éventuellement l’adhérent ramène le livre à la bibliothèque) et l’adhérent est interdit de prêt. S’il y a une réservation attenante à ce livre perdu, elle est annulée et un email est envoyé à celui ou celle qui avait fait cette réservation.

### Travail à réaliser 

  * Identifier dans ces nouvelles spécifications ce qui fait partie de votre système et ce qui n'en fait pas partie;
  * Faite évoluer vos modèles et votre code pour permettre de supporter ces nouvelles fonctionalités





[^dates]: Les horaires de rendus s'entendent en _Heure Normale de l'Est_.
