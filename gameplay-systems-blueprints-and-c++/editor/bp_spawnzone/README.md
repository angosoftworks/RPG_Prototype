# BP\_SpawnZone

#### Description générale

Le **BP\_SpawnZone** est un Blueprint de type **Actor** qui sert à définir une zone dans laquelle des acteurs peuvent être générés (spawned) de manière contrôlée. Ce Blueprint intègre des paramètres configurables pour la gestion du spawn, des contrôles sur la disponibilité de la zone, et des interfaces pour communiquer avec d'autres éléments du gameplay.

***

#### Paramètres généraux

| Propriété                        | Valeur par défaut / Paramètres spécifiques |
| -------------------------------- | ------------------------------------------ |
| **Classe parent**                | `Acteur`                                   |
| **Déprécier**                    | Non coché                                  |
| **Generate Const Class**         | Non coché                                  |
| **Generate Abstract Class**      | Non coché                                  |
| **Should Cook Property Guides?** | Inherit                                    |

***

#### Options du Blueprint

| Option                                   | Valeur               |
| ---------------------------------------- | -------------------- |
| **Run Construction Script on Drag**      | ✅ Activé             |
| **Run Construction Script in Sequencer** | Non coché            |
| **Blueprint Display Name**               | (vide)               |
| **Blueprint Description**                | (vide)               |
| **Blueprint Namespace**                  | (vide)               |
| **Blueprint Category**                   | (vide)               |
| **Hide Categories**                      | Aucun élément masqué |

***

#### Importations & Espaces de noms

| Section                        | Valeur |
| ------------------------------ | ------ |
| **Espaces de noms par défaut** | Aucun  |
| **Espaces de noms importés**   | Aucun  |

***

#### Interfaces

| Type                        | Valeur                                                                 |
| --------------------------- | ---------------------------------------------------------------------- |
| **Interfaces héritées**     | Aucune interface héritée                                               |
| **Interfaces implémentées** | `BPI_SpawnZone` (Interface spécifique liée à la gestion du spawn zone) |

***

#### Points clés

* **Construction Script actif au Drag & Drop** : Ce qui permet d’avoir un comportement ou une visualisation immédiate dans l'éditeur lors du placement du BP\_SpawnZone dans la scène.
* **Pas d’abstraction ou const class** : Le BP peut être directement instancié, ce n’est pas une classe "template" destinée à être dérivée uniquement.
* **Pas de catégorie spécifique ni d’espaces de noms/importations personnalisées.**
* **Implémentation d’une interface BPI\_SpawnZone** : Cela suggère que le Blueprint peut communiquer avec d'autres Blueprints ou systèmes utilisant cette interface, pour des interactions comme validation ou gestion du spawn.

***

#### Utilisation typique

* Définir des **zones de spawn paramétrables** sur la map.
* Vérification de la disponibilité de la zone via les méthodes exposées dans l'interface **BPI\_SpawnZone**.
* Contrôle dynamique du spawn d’acteurs (ex : limite max d’acteurs, cooldown, etc.).
* Possibilité d’utiliser le **Construction Script** pour prévisualiser ou modifier la zone directement dans l’éditeur.

***

#### Conseils

| Action                                                                                     | Pourquoi ?                                                                    |
| ------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------- |
| Remplir le **Blueprint Display Name** et **Description**                                   | Pour faciliter la lecture et la compréhension rapide dans le Content Browser. |
| Si plusieurs spawn zones différentes, utiliser un **Blueprint Namespace** ou **Category**  | Aide à organiser les Blueprints et facilite leur recherche.                   |
| Ajouter un commentaire global dans la description pour expliquer le rôle et particularité. | Améliore la maintenabilité et la passation de projet.                         |

***

💡 **Astuce :**\
Grâce à l'interface **BPI\_SpawnZone**, ce Blueprint peut facilement être interrogé ou contrôlé par un **SpawnManager** ou d'autres systèmes sans couplage direct. Très pratique pour une architecture scalable.
