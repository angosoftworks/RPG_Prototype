---
description: Liste des points de spawn utilisables par ce système.
icon: table-cells
---

# SpawnedActorsInZone

#### Description générale

`SpawnedActorsInZone` est une variable de type **Array d’Actors** utilisée dans le Blueprint **BP\_SpawnZone**. Elle contient la liste des acteurs qui ont déjà été spawnés dans la zone correspondante. Ce tableau est essentiel pour suivre et contrôler le nombre d’acteurs actifs dans chaque zone.

***

#### Détails techniques

| Propriété                      | Valeur                                                                             |
| ------------------------------ | ---------------------------------------------------------------------------------- |
| **Nom de la variable**         | SpawnedActorsInZone                                                                |
| **Type**                       | Array of Actor (objet dérivé de **AActor**)                                        |
| **Catégorie**                  | Par défaut                                                                         |
| **Instance modifiable**        | Non                                                                                |
| **Blueprint en lecture seule** | Non                                                                                |
| **Exposer à l’apparition**     | Non                                                                                |
| **Privé**                      | Non (accessible aux autres Blueprints)                                             |
| **Réplicable**                 | Non                                                                                |
| **Condition de réplication**   | Aucune                                                                             |
| **Valeur par défaut**          | Vide (0 élément)                                                                   |
| **Description**                | "Liste des acteurs déjà spawn dans cette zone" (affichée dans l’inspecteur Unreal) |

***

#### Comportement

Cette variable joue un rôle crucial dans la gestion dynamique des acteurs présents dans la zone :

1. **Ajout d’acteurs** : Chaque fois qu’un acteur est spawné dans la zone, une référence à cet acteur est ajoutée à ce tableau.
2. **Vérification de la capacité** : Utilisée dans la fonction **IsZoneAvailable** pour comparer le nombre d’acteurs spawnés avec la valeur de **MaxActorsInZone**.
3. **Nettoyage éventuel** : Lorsque des acteurs sont détruits ou quittent la zone, ils peuvent être retirés du tableau si nécessaire (suivant la logique de ton projet).

***

#### Utilisation prévue

* **Système de spawn** : Sert de mémoire pour savoir combien d’acteurs sont actifs dans la zone à un moment donné.
* **Contrôle de surcharge** : Permet d’empêcher le spawn d’acteurs supplémentaires si la zone est pleine.
* **Gestion dynamique** : Peut être parcourue pour effectuer des actions globales (désactivation, destruction, repositionnement des acteurs présents).

***

#### Bonnes pratiques

* **Nettoyage** : Penser à retirer proprement les références d’acteurs détruits pour éviter les références nulles.
* **Vérification de validité** : Lors de parcours ou d’opérations sur ce tableau, toujours vérifier si chaque acteur est toujours valide (non détruit).
* **Catégorisation** : Envisager de déplacer cette variable sous une catégorie personnalisée du type **Spawn | Zone** pour plus de clarté.

***

#### Suggestions d’améliorations

| Suggestion                         | Détail                                                                                                                     |
| ---------------------------------- | -------------------------------------------------------------------------------------------------------------------------- |
| **Optionnel : Réplication future** | Si le projet évolue vers du multijoueur, envisager de rendre cette variable réplicable pour synchroniser l’état des zones. |
| **Description enrichie**           | Ajouter plus de détails dans le tooltip, notamment le comportement attendu lors du nettoyage ou destruction d’acteurs.     |
| **Encapsulation**                  | Implémenter des fonctions dédiées (AddActor, RemoveActor) pour manipuler ce tableau proprement et éviter les erreurs.      |
