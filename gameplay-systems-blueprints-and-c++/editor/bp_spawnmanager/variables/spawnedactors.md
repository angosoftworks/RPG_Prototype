---
description: Liste des points de spawn utilisables par ce système.
icon: table-cells
---

# SpawnedActors

#### Description générale

`SpawnedActors` est une variable de type **Array d'objets**, contenant des références aux instances d’acteurs (`Actor`) qui ont été générés par le système de spawn. Elle permet de conserver la liste des acteurs actuellement présents en jeu suite à une action de spawn, facilitant ainsi leur gestion (destruction, contrôle, comptage, etc.).

***

#### Détails techniques

| Propriété                      | Valeur                                 |
| ------------------------------ | -------------------------------------- |
| **Nom de la variable**         | SpawnedActors                          |
| **Type**                       | Array d'objets : `Actor`               |
| **Catégorie**                  | Par défaut                             |
| **Instance modifiable**        | Non                                    |
| **Blueprint en lecture seule** | Non                                    |
| **Exposer à l’apparition**     | Non                                    |
| **Privé**                      | Non (accessible aux autres Blueprints) |
| **Réplicable**                 | Non                                    |
| **Condition de réplication**   | Aucune                                 |
| **Valeur par défaut**          | Initialisée vide (0 élément)           |

***

#### Comportement

* **Gestion dynamique** : Cette variable contient à tout moment les références des acteurs générés par le système.
* **Non modifiable à l’instanciation** : Elle est remplie uniquement en runtime lors des actions de spawn.
* **Locale** : Aucun comportement de réplication n’est défini — elle reste locale et n’est pas synchronisée en multijoueur.

***

#### Utilisation prévue

`SpawnedActors` est utilisée pour :

* Garder une trace des acteurs créés dynamiquement.
* Faciliter la gestion des acteurs spawnés : destruction groupée, vérification de leur état, comptage pour contrôler la densité du gameplay.
* Implémenter des systèmes de "clean-up" (nettoyage) pour supprimer proprement les acteurs inutiles.

***

#### Bonnes pratiques

* **Validation** : Toujours vérifier que les références contenues dans le tableau sont valides avant toute opération (ex : éviter d’essayer de détruire un acteur déjà supprimé).
* **Mise à jour** : Penser à retirer les références d’acteurs détruits ou invalides du tableau pour éviter les accès inutiles.
* **Performance** : En cas de grand nombre d’acteurs, préférer des itérations efficaces (par ex. : boucle optimisée ou suppression en lot).
* **Centralisation** : Toutes les modifications de cette variable doivent idéalement passer par un manager central pour une cohérence maximale.

***

#### Suggestions d’améliorations

| Suggestion                     | Détail                                                                                         |
| ------------------------------ | ---------------------------------------------------------------------------------------------- |
| **Catégorisation**             | Créer une catégorie personnalisée (ex. : \`Gameplay                                            |
| **Description**                | Ajouter une description dans Unreal pour expliciter clairement son rôle dans l'éditeur.        |
| **Blueprint en lecture seule** | Activer si la variable ne doit être lue que pour des vérifications, sans modification externe. |
| **Réplicabilité future**       | Envisager la réplication si les acteurs doivent être visibles et synchronisés en multijoueur.  |

***

#### Remarque

Il est recommandé d’utiliser **SpawnedActors** conjointement avec **MaxSpawnedActors** pour toujours garder le contrôle sur la densité et le comportement des entités présentes.
