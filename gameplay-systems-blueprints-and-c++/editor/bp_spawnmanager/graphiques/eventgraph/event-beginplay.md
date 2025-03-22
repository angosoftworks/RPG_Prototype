---
icon: arrow-right-to-bracket
---

# Event BeginPlay

#### Description générale

`ReceiveBeginPlay` est un événement standard hérité de la classe **Actor**. Il est automatiquement déclenché au **début du jeu** ou lorsque l’acteur est spawné dans le monde. Cet événement est idéal pour initialiser des variables, préparer des systèmes ou lancer des processus dès que l’acteur entre en jeu.

Dans ton Blueprint **BP\_SpawnManager**, l’événement **ReceiveBeginPlay** est actuellement désactivé. Il est cependant déjà présent, prêt à être activé et utilisé pour toute logique d’initialisation nécessaire.

***

#### Détails techniques

| Propriété                  | Valeur                                                                                                      |
| -------------------------- | ----------------------------------------------------------------------------------------------------------- |
| **Nom de l’événement**     | ReceiveBeginPlay                                                                                            |
| **Défini dans**            | `/Game/Blueprints/BP_SpawnManager`                                                                          |
| **Type d’événement**       | BeginPlay                                                                                                   |
| **Appelé automatiquement** | Oui, au début du jeu ou lors du spawn de l’acteur                                                           |
| **Statut actuel**          | Désactivé                                                                                                   |
| **Commentaire visible**    | Oui, indiquant que le nœud est désactivé                                                                    |
| **Commentaire**            | "Ce nœud est désactivé et ne sera pas appelé. Faites glisser les broches pour générer des fonctionnalités." |

***

#### Comportement

* **Déclenchement automatique** : Si activé, cet événement est appelé dès que l’acteur est actif dans le monde (au lancement ou lorsqu'il est spawné dynamiquement).
* **Initialisation** : Parfait pour préparer des variables, systèmes de spawn, remplissage de pool, configuration d’UI, etc.
* **Actuellement désactivé** : Le nœud est présent mais non fonctionnel. Peut être activé facilement pour ajouter de la logique.

***

#### Utilisation prévue

Dans le contexte du **BP\_SpawnManager**, cet événement pourrait être utilisé pour :

* Initialiser le **ActorPool**.
* Remplir dynamiquement la liste des **SpawnZones**.
* Vérifier et préparer les paramètres comme **MaxSpawnedActors** ou **bUsePooling**.
* Lancer des timers pour commencer le spawning basé sur **SpawnInterval**.

***

#### Bonnes pratiques

* **Événement léger** : Éviter d’y mettre des opérations lourdes, préférer déléguer aux systèmes spécialisés (ex : utiliser un manager ou des timers).
* **Séparer l’initialisation du gameplay** : Utiliser BeginPlay uniquement pour l’initialisation, garder la logique gameplay principale ailleurs.
* **Validation** : Vérifier que toutes les références critiques (zones, pools, paramètres) sont valides au moment de BeginPlay.

***

#### Suggestions d’améliorations

| Suggestion                | Détail                                                                                                       |
| ------------------------- | ------------------------------------------------------------------------------------------------------------ |
| **Activer si besoin**     | Si une initialisation spécifique est nécessaire, activer cet événement et documenter son usage.              |
| **Organisation visuelle** | Ajouter un commentaire clair expliquant les blocs d’initialisation utilisés dans BeginPlay.                  |
| **Optimisation**          | Si plusieurs initialisations sont requises, regrouper la logique dans une fonction appelée depuis BeginPlay. |

***

#### Exemple visuel _(facultatif pour GitBook)_ :

* Capture d’écran du **ReceiveBeginPlay** activé, avec des blocs pour initialiser les variables du **SpawnManager**.
* Illustration d’un appel à une fonction dédiée à la préparation du système de spawn depuis BeginPlay.

***

#### Remarque

Même désactivé, le **ReceiveBeginPlay** est un point stratégique dans Unreal pour tout ce qui concerne la mise en place initiale de l’acteur. Dans un système comme le **BP\_SpawnManager**, il est particulièrement adapté pour préparer le terrain avant le début effectif du gameplay.
