---
icon: arrow-right-to-bracket
---

# Event ActorBeginOverlap

#### Description

Cet événement est appelé lorsque **n'importe quel autre acteur** commence à entrer en collision avec l'acteur actuel (ici ton `BP_SpawnZone`). C’est une fonction native d'`Actor` très utile pour déclencher des comportements lorsqu'une interaction physique ou une collision commence.

***

#### Détails techniques

| Propriété              | Valeur                                                                                                                                                                                                                               |
| ---------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Nom de l'événement** | ReceiveActorBeginOverlap                                                                                                                                                                                                             |
| **Classe Parent**      | `Actor`                                                                                                                                                                                                                              |
| **Override Function**  | `True`                                                                                                                                                                                                                               |
| **État**               | **Désactivé**                                                                                                                                                                                                                        |
| **Position Y**         | `208`                                                                                                                                                                                                                                |
| **Commentaire**        | `"Ce nœud est désactivé et ne sera pas appelé.\nFaites glisser les broches pour générer des fonctionnalités."`                                                                                                                       |
| **NodeGuid**           | `2211C61D430D46C92C436F86F30BAD14`                                                                                                                                                                                                   |
| **Pins**               | \<ul>\<li>**OutputDelegate** : Type = `delegate` (lié à ReceiveActorBeginOverlap)\</li>\<li>**then** : Exécution, non connectée\</li>\<li>**OtherActor** : Type = `Actor` - Référence de l’acteur qui a débuté l'overlap\</li>\</ul> |

***

#### Utilisation typique

Cet événement peut être utilisé pour :

| Exemples                                                                                                               |
| ---------------------------------------------------------------------------------------------------------------------- |
| Déclencher le spawn d’un acteur spécifique lorsqu’un joueur ou objet rentre dans la zone.                              |
| Commencer un cooldown ou une animation d’activation quand un overlap est détecté.                                      |
| Vérifier si l’acteur entrant remplit certaines conditions (ex : une classe particulière) avant d’effectuer une action. |
| Collecter ou supprimer des acteurs spécifiques lorsqu'ils entrent dans la zone.                                        |

***

#### Pourquoi désactivé ici ?

* **Contrôle de logique** : Peut-être que tu utilises une **Box Collision** ou un autre composant pour gérer les overlaps à un niveau plus fin (via le composant directement plutôt qu’au niveau `Actor`).
* **Éviter des appels inutiles** si tu n'as pas encore besoin de cette logique.
* **Clarté** : Commentaire clair indiquant qu’il n’est pas encore exploité.

***

#### Recommandations

| Action                                                                                                         | Pourquoi ?                                                                  |
| -------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------- |
| **Laisser désactivé tant qu'aucune logique n'est requise.**                                                    | Optimisation & clarté.                                                      |
| **L’activer si besoin de gérer des entrées dans la zone au niveau Actor.**                                     | Pour un contrôle global sans passer par des composants.                     |
| **Déplacer la logique vers le composant Box si tu veux un overlap plus précis (via OnComponentBeginOverlap).** | Plus précis, contrôle par composant, moins coûteux qu’un test global Actor. |
