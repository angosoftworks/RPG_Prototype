---
icon: arrow-right-to-bracket
---

# Event Tick

### Description générale

L’événement **ReceiveTick** est appelé à chaque frame pour l’acteur `BP_Manager`.\
Dans sa configuration actuelle, il est **désactivé** et ne contient aucune logique.\
Son activation permettrait d'exécuter du code en continu, mais il est volontairement laissé vide pour optimiser les performances.

***

### Détails techniques

| Propriété                  | Valeur                                                         |
| -------------------------- | -------------------------------------------------------------- |
| **Nom de l’événement**     | ReceiveTick                                                    |
| **Classe parente**         | `Actor`                                                        |
| **Override**               | Oui (`bOverrideFunction=True`)                                 |
| **Position dans le graph** | Y: 416                                                         |
| **Statut**                 | **Désactivé** (`EnabledState=Disabled`)                        |
| **Paramètre**              | `DeltaSeconds` (float) – Temps écoulé depuis la dernière frame |

***

### Fonctionnement

* **Déclenchement prévu** : À chaque frame du jeu (si activé).
* **Paramètre disponible** :
  * **DeltaSeconds** : Temps écoulé entre deux frames, utile pour des calculs dépendants du temps (ex : animations, timers).

**Remarque actuelle :**

```
Ce nœud est désactivé et ne sera pas appelé.
Faites glisser les broches pour générer des fonctionnalités.
```

Le nœud est présent pour une éventuelle utilisation future, mais ne contribue actuellement à aucun traitement.

***

### Utilisation potentielle

Le **ReceiveTick** peut être activé pour :

* Exécuter des vérifications ou des actions nécessitant une mise à jour constante (par ex. : surveiller un état global, gérer un timer spécifique au village).
* Contrôler dynamiquement des comportements du village en temps réel.

***

### Bonnes pratiques recommandées

* **Laisser désactivé par défaut** : Le Tick peut être coûteux en performance, surtout pour un manager qui ne nécessite pas de traitement frame par frame.
* **Si activé** :
  * **Limiter l’usage** : Ne pas y mettre de calculs lourds ou inutiles.
  * **Utiliser un booléen d'activation conditionnelle** si la logique n'est pas toujours nécessaire.
  * **Désactiver le Tick** dans le **Construction Script** ou via **`SetActorTickEnabled(false)`** si certaines conditions sont remplies.

***

### Suggestion d’amélioration future

* Si besoin ponctuel d’un Tick-like :
  * **Utiliser des Timers** Unreal qui sont plus performants et contrôlables que le Tick.
* Intégrer une logique réseau : S'assurer que tout traitement sensible est effectué uniquement sur le serveur, si applicable.
