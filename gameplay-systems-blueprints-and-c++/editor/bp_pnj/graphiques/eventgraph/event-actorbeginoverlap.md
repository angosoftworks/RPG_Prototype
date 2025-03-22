---
icon: arrow-right-to-bracket
---

# Event ActorBeginOverlap

### Description générale

L’événement **ReceiveActorBeginOverlap** est appelé lorsqu’un autre acteur entre en collision (overlap) avec le PNJ.\
Actuellement, ce nœud est **désactivé** et n’a aucune logique définie, mais il peut être utilisé dans le futur pour gérer des interactions contextuelles, comme détecter la présence du joueur ou déclencher des animations.

***

### Détails techniques

| Propriété                  | Valeur                                                      |
| -------------------------- | ----------------------------------------------------------- |
| **Nom de l’événement**     | ReceiveActorBeginOverlap                                    |
| **Classe parente**         | `Actor`                                                     |
| **Override**               | Oui (`bOverrideFunction=True`)                              |
| **Statut**                 | **Désactivé** (`EnabledState=Disabled`)                     |
| **Position dans le graph** | Y: 208                                                      |
| **Paramètre disponible**   | `OtherActor` (Référence de l’acteur qui entre en collision) |

***

### Fonctionnement actuel

* **État** : Le nœud est désactivé et aucune logique n’est définie.
*   **Commentaire existant** :

    ```
    Ce nœud est désactivé et ne sera pas appelé.
    Faites glisser les broches pour générer des fonctionnalités.
    ```

***

### Utilisation potentielle

Le **ReceiveActorBeginOverlap** peut être activé et utilisé pour :

* **Détecter le joueur** ou un autre PNJ entrant en collision avec le PNJ.
* **Déclencher un dialogue** lorsque le joueur s'approche.
* **Activer un comportement spécifique** (animation, fuite, attaque…).
* **Déclencher une quête ou un événement** contextuel.

***

### Bonnes pratiques recommandées

* **Valider l’acteur entrant** (`OtherActor`) pour s’assurer qu'il correspond au type attendu (via `Cast` ou `Tags`).
* **Limiter les traitements coûteux** dans cet événement, car les overlaps peuvent être fréquents.
* **Utiliser des collisions précises** pour éviter des appels inutiles (via des volumes ou collision presets adaptés).

***

### Suggestions d’amélioration future

* Ajouter une **vérification réseau** (`HasAuthority`) si les interactions doivent être gérées uniquement côté serveur.
* Coupler cet événement avec un **système d’état** du PNJ pour varier les réactions selon le contexte (par ex. : dialogue seulement si PNJ disponible).
* Utiliser des **interfaces Blueprint** pour déclencher des interactions sans dépendance forte sur l’acteur entrant.

***

### Exemple de commentaire à insérer dans Unreal :

```
Événement désactivé. Peut être activé pour réagir aux overlaps (ex : détection du joueur, déclenchement de dialogue ou animation).
Valider OtherActor avant de traiter.
```
