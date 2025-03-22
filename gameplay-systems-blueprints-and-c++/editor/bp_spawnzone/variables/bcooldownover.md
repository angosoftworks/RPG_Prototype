---
description: Volumes définissant les zones valides pour le spawn dynamique.
icon: rectangle-wide
---

# bCooldownOver

#### Description générale

`bCooldownOver` est une variable booléenne présente dans le Blueprint **BP\_SpawnZone**. Elle indique si le délai de rechargement (cooldown) de la zone est terminé. Tant que cette variable est à **False**, la zone n'est pas disponible pour le spawn, même si d'autres conditions sont réunies. Cela permet d’introduire des pauses contrôlées entre les spawns pour un gameplay plus équilibré.

***

#### Détails techniques

| Propriété                      | Valeur                                                                  |
| ------------------------------ | ----------------------------------------------------------------------- |
| **Nom de la variable**         | bCooldownOver                                                           |
| **Type**                       | Booléen (True / False)                                                  |
| **Catégorie**                  | Par défaut                                                              |
| **Instance modifiable**        | Oui (modifiable dans l’inspecteur)                                      |
| **Blueprint en lecture seule** | Non                                                                     |
| **Exposer à l’apparition**     | Non                                                                     |
| **Privé**                      | Non (accessible aux autres Blueprints)                                  |
| **Réplicable**                 | Non                                                                     |
| **Condition de réplication**   | Aucune                                                                  |
| **Valeur par défaut**          | True                                                                    |
| **Description**                | Aucune description définie explicitement (à envisager d’en ajouter une) |

***

#### Comportement

Cette variable est un **flag** déterminant dans la logique de spawn :

* **True** : Le cooldown est terminé, la zone peut potentiellement être utilisée pour le spawn (en combinaison avec d'autres conditions comme le nombre maximum d'acteurs et l'état d'activation).
* **False** : La zone est temporairement indisponible à cause d’un cooldown en cours. Elle ne participera pas au processus de spawn tant qu’elle n’est pas remise à **True**.

Elle est typiquement modifiée à runtime, souvent après le spawn d’un acteur, pour introduire un délai configurable avant qu’un autre spawn puisse se produire dans la même zone.

***

#### Utilisation prévue

* **Contrôle du rythme de spawn** : Empêche le spam d’acteurs dans une zone.
* **Système de cooldown personnalisé** : Peut être utilisée avec des timers ou des events pour gérer le reset du cooldown.
* **Vérification logique** : Est vérifiée dans la fonction **IsZoneAvailable**, combinée avec d'autres paramètres comme **bIsZoneEnabled**.

***

#### Bonnes pratiques

* **Ajout d’une description Unreal** : Un tooltip du type "Indique si le cooldown de la zone est terminé" améliorerait la lisibilité dans l’éditeur.
* **Encapsulation** : Utiliser des fonctions Blueprint dédiées du style `StartCooldown()` / `ResetCooldown()` pour modifier proprement cette variable.
* **Affichage visuel (optionnel)** : Envisager d’ajouter un feedback visuel ou un widget lorsque le cooldown est actif, si pertinent pour le gameplay.

***

#### Suggestions d’améliorations

| Suggestion                       | Détail                                                                                                                        |
| -------------------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| **Description Unreal**           | Ajouter un tooltip explicatif dans Unreal.                                                                                    |
| **Catégorisation personnalisée** | Classer la variable sous une catégorie dédiée comme \*\*Spawn                                                                 |
| **Réplication (optionnel)**      | Si le projet passe en multijoueur, considérer la réplication pour synchroniser l’état du cooldown.                            |
| **Timer Blueprint dédié**        | Créer une logique de cooldown automatisée (par exemple avec `Set Timer by Function Name`) pour contrôler la réinitialisation. |
