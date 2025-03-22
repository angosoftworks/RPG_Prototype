---
icon: arrow-right-to-bracket
---

# Event ActorBeginOverlap

#### Description générale

`ReceiveActorBeginOverlap` est un événement standard hérité de la classe **Actor**. Il est déclenché automatiquement lorsque l’acteur commence à **chevaucher un autre acteur** (overlap), c’est-à-dire lorsqu'il entre en collision avec un autre acteur configuré pour générer des événements d’overlap.

Dans le Blueprint **BP\_SpawnManager**, cet événement est présent mais actuellement désactivé. Il est prêt à être activé si un comportement spécifique lors de collisions ou de contacts est requis.

***

#### Détails techniques

| Propriété                  | Valeur                                                                                                      |
| -------------------------- | ----------------------------------------------------------------------------------------------------------- |
| **Nom de l’événement**     | ReceiveActorBeginOverlap                                                                                    |
| **Défini dans**            | `/Game/Blueprints/BP_SpawnManager`                                                                          |
| **Type d’événement**       | ActorBeginOverlap                                                                                           |
| **Appelé automatiquement** | Oui, lors d’un chevauchement (overlap)                                                                      |
| **Statut actuel**          | Désactivé                                                                                                   |
| **Pin spécifique**         | `OtherActor` – référence à l’acteur qui entre en collision                                                  |
| **Commentaire visible**    | Oui, précisant que le nœud est désactivé                                                                    |
| **Commentaire**            | "Ce nœud est désactivé et ne sera pas appelé. Faites glisser les broches pour générer des fonctionnalités." |

***

#### Comportement

* **Déclenchement automatique** : Lorsqu’un autre acteur entre dans la zone de collision de cet acteur (et que la détection d'overlap est activée).
* **Utilisation classique** : Détection d'interactions (ex : ramassage d’objets, déclenchement de pièges, zones de spawn conditionnelles).
* **Actuellement désactivé** : Le nœud est présent mais ne sera pas appelé tant qu’il n’est pas activé.

***

#### Utilisation prévue

Dans le contexte du **BP\_SpawnManager**, l’événement **ReceiveActorBeginOverlap** pourrait être utilisé pour :

* Déclencher des spawns lorsqu’un joueur ou PNJ entre dans une zone spécifique.
* Désactiver ou activer certaines zones de spawn dynamiquement.
* Interagir avec des acteurs spécifiques (par ex. : valider si le **OtherActor** est un joueur, un ennemi, ou un objet particulier).
* Coupler avec des volumes de trigger pour gérer des événements liés aux spawns.

***

#### Bonnes pratiques

* **Filtrage des acteurs** : Utiliser le pin **OtherActor** pour vérifier précisément avec quel type d’acteur l’overlap est déclenché (par exemple, via `Cast To` ou `Actor Tags`).
* **Validation** : Toujours vérifier que **OtherActor** est valide avant d’effectuer des actions.
* **Optimisation** : Si l’événement est inutilisé, laisser désactivé pour éviter des appels inutiles en runtime.
* **Organisation visuelle** : Ajouter des commentaires expliquant l’usage si activé (ex : "Détection d’entrée dans la zone de spawn").

***

#### Suggestions d’améliorations

| Suggestion                   | Détail                                                                                                       |
| ---------------------------- | ------------------------------------------------------------------------------------------------------------ |
| **Activer si nécessaire**    | Si le système de spawn doit réagir à des overlaps, activer cet événement et ajouter la logique appropriée.   |
| **Commentaires clairs**      | Documenter clairement la logique ajoutée, surtout si plusieurs types d’acteurs interagissent.                |
| **Détection conditionnelle** | Filtrer les acteurs en fonction du gameplay (joueurs, PNJs, objets) pour éviter des déclenchements inutiles. |

***

#### Exemple visuel _(pour ton GitBook si besoin)_ :

* Capture d’écran du **ReceiveActorBeginOverlap** activé, filtrant les overlaps uniquement pour des acteurs spécifiques.
* Illustration d'une interaction typique : spawn déclenché lors de l’entrée du joueur dans une zone.

***

#### Remarque

Cet événement est une excellente base pour rendre le système de spawn réactif à l’environnement ou aux actions du joueur. Même désactivé, il est déjà en place pour être facilement utilisé si nécessaire.
