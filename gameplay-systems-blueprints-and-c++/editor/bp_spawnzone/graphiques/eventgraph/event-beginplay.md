---
icon: arrow-right-to-bracket
---

# Event BeginPlay

#### Description

Cet événement hérité d'`Actor` dans Unreal Engine est déclenché automatiquement lorsque l’acteur entre en jeu (c’est-à-dire lors du début du niveau ou lorsqu’il est spawn dynamiquement).

***

#### Détails techniques

| Propriété              | Valeur                                                                                                                              |
| ---------------------- | ----------------------------------------------------------------------------------------------------------------------------------- |
| **Nom de l'événement** | ReceiveBeginPlay                                                                                                                    |
| **Classe Parent**      | `Actor`                                                                                                                             |
| **Override Function**  | `True`                                                                                                                              |
| **État**               | **Désactivé**                                                                                                                       |
| **Commentaire**        | `"Ce nœud est désactivé et ne sera pas appelé.\nFaites glisser les broches pour générer des fonctionnalités."`                      |
| **NodeGuid**           | `ED6CCDEC4385D22E721F889464245ED8`                                                                                                  |
| **Pins**               | \<ul>\<li>**OutputDelegate** : Type = `delegate` (lié à ReceiveBeginPlay)\</li>\<li>**then** : Exécution, non connectée\</li>\</ul> |

***

#### Pourquoi désactivé ?

* **Performance** : Tant que tu n’as pas besoin d’exécuter une logique au démarrage de ton spawn zone, il est préférable de le désactiver.
* **Clarté** : Le commentaire indique clairement aux autres développeurs que l’événement est volontairement inactif.

***

#### Potentiel d’utilisation future

Voici quelques exemples de ce que tu pourrais faire avec ce nœud si tu l’actives :

| Utilisation Possible                                                                                       |
| ---------------------------------------------------------------------------------------------------------- |
| Initialiser des variables ou des états de la zone (ex : reset d’un compteur d’acteurs).                    |
| Démarrer un timer pour un cooldown lié à la zone.                                                          |
| Effectuer des traces ou des calculs spécifiques à la zone avant que le joueur n’interagisse avec celle-ci. |
| Afficher une animation, un effet visuel ou un message à l’entrée en jeu.                                   |

***

#### Recommandations

* **Garder désactivé tant qu’aucune logique n’est nécessaire.**
* **Ajouter un commentaire personnalisé** si tu veux expliquer pourquoi il est désactivé (ex : optimisation, logique implémentée ailleurs).
* **Activer si besoin** d’un comportement spécifique au spawn de la zone (initialisation dynamique).
