# TP1 : La Bibliothèque Universitaire

  * Auteurs : Philippe Collet (UCA), Benjamin Benni (UCA) & Sébastien Mosser (UQAM)
  * Relecteur : Guy Tremblay (UQAM), Naouel Moha (UQAM)
  * Version : UQAM-H19
  * Durée : 3,5 semaines
 
 
## Informations Importantes

  * Travail a réaliser en Java par groupe de 2 à 4 étudiants, 3 étant la __taille recomandée__ au vu du travail attendu;
    * Les groupes ne respectant pas cette contrainte ne seront pas évalués.
      * Astuce : Utilisez le Slack pour former vos équipes !
    * Le premier étudiant crée l'équipe sur _Classroom_, puis les autres rejoignent cette équipe. 
    * Ce sont les informations présentes dans _Classroom_ qui feront foi pour l'évaluation, donc faites attention.
  * Récupérez le travail sur Github Classroom:
    * TODO []() 
  * Par modèle, on entend dans ce travail les trois types de modèles UML suivants : diagrammes de cas d'utilisation, de classes et de séquence. 
  * Il n'est pas attendu d'interface personne-machine (textuelle ou graphique). Les seules exécutions de votre code seront les tests unitaires et les scénarios d'acceptation.
  * Il n'est pas attendu de base de données, ou quoi que ce soit de ce genre. Si vous pensez ce genre de système nécéssaire, _bouchonnez_ le avec des objets Java.

### Dates importantes[^dates]

  * Date de formation des équipes : 22.01.19, 23h50
  * Date de remise des travaux : 10.02.19, 23h50
    * _Vous aurez les retours sur ce travail avant l'intra du 20 février._ 

**Aucune remise ne sera acceptée après la date de clôture automatique des dépôts**. 


### Évaluation (/100)
 
  * Rapport : 40 points 
    * Diagramme de cas d'utilisation : 		5 points
    * Diagramme de classe : 					10 points
    * Diagramme(s) de séquences : 				10 points
    * Justification des choix de conception : 	15 points
    * Identifications des limites de la conception : 10 points
  * Qualité du code objet : 30 points
    * Respect des principes (i) _responsabilité unique_ et (ii) _ouvert/fermé_ : 15 points
    * Lisibilité du code Java : 5 points
    * Cohérence entre conception et code développé : 10 points
  * Scénarios d'acceptation : 30 points
    * Couverture fonctionnelle des spécifications : 20 points
    * Lisibilité des scénarios et des codes des étapes : 10 points 

