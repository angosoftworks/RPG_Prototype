---
description: Volumes définissant les zones valides pour le spawn dynamique.
icon: rectangle-wide
---

# bIsZoneEnabled

#### Description générale

`bIsZoneEnabled` est une variable booléenne utilisée dans le Blueprint **BP\_SpawnZone**. Elle indique si la zone de spawn est actuellement active et disponible pour le spawn d’acteurs. Elle permet un contrôle simple et efficace pour activer ou désactiver une zone sans avoir à modifier la logique du système de spawn.

***

#### Détails techniques

| Propriété                      | Valeur                                                                                             |
| ------------------------------ | -------------------------------------------------------------------------------------------------- |
| **Nom de la variable**         | bIsZoneEnabled                                                                                     |
| **Type**                       | Booléen (True / False)                                                                             |
| **Catégorie**                  | Par défaut                                                                                         |
| **Instance modifiable**        | Oui (modifiable dans l’inspecteur)                                                                 |
| **Blueprint en lecture seule** | Non                                                                                                |
| **Exposer à l’apparition**     | Non                                                                                                |
| **Privé**                      | Non (accessible aux autres Blueprints)                                                             |
| **Réplicable**                 | Non                                                                                                |
| **Condition de réplication**   | Aucune                                                                                             |
| **Valeur par défaut**          | True                                                                                               |
| **Description**                | (Non spécifiée explicitement, à envisager d’ajouter un tooltip pour plus de clarté dans l’éditeur) |

***

#### Comportement

Cette variable joue un rôle fondamental dans le contrôle du comportement des zones :

* **True** : La zone est active, les acteurs peuvent y être spawnés.
* **False** : La zone est désactivée, elle ne sera pas considérée lors des vérifications du système de spawn (notamment via la fonction **IsZoneAvailable**).

Elle permet ainsi une désactivation temporaire ou permanente de certaines zones selon les besoins du gameplay (ex : zone temporairement fermée, bloquée par un événement).

***

#### Utilisation prévue

* **Système de spawn** : Vérifiée dans les conditions de disponibilité (fonction **IsZoneAvailable**) pour permettre ou non le spawn dans la zone.
* **Contrôle par le Level Designer** : Peut être ajustée directement depuis l’inspecteur Unreal en fonction des besoins du niveau.
* **Gameplay dynamique** : Peut être modifiée à runtime via Blueprints pour activer/désactiver une zone selon des événements (ex : après un timer, une interaction, etc.).

***

#### Bonnes pratiques

* **Ajouter une description** : Pour plus de clarté, il est conseillé d’ajouter un **tooltip** dans Unreal du style : "Active ou désactive cette zone pour le spawn".
* **Catégorisation** : Envisager d’ajouter une catégorie personnalisée du type **Spawn | Zone Settings** pour une meilleure organisation.
* **Utilisation avec événements** : Manipuler cette variable via des fonctions ou événements dédiés (par ex. `EnableZone()` / `DisableZone()`) pour garantir un contrôle propre et éviter les modifications directes intempestives.

***

#### Suggestions d’améliorations

| Suggestion                  | Détail                                                                                                            |
| --------------------------- | ----------------------------------------------------------------------------------------------------------------- |
| **Description Unreal**      | Ajouter une description pour expliciter son rôle dans l’inspecteur.                                               |
| **Réplication potentielle** | Envisager la réplication si le projet passe en multijoueur, pour synchroniser l'état d'activation de chaque zone. |
| **Encapsulation**           | Proposer des fonctions Blueprint pour modifier proprement son état (activation/désactivation).                    |
