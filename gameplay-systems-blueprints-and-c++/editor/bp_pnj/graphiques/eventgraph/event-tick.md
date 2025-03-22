---
icon: arrow-right-to-bracket
---

# Event Tick

### Description générale

L’événement **ReceiveTick** est appelé à **chaque frame** pour le PNJ.\
Dans le Blueprint **BP\_PNJ**, ce nœud est actuellement **désactivé** et ne contient aucune logique.\
Il est prévu pour des cas où un comportement dynamique ou continu du PNJ est requis.

***

### Détails techniques

| Propriété                  | Valeur                                                         |
| -------------------------- | -------------------------------------------------------------- |
| **Nom de l’événement**     | ReceiveTick                                                    |
| **Classe parente**         | `Actor`                                                        |
| **Override**               | Oui (`bOverrideFunction=True`)                                 |
| **Statut**                 | **Désactivé** (`EnabledState=Disabled`)                        |
| **Position dans le graph** | Y: 416                                                         |
| **Paramètre disponible**   | `DeltaSeconds` (float) – Temps écoulé depuis la dernière frame |

***

### Fonctionnement actuel

* **État** : Le nœud est désactivé, il ne sera pas exécuté.
*   **Commentaire existant** :

    ```
    Ce nœud est désactivé et ne sera pas appelé.
    Faites glisser les broches pour générer des fonctionnalités.
    ```

***

### Utilisation potentielle

Le **ReceiveTick** peut être utilisé pour :

* Appliquer des comportements dynamiques en temps réel (ex : suivi du joueur, animation procédurale, regard dynamique…).
* Gérer des timers ou des compteurs propres à chaque PNJ.
* Détecter des conditions de gameplay spécifiques (par exemple : si un PNJ doit changer d'état après X secondes).

***

### Bonnes pratiques recommandées

* **Limiter l'utilisation du Tick** pour préserver les performances, surtout s'il y a beaucoup de PNJs.
* Préférer les **Timers** ou les événements déclenchés conditionnellement lorsque possible.
* Si utilisé :
  * Ajouter un **booléen d'activation conditionnelle** (ex : bIsTicking) pour désactiver le Tick quand inutile.
  * Nettoyer la logique après qu’elle ait accompli son rôle (désactivation manuelle).

***

### Suggestions d’amélioration future

* Utiliser **`SetActorTickEnabled(false)`** dès qu'il n’est plus nécessaire.
* Ajouter un système de **LOD comportemental** : désactiver le Tick pour les PNJs éloignés du joueur.
* En multijoueur, prévoir que certaines logiques ne s’exécutent **que côté serveur** si pertinent (via **`HasAuthority()`**).

***

### Exemple de commentaire à insérer dans Unreal :

```
Événement désactivé. Peut être activé pour appliquer des comportements dynamiques (déplacement, suivi, timer...) du PNJ à chaque frame.
À utiliser avec précaution pour éviter toute surcharge de performance.
```
