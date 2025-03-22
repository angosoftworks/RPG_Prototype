---
icon: diagram-project
---

# EventGraph

#### Description générale

L’**Event Graph** du Blueprint **BP\_SpawnManager** contient les événements principaux liés au cycle de vie de l’acteur. Dans ce Blueprint, plusieurs événements standards sont présents mais actuellement désactivés. Ces événements peuvent être activés pour ajouter des comportements spécifiques au moment du début du jeu, des collisions ou à chaque tick.

***

#### Événements présents

| Événement                    | Statut    | Description                                                                 |
| ---------------------------- | --------- | --------------------------------------------------------------------------- |
| **ReceiveBeginPlay**         | Désactivé | Appelé automatiquement au début du jeu ou lorsque l’acteur est spawné.      |
| **ReceiveActorBeginOverlap** | Désactivé | Appelé lorsque l’acteur commence à chevaucher un autre acteur.              |
| **ReceiveTick**              | Désactivé | Appelé à chaque frame (tick) avec le temps écoulé depuis la dernière frame. |

***

#### Détails techniques

| Propriété                          | Valeur                                                                                         |
| ---------------------------------- | ---------------------------------------------------------------------------------------------- |
| **Nom du Blueprint**               | BP\_SpawnManager                                                                               |
| **Événements définis**             | ReceiveBeginPlay, ReceiveActorBeginOverlap, ReceiveTick                                        |
| **Statut des événements**          | Tous désactivés                                                                                |
| **Commentaires visibles**          | Oui, indiquant que les nœuds sont désactivés                                                   |
| **Remarques sur chaque événement** | Chaque événement contient un commentaire informant qu'il est désactivé et prêt à être utilisé. |

***

#### Comportement

* **ReceiveBeginPlay** : Ce nœud est conçu pour initialiser des comportements au début du jeu. Actuellement désactivé.
* **ReceiveActorBeginOverlap** : Sert à réagir lorsqu'un autre acteur entre en collision ou chevauche cet acteur. Actuellement désactivé.
* **ReceiveTick** : Peut être utilisé pour des mises à jour continues en runtime (par frame). Actuellement désactivé.

Aucun de ces événements n’est actif dans le Blueprint pour le moment. Cependant, ils sont déjà en place, prêts à être utilisés si besoin, ce qui simplifie l'ajout ultérieur de logique sans avoir à les recréer.

***

#### Bonnes pratiques

* **Clarté visuelle** : Garder les événements non utilisés visibles mais désactivés permet aux autres développeurs de comprendre les possibilités d’extension du Blueprint.
* **Commentaires** : Le commentaire ajouté sur chaque nœud précise qu’il est désactivé et qu’il peut être utilisé si nécessaire.
* **Performance** : Désactiver les événements inutilisés évite des appels superflus pendant le runtime.
* **Réactivation contrôlée** : Activer uniquement les événements nécessaires selon les besoins du gameplay (éviter d’utiliser Tick sans raison valable).

***

#### Suggestions d’améliorations

| Suggestion                                | Détail                                                                                                             |
| ----------------------------------------- | ------------------------------------------------------------------------------------------------------------------ |
| **Organisation du graph**                 | Grouper visuellement les événements désactivés avec des commentaires pour montrer qu’ils sont optionnels.          |
| **Suppression des événements inutilisés** | Si certains événements ne seront jamais utilisés, envisager de les supprimer pour alléger le graph.                |
| **Réactivation conditionnelle**           | Réactiver les événements si besoin (par exemple : pour initialiser le pool d’acteurs dans BeginPlay).              |
| **Centralisation**                        | Pour la lisibilité, regrouper les événements d'initialisation, collision et tick séparément avec des commentaires. |

***

#### Exemple visuel _(facultatif pour GitBook)_

* Capture d’écran du **Event Graph** montrant les trois événements désactivés avec leur commentaire.
* Exemple d’un **ReceiveBeginPlay** activé et utilisé pour initialiser les variables (comme le remplissage du pool d’acteurs).

***

#### Remarque

Même désactivés, ces événements sont une base pratique pour ajouter rapidement de la logique supplémentaire dans le **BP\_SpawnManager**, tout en gardant une structure claire et extensible.
