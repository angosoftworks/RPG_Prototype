---
icon: arrow-right-to-bracket
---

# Event ActorBeginOverlap

### Description générale

L’événement **ReceiveActorBeginOverlap** est déclenché lorsqu’un autre acteur entre en collision (overlap) avec l’acteur `BP_Manager`.\
**Actuellement**, il est désactivé et ne contient aucune logique, mais il peut être utilisé ultérieurement pour détecter des interactions spécifiques ou déclencher des événements contextuels.

***

### Détails techniques

| Propriété                  | Valeur                                  |
| -------------------------- | --------------------------------------- |
| **Nom de l’événement**     | ReceiveActorBeginOverlap                |
| **Classe parente**         | `Actor`                                 |
| **Override**               | Oui (`bOverrideFunction=True`)          |
| **Position dans le graph** | Y: 208                                  |
| **Statut**                 | **Désactivé** (`EnabledState=Disabled`) |

***

### Fonctionnement

* **Déclenchement prévu** : Quand un autre acteur entre en overlap avec `BP_Manager`.
* **Paramètre disponible** :
  * **OtherActor** _(Actor Object Reference)_ : L’acteur ayant déclenché l’overlap.

**Remarque actuelle** :

```
Ce nœud est désactivé et ne sera pas appelé.
Faites glisser les broches pour générer des fonctionnalités.
```

Le nœud est présent à titre préparatoire, mais sans impact sur le gameplay actuel.

***

### Utilisation potentielle

Bien que désactivé, cet événement pourrait être utilisé dans le futur pour :

* Détecter si le joueur ou un PNJ entre dans une zone spécifique contrôlée par `BP_Manager`.
* Déclencher des événements de gameplay contextuels (ex : cinématique, dialogue, mise à jour de quête).
* Contrôler l’état du village en fonction d’interactions physiques avec d'autres acteurs.

***

### Bonnes pratiques recommandées

* **Laisser désactivé tant qu’il n’y a pas d’usage** pour éviter toute surcharge inutile.
* **Ajouter une condition (`IsValid`, `Cast`, etc.)** pour vérifier la nature de `OtherActor` si activé.
* **Commenter clairement l’objectif du nœud** si une logique est ajoutée, pour assurer la maintenabilité.

***

### Suggestion d’amélioration future

* Si activé, prévoir un système d’identification de l’acteur entrant (par exemple via tags ou interface Blueprint).
* Ajouter une logique réseau si le projet devient multijoueur : exécuter l’overlap uniquement sur le serveur si nécessaire.
