---
description: Liste des PNJs actuellement spawnés et gérés par le système.
icon: rectangle-wide
---

# MaxSpawnedActors

#### Description générale

`MaxSpawnedActors` est une variable de type **entier (int)** qui définit le nombre maximal d’acteurs pouvant être générés simultanément par le système de spawn. Elle agit comme une limite de contrôle pour éviter une surcharge du gameplay ou du système.

***

#### Détails techniques

| Propriété                      | Valeur                                 |
| ------------------------------ | -------------------------------------- |
| **Nom de la variable**         | MaxSpawnedActors                       |
| **Type**                       | Integer (`int`)                        |
| **Catégorie**                  | Par défaut                             |
| **Instance modifiable**        | Non                                    |
| **Blueprint en lecture seule** | Non                                    |
| **Exposer à l’apparition**     | Non                                    |
| **Privé**                      | Non (accessible aux autres Blueprints) |
| **Réplicable**                 | Non                                    |
| **Condition de réplication**   | Aucune                                 |
| **Valeur par défaut**          | `0`                                    |

***

#### Comportement

* **Contrôle** : La variable fixe une limite supérieure au nombre d’acteurs qui peuvent être présents simultanément, ce qui permet de maîtriser la charge système et la complexité en jeu.
* **Non modifiable à l’instanciation** : Elle n’est pas exposée à l’apparition, donc elle doit être définie par défaut ou modifiée via scripts/Blueprints pendant l’exécution.
* **Locale** : Aucun comportement de réplication, donc la valeur est locale et non synchronisée en multijoueur.

***

#### Utilisation prévue

`MaxSpawnedActors` est utilisée pour :

* Limiter le nombre d’acteurs spawnés afin de préserver les performances.
* Servir de condition dans les systèmes de spawn (ex : empêcher de nouvelles apparitions si la limite est atteinte).
* Potentiellement offrir un paramètre ajustable en fonction du niveau ou du contexte (facilité/difficulté, environnement, etc.).

***

#### Bonnes pratiques

* **Validation** : Toujours vérifier que la valeur est supérieure à zéro avant de l’utiliser dans une logique de spawn.
* **Équilibrage** : Ajuster cette valeur en fonction des capacités matérielles visées et du gameplay souhaité.
* **Centralisation** : Modifier ou exposer cette variable uniquement dans un système de gestion central (ex : Manager de spawn) pour éviter des conflits ou incohérences.
* **Commentaires** : Ajouter une description claire dans l’éditeur pour rappeler son rôle.

***

#### Suggestions d’améliorations

| Suggestion                     | Détail                                                                                                         |
| ------------------------------ | -------------------------------------------------------------------------------------------------------------- |
| **Catégorisation**             | Créer une catégorie personnalisée (ex. : \`Gameplay                                                            |
| **Description**                | Ajouter une description dans Unreal pour expliciter la fonction de la variable.                                |
| **Blueprint en lecture seule** | Activer cette option si la variable doit uniquement être lue pendant le gameplay, sans modification dynamique. |
