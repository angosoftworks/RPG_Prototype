# BP\_SpawnManager

### Description générale

**BP\_SpawnManager** est un Blueprint de type **Acteur (Actor)** servant de système centralisé pour la gestion du spawn d’acteurs dans le jeu. Il intègre différentes variables, systèmes de pooling, zones de spawn et paramètres permettant de contrôler dynamiquement le comportement des entités spawnées.

Ce Blueprint est conçu pour être flexible, performant et facilement configurable, tout en restant optimisé pour l’édition et le runtime.

***

### Détails techniques

| Propriété                                | Valeur                     |
| ---------------------------------------- | -------------------------- |
| **Classe parent**                        | Actor                      |
| **Déprécié**                             | Non                        |
| **Const Class**                          | Non                        |
| **Abstract Class**                       | Non                        |
| **Should Cook Property GUIDs**           | Inherit (hérite du parent) |
| **Run Construction Script on Drag**      | Oui (activé)               |
| **Run Construction Script in Sequencer** | Non                        |
| **Blueprint Display Name**               | _(non défini)_             |
| **Blueprint Description**                | _(non défini)_             |
| **Blueprint Namespace**                  | _(non défini)_             |
| **Blueprint Category**                   | _(non défini)_             |
| **Hide Categories**                      | Aucun                      |
| **Interfaces héritées**                  | Aucune                     |
| **Interfaces implémentées**              | Aucune                     |
| **Espaces de noms importés**             | Aucun                      |

***

### Comportement général

* **Classe Parent : Actor**\
  Ce choix permet à **BP\_SpawnManager** d’être placé librement dans le niveau et d’interagir avec le monde (collisions, Tick, overlap...).
* **Construction Script actif lors du Drag**\
  Le flag **Run Construction Script on Drag** est activé, ce qui signifie que le **UserConstructionScript** sera exécuté à chaque déplacement dans l’éditeur. Très utile pour visualiser dynamiquement les zones de spawn ou autres éléments configurés dans le Blueprint.
* **Pas d’interfaces**\
  Aucune interface implémentée ou héritée, ce qui indique que le Blueprint n'est pas dépendant de systèmes d'interfaçage spécifiques. Simple à intégrer et autonome.

***

### Utilisation prévue

**BP\_SpawnManager** est destiné à :

* Centraliser la logique de gestion du spawn (zones, pooling, limites, types d’acteurs...).
* Contrôler dynamiquement la fréquence et les conditions de spawn.
* Optimiser les performances grâce à l’utilisation facultative du pooling.
* Être facilement extensible en activant ou configurant les événements standards Unreal (BeginPlay, Tick, Overlap...).

***

### Bonnes pratiques

* **Compléter les champs d’identification** : Pour une meilleure lisibilité dans l’éditeur, il est conseillé de remplir :
  * **Blueprint Display Name**
  * **Blueprint Description**
  * **Blueprint Category**
* **Utilisation du Construction Script** : Puisque le script est déclenché lors du drag, il est idéal pour mettre en place des visualisations des zones ou autres repères visuels dans l’éditeur.
* **Organisation** : Regrouper les variables dans des catégories personnalisées (ex : `Gameplay | Spawn`) pour une meilleure clarté dans l’inspecteur.

***

### Suggestions d’améliorations

| Suggestion                                      | Détail                                                                                                                                |
| ----------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------- |
| **Ajouter une description**                     | Préciser le rôle du Blueprint pour les autres développeurs (ex : “Système central de spawn avec pooling”).                            |
| **Catégorisation des variables**                | Organiser proprement les variables et composants en catégories spécifiques dans l’inspecteur.                                         |
| **Implémentation d'interfaces**                 | Si besoin d’une communication avec d'autres systèmes, envisager l’ajout d’interfaces (ex : I\_Spawnable).                             |
| **Événements clés désactivés prêts à l’emploi** | Le Blueprint contient des événements standards désactivés (BeginPlay, Tick, Overlap) qui peuvent être activés et utilisés facilement. |

***

### Résumé

**BP\_SpawnManager** est un Blueprint modulable et performant, conçu pour centraliser la logique de spawn dans ton projet. Sa structure actuelle est prête à accueillir divers comportements avancés (pooling, contrôle du nombre d’acteurs, gestion dynamique via l'éditeur) tout en laissant la place à des améliorations et personnalisations futures.
