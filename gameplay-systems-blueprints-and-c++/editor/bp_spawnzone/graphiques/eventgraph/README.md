---
icon: diagram-project
---

# EventGraph

#### Description générale

Le **Event Graph** du `BP_SpawnZone` contient les événements par défaut hérités de la classe `Actor` dans Unreal Engine, mais ceux-ci sont désactivés. Cela signifie que les événements ne seront pas appelés par le moteur lors de l'exécution. Il est cependant possible de les réactiver pour ajouter des comportements spécifiques liés au cycle de vie de l'acteur ou aux interactions physiques.

***

#### Événements présents

| Événement                    | État      | Détails                                                                                                                                                                                                                 |
| ---------------------------- | --------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **ReceiveBeginPlay**         | Désactivé | Déclenché au début du jeu ou lorsque l'acteur est spawn. Ici, le commentaire précise qu'il est désactivé : _"Ce nœud est désactivé et ne sera pas appelé."_                                                             |
| **ReceiveActorBeginOverlap** | Désactivé | Déclenché lorsqu'un autre acteur entre en overlap avec le `BP_SpawnZone`. Également désactivé, mais prêt à être utilisé si nécessaire. Un pin "OtherActor" permet de récupérer l'acteur entrant en collision.           |
| **ReceiveTick**              | Désactivé | Exécuté chaque frame. Peut être activé si une logique temps réel est nécessaire, comme un compte à rebours ou un suivi dynamique d'autres acteurs. Le pin "DeltaSeconds" permet de récupérer le temps écoulé par frame. |

***

#### Pourquoi sont-ils désactivés ?

Ces événements sont souvent présents par défaut dans les Blueprints dérivés d'`Actor`. Ici, ils sont désactivés pour :

* Éviter des appels inutiles au runtime (performance).
* Laisser la place à une implémentation future si nécessaire.
* Garder la structure du Blueprint propre tout en anticipant des besoins possibles.

***

#### Suggestions d’utilisation

| Événement                    | Utilisation possible                                                                                         |
| ---------------------------- | ------------------------------------------------------------------------------------------------------------ |
| **ReceiveBeginPlay**         | Initialisation dynamique d'acteurs, début d'un système de spawn, ou réglages spécifiques au moment du spawn. |
| **ReceiveActorBeginOverlap** | Détection d'acteurs entrants pour déclencher un spawn, lancer une animation, ou appliquer des effets.        |
| **ReceiveTick**              | Système de cooldown, animation de zone, surveillance constante d'une condition de spawn.                     |

***

#### Bonnes pratiques

* **Désactivation justifiée** : Tant que le comportement n’est pas nécessaire, il est préférable de laisser ces événements désactivés pour limiter les appels de fonction.
* **Ajout de commentaires** : Comme déjà fait, le commentaire sur chaque événement informe que le nœud est désactivé. C'est très clair pour toute personne consultant le Blueprint.
* **Activer seulement en cas de besoin** : Si vous commencez à implémenter une logique, réactivez uniquement l’événement nécessaire, et désactivez ceux inutilisés pour éviter du code dormant.
