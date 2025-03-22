---
icon: function
---

# RecycleActor

#### 📝 **Description générale**

La fonction **RecycleActor** gère le recyclage (désactivation) d’un acteur en le rendant invisible, en désactivant sa collision et son tick, puis en l’ajoutant à un pool d’acteurs réutilisables.

Cette approche permet d’éviter la destruction/recréation d’acteurs, optimisant ainsi les performances grâce à l’implémentation d’un **Object Pooling**.

***

#### ⚙️ **Détails techniques**

| **Nom de la fonction** | `RecycleActor`                                |
| ---------------------- | --------------------------------------------- |
| **Type**               | Function Blueprint (`K2Node_FunctionEntry`)   |
| **Accessibilité**      | Editable                                      |
| **Entrée**             | **ActorToRecycle** – Référence à un **Actor** |
| **Sortie**             | Aucun                                         |

***

#### 🔄 **Fonctionnement interne**

1. **Masquer l’acteur :**
   * Appelle **SetActorHiddenInGame(true)** pour cacher visuellement l’acteur dans le jeu.
2. **Désactiver les collisions :**
   * Appelle **SetActorEnableCollision(false)** pour éviter toute interaction physique.
3. **Désactiver le tick :**
   * Appelle **SetActorTickEnabled(false)** pour empêcher l’acteur d’exécuter du code à chaque frame.
4. **Ajout dans le pool d’acteurs :**
   * Utilise **Array\_Add** pour stocker l’acteur recyclé dans la variable **ActorPool** (array d’acteurs).
   * Ce pool servira à réutiliser ces acteurs plutôt que d’en recréer, en améliorant les performances.

***

#### 🗺️ **Flow visuel simplifié :**

```
scssCopierModifier[RecycleActor]
 ├── SetActorHiddenInGame(true)
 ├── SetActorEnableCollision(false)
 ├── SetActorTickEnabled(false)
 └── Array_Add(ActorPool, ActorToRecycle)
```

***

#### 📋 **Variables utilisées**

| **Variable / Node**         | **Type**                    | **Rôle**                                      |
| --------------------------- | --------------------------- | --------------------------------------------- |
| **ActorToRecycle**          | Actor                       | Acteur à désactiver et réinsérer dans le pool |
| **ActorPool**               | Array d’Actor Références    | Pool contenant les acteurs recyclés           |
| **SetActorHiddenInGame**    | Fonction Actor              | Masque l’acteur visuellement                  |
| **SetActorEnableCollision** | Fonction Actor              | Désactive la collision                        |
| **SetActorTickEnabled**     | Fonction Actor              | Désactive le Tick                             |
| **Array\_Add**              | Fonction KismetArrayLibrary | Ajoute l’acteur recyclé au pool               |

***

#### ✅ **Points forts**

1. **Optimisation performance :**
   * Utilise l’**Object Pooling**, réduisant drastiquement le coût CPU/GPU/mémoire lié à la destruction/création d’acteurs.
2. **Simplicité et efficacité :**
   * Le processus est clair : masquer, désactiver, stocker.
3. **Réutilisabilité facile :**
   * Le pool peut être utilisé plus tard pour respawn ou repositionner ces acteurs.

***

#### 🌟 **Suggestions d’amélioration possible**

1. **Vérification de doublons dans le pool :**
   * Actuellement, l’acteur est ajouté sans vérification. Ajouter un check pour éviter d’avoir plusieurs fois le même acteur.
2. **Réinitialisation facultative des variables :**
   * Si les acteurs possèdent des variables spécifiques (santé, état), prévoir un reset avant recyclage.
3. **Notification ou callback :**
   * Éventuellement, notifier l’acteur recyclé (via un Event) pour qu’il réinitialise ses propres composants ou états.

***

#### 🏷️ **Résumé rapide**

| **Responsabilité principale** | Désactiver et stocker un acteur inutilisé pour réutilisation future |
| ----------------------------- | ------------------------------------------------------------------- |
| **Entrée principale**         | ActorToRecycle (Actor)                                              |
| **Actions clés**              | Masquer, désactiver collisions/tick, ajouter au pool                |
| **Dépendances**               | ActorPool, Actor functions (Hidden, Collision, Tick)                |
| **Design Pattern**            | **Object Pooling**                                                  |
