---
description: Volumes définissant les zones valides pour le spawn dynamique.
icon: rectangle-wide
---

# ActorToSpawn

#### Description générale

`ActorToSpawn` est une variable de type **Classe d'acteur (Actor Class)** utilisée pour spécifier quel type d’acteur doit être généré par le système de spawn. Elle permet de paramétrer dynamiquement le type d’acteur à instancier sans avoir à modifier directement le Blueprint ou le code.

***

#### Détails techniques

| Propriété                      | Valeur                                 |
| ------------------------------ | -------------------------------------- |
| **Nom de la variable**         | ActorToSpawn                           |
| **Type**                       | Classe d’acteur (`Actor Class`)        |
| **Catégorie**                  | Par défaut                             |
| **Instance modifiable**        | Non                                    |
| **Blueprint en lecture seule** | Non                                    |
| **Exposer à l’apparition**     | Non                                    |
| **Privé**                      | Non (accessible aux autres Blueprints) |
| **Réplicable**                 | Non                                    |
| **Condition de réplication**   | Aucune                                 |
| **Valeur par défaut**          | `None`                                 |

***

#### Comportement

* **Paramétrage dynamique** : Permet de choisir dynamiquement la classe d’acteur à instancier au moment du spawn.
* **Non modifiable à l’instanciation** : La valeur doit être définie soit par défaut, soit via Blueprints ou code en amont.
* **Locale** : Aucun comportement de réplication défini, la valeur est locale.

***

#### Utilisation prévue

`ActorToSpawn` est principalement utilisée pour :

* Spécifier quel type d’acteur doit être spawné (ex : PNJ, objet interactif, ennemi spécifique, etc.).
* Permettre une grande flexibilité, en autorisant de changer le type d’acteur à générer sans avoir à modifier la logique du spawn.
* Rendre le système de spawn modulaire, en rendant l’acteur à spawn paramétrable par d’autres Blueprints ou systèmes.

***

#### Bonnes pratiques

* **Validation** : Vérifier que la référence à la classe d’acteur n’est pas `None` avant toute tentative de spawn.
* **Centralisation** : Gérer l’affectation de cette variable depuis un point centralisé (par exemple un spawn manager ou configurateur global).
* **Description** : Ajouter une description explicite dans Unreal pour faciliter la compréhension lors du survol dans l'éditeur.
* **Contrôle de type** : S’assurer que seules des classes compatibles sont affectées (héritées de `Actor`).

***

#### Suggestions d’améliorations

| Suggestion                     | Détail                                                                                           |
| ------------------------------ | ------------------------------------------------------------------------------------------------ |
| **Catégorisation**             | Créer une catégorie personnalisée (ex. : \`Gameplay                                              |
| **Description**                | Ajouter une description dans Unreal pour clarifier son usage lors du survol dans l'éditeur.      |
| **Blueprint en lecture seule** | Activer si cette variable est uniquement définie au début et ne doit pas être modifiée ensuite.  |
| **Réplicabilité future**       | Envisager la réplication si la classe d’acteur doit être identique entre clients en multijoueur. |

***

#### Exemple visuel _(facultatif pour enrichir la doc GitBook)_ :

* Capture d’écran montrant un **Spawn Actor from Class** utilisant `ActorToSpawn` comme classe de référence.
* Illustration d’une logique conditionnelle changeant dynamiquement le type d’acteur assigné à `ActorToSpawn`.

***

#### Remarque

`ActorToSpawn` fonctionne en parfaite synergie avec les variables comme **SpawnZones**, **SpawnInterval** et **MaxSpawnedActors** pour offrir un système de spawn entièrement paramétrable et modulaire.
