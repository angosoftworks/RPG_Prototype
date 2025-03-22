---
icon: arrow-right-to-bracket
---

# Event Tick

#### Description générale

`ReceiveTick` est un événement standard hérité de la classe **Actor**, déclenché automatiquement **à chaque frame** pendant le runtime. Il est utilisé pour exécuter des actions nécessitant une mise à jour en continu, telles que le suivi d’un état, des timers personnalisés ou des comportements dynamiques.

Dans ton Blueprint **BP\_SpawnManager**, l’événement **ReceiveTick** est actuellement présent mais désactivé. Il est prêt à être activé si une logique nécessitant une mise à jour continue doit être ajoutée.

***

#### Détails techniques

| Propriété                  | Valeur                                                                                                      |
| -------------------------- | ----------------------------------------------------------------------------------------------------------- |
| **Nom de l’événement**     | ReceiveTick                                                                                                 |
| **Défini dans**            | `/Game/Blueprints/BP_SpawnManager`                                                                          |
| **Type d’événement**       | Tick                                                                                                        |
| **Appelé automatiquement** | Oui, à chaque frame (FPS dépendant)                                                                         |
| **Paramètre spécifique**   | `DeltaSeconds` (temps écoulé depuis la dernière frame)                                                      |
| **Statut actuel**          | Désactivé                                                                                                   |
| **Commentaire visible**    | Oui, précisant que le nœud est désactivé                                                                    |
| **Commentaire**            | "Ce nœud est désactivé et ne sera pas appelé. Faites glisser les broches pour générer des fonctionnalités." |

***

#### Comportement

* **Déclenchement en continu** : Exécuté chaque frame durant l’exécution du jeu.
* **Utilisation classique** : Suivi du temps, mise à jour de positions, comportements dynamiques dépendants du temps, contrôle de cooldowns.
* **Actuellement désactivé** : Le nœud est visible mais ne sera pas appelé tant qu’il reste désactivé.

***

#### Utilisation prévue

Dans le cadre du **BP\_SpawnManager**, l’événement **ReceiveTick** pourrait être utilisé pour :

* Vérifier et ajuster dynamiquement les conditions de spawn (ex : vérifier en temps réel si le nombre d’acteurs spawnés atteint une limite).
* Gérer un timer personnalisé pour déclencher des spawns à intervalles variables sans utiliser le système Timer.
* Surveiller des conditions de gameplay évolutives (par ex. : présence d’un joueur dans une zone de spawn).

***

#### Bonnes pratiques

* **Optimisation critique** : Le Tick étant appelé à chaque frame, limiter les opérations lourdes à l’intérieur.
* **Utiliser DeltaSeconds** : Toujours multiplier les valeurs dépendantes du temps par `DeltaSeconds` pour garantir une mise à jour fluide, indépendamment du framerate.
* **Conditionner les appels** : Si certaines actions ne doivent pas être exécutées en permanence, encapsuler la logique dans des branches conditionnelles.
* **Désactiver si inutile** : Garder le Tick désactivé par défaut pour préserver les performances.

***

#### Suggestions d’améliorations

| Suggestion                    | Détail                                                                                           |
| ----------------------------- | ------------------------------------------------------------------------------------------------ |
| **Activation conditionnelle** | Activer uniquement si nécessaire pour des mises à jour temps réel.                               |
| **Commentaires explicites**   | Documenter clairement chaque bloc logique à l’intérieur du Tick si activé.                       |
| **Alternative**               | Utiliser des **Timers** si les actions peuvent être espacées, pour éviter l’utilisation du Tick. |

***

#### Exemple visuel _(pour ton GitBook si besoin)_ :

* Capture d’écran du **ReceiveTick** activé, utilisant **DeltaSeconds** pour incrémenter un compteur avant d’appeler une action (ex : spawn périodique).
* Illustration comparant l’utilisation du Tick versus des Timers pour la gestion des spawns.

***

#### Remarque

L’utilisation du **ReceiveTick** doit toujours être pesée avec soin pour ne pas impacter les performances globales, surtout dans un système comme le **BP\_SpawnManager** où des alternatives comme les Timers sont souvent plus efficaces.