Le rapport est rédigé en français. Un rapport de mauvaise qualité (sur la forme, l'orthographe, ou la grammaire, ...) se verra attribué un malus qui pourra aller jusqu'à 10% de la note du travail.

Votre participation sur le Git sera utilisée pour pondérer votre note en fonction de l'effort de développement mis dans le projet, avec un malus pouvant aller jusqu'à 100% de la note de groupe pour les cas extrêmes. Assurez vous de régler votre environnement pour que vos _commits_ soient reliés à votre véritable identité (voir atelier `A1` pour régler ce genre de détails).
 

## Première itération : Produit minimal et viable

On souhaite informatiser la bibliothèque universitaire de l'UQAM, et on fait l’hypothèse qu’il n’y a pas déjà de système existant. 

  * Cette bibliothèque propose aux usagers de l’Université des livres à emprunter. 
  * Chaque document est identifié par un numéro unique. 
  * Un livre est caractérisé par un titre, un nom d’éditeur et un ou plusieurs auteur(s). 
  * Un livre peut être emprunté ou consulté sur place.
  * Les usagers sont identifiés par les informations associées à leur carte UQAM : leur code permanent, un nom, un prénom et une adresse. 
  * Ils peuvent consulter sur place, effectuer des recherches de documents par titre ou nom d'auteur en utilisant le système d'information de la bibliothèque.
  * Chaque livre emprunté par un usager précis est connu du système d’information de la bibliothèque : l’étudiant donne le livre à emprunter à la bibliothécaire à la caisse de sortie, avec sa carte UQAM. 
  * Pour rendre un livre, un étudiant le place simplement sur des étagères spécifiques à la caisse et, régulièrement, les bibliothécaires utilisent le système pour remettre le livre dans le fond documentaire de la bibliothèque.

### Travail à réaliser 

  1. Faire un premier diagramme de cas d’utilisation qui couvre les acteurs et les cas déterminés (ne cherchez pas à faire compliqué pour le moment).
  2. Prendre le cas d’utilisation que vous considérez le plus important et :
    * Définir un diagramme de classes et un diagramme de séquences correspondant et cohérent.
    * Développer le code (métier et tests d'acceptation) qui supportent cette conception.
  3. Procéder cas par cas pour arriver au final à couvrir toutes les fonctionnalité 

## Seconde itération : Complexification métier

Après plusieurs réunions avec des représentants des bibliothèques universitaires, plusieurs besoins additionnels doivent être intégrés :
  
  * La bibliothèque propose aux étudiants et aux enseignants de l’université des livres et des revues. 
  * Un livre est caractérisé par un titre, un nom d’éditeur et un ou plusieurs auteur(s). Les revues sont caractérisées par un titre et la périodicité de leur parution. 
  * S’il existe plusieurs exemplaires d’un livre, chaque exemplaire a une cote qui lui est propre.
  * On ne peut pas emprunter plus de 3 livres en même temps, et la durée maximum d’un prêt est de 15 jours pour un étudiant et de 1 mois pour un enseignant. 
  * Si un livre n’est pas disponible, on peut le réserver. 
  * Quand ils rendent en retard un document, les usagers ont une période de _gel_ qui les empêche d'emprunter de nouveaux documents pendant une durée égale à 2 fois la durée de leur retard.
 
### Travail à réaliser 

  * Faire évoluer vos modèles pourconcevoir ces nouvelles fonctionalités;
  * Implémentez le code objet associé, ainsi que les scénarios d'acceptation démontrant ces fonctionnalités.

## À Rendre

  * Avant la date de clôture, vous poserez sur le _commit_ correspondant à votre rendu le tag `final` (n'oubliez pas de pousser ce tag sur le dépôt, par exemple avec la commande `git push --tags`);
  * A la racine de votre dépôt, vous devez livrer un rapport au format PDF, nommé `Rapport_XX_YY_ZZ_TT.pdf`, où `XX`, `YY`, `ZZ` et `TT` correspondent aux codes permanents des étudiants ayant participé au rendu.
  * Le code rendu doit compiler et les tests d'acceptation s'exécuter avec la commande `mvn clean package` lancée à la racine de votre dépôt. Si vous ne changez pas la structure donnée, c'est déjà la cas.

Votre rapport (format Letter, 10 pages max, police type Times en 11 pts) doit contenir les informations suivantes : 

  * Les modèles _importants_ correspondant à la version finale,
    * en identifiant ce qui a du être modifié entre la première itération et la seconde;
    * en identifiant pourquoi vous considérez que ces modèles sont _importants_ pour l'application conçue;
  * Une justification des choix de conception que vous avez faits pour la version finale;
  * Une identification des limites (points fixes et points de variations) de votre conception : qu'est-ce qu'il sera facile de faire évoluer, au contraire, qu'est-ce qui est figé ?
  * Un court paragraphe de gestion de projet explicitant comment vous avez développé le projet, et qui a fait quoi.


## Pour aller plus loin : Itération Bonus

Pour les équipes intéressées à aller plus loin, vous pouvez considérer les évolutions de spécification suivantes. Attention, ce travail ne sera pris en compte que si le reste du travail rendu à une note > 75. Il pourra donner un bonus de 10 points maximum sur la note totale du travail, la note maximale restant 100.

  * Un adhérent qui ne rend pas le livre qu’il a emprunté à la date prévue est relancé 2 fois, à une semaine d’intervalle.
  * Sur un même livre, il ne peut pas y avoir plus de réservations que de nombre d’exemplaires de ce livre. Les réservations sont évidemment ordonnées.
  * Lors d’une réservation, une date potentielle de disponibilité est donnée : elle est calculée en fonction de :
    * la date d’emprunt de l’exemplaire qui correspond à sa place dans la liste d’attente (si on est 4ème, c’est la date d’emprunt du 4ème exemplaire plus ancien qui est utilisée);
    * couplée à la durée moyenne de prêt de ce livre, calculée sur les deux dernières années.
  * Si le livre n’est toujours pas rendu 1 semaine après la dernière relance, il est considéré comme perdu (jusqu’à ce qu’éventuellement l’adhérent ramène le livre à la bibliothèque) et l’adhérent est interdit de prêt. S’il y a une réservation attenante à ce livre perdu, elle est annulée et un email est envoyé à celui ou celle qui avait fait cette réservation.

### Travail à réaliser 

  * Identifiez dans ces nouvelles spécifications ce qui fait partie de votre système et ce qui n'en fait pas partie;
  * Faire évoluer vos modèles et votre code pour permettre de supporter ces nouvelles fonctionnalités



[^dates]: Les horaires de rendus s'entendent en _Heure Normale de l'Est_.
