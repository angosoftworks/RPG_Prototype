---
icon: arrow-right-to-bracket
---

# Event Tick

#### Description

Cet événement est appelé **à chaque frame**, tant que l'acteur est actif dans la scène. Cela te permet d'exécuter du code en continu, par exemple pour des vérifications, des animations custom ou des comportements dynamiques.

***

#### Détails techniques

| Propriété              | Valeur                                                                                                                                                                                                     |
| ---------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Nom de l'événement** | ReceiveTick                                                                                                                                                                                                |
| **Classe Parent**      | `Actor`                                                                                                                                                                                                    |
| **Override Function**  | `True`                                                                                                                                                                                                     |
| **État**               | **Désactivé**                                                                                                                                                                                              |
| **Position Y**         | `416`                                                                                                                                                                                                      |
| **Commentaire**        | `"Ce nœud est désactivé et ne sera pas appelé.\nFaites glisser les broches pour générer des fonctionnalités."`                                                                                             |
| **NodeGuid**           | `FE1A37A941DF4FE702C9859253332860`                                                                                                                                                                         |
| **Pins**               | \<ul>\<li>**OutputDelegate** : Type = `delegate` (lié à ReceiveTick)\</li>\<li>**then** : Exécution, non connecté\</li>\<li>**DeltaSeconds** : Float, le temps écoulé depuis la dernière frame\</li>\</ul> |

***

#### Utilisation typique

| Exemples                                                                                     |
| -------------------------------------------------------------------------------------------- |
| Faire un **compteur ou timer manuel** basé sur `DeltaSeconds`.                               |
| Déplacer ou faire évoluer un acteur de manière fluide (ex : translation, rotation continue). |
| Vérifier constamment certaines conditions (proximité, état, etc.).                           |
| Décrémenter un cooldown ou temps d’attente personnalisé.                                     |
| Debugging visuel en temps réel (affichage texte, gizmos, etc.).                              |

***

#### Pourquoi désactivé ici ?

* **Optimisation** : Le `Tick` est **coûteux en performances**, surtout si mal utilisé. Tu évites donc les calculs inutiles en le laissant désactivé.
* **Pas de logique nécessitant un traitement constant** dans ce Blueprint précis (`BP_SpawnZone`).
* **Mieux vaut utiliser des Timers ou Events** déclenchés ponctuellement (comme OnOverlap) plutôt qu'un Tick global pour des cas simples.

***

#### Recommandations

| Action                                                                                                        | Pourquoi ?                                                            |
| ------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------- |
| **Laisser désactivé tant qu'il n'y a pas besoin de logique frame par frame.**                                 | Évite la consommation CPU/GPU inutile.                                |
| **Utiliser plutôt des Timers (SetTimerByFunctionName)** ou des événements pour des comportements cadencés.    | Moins gourmand, plus lisible et contrôlable.                          |
| **Activer uniquement si besoin (ex : interpolation, suivi dynamique)** et ajouter un **DisableTickWhenIdle**. | Pour des fonctionnalités précises nécessitant du suivi en temps réel. |
