---
icon: diagram-project
---

# EventGraph

### Description générale

L’**EventGraph** du Blueprint **BP\_PNJ** contient les événements standards hérités de la classe **Actor**.\
Actuellement, les événements sont présents mais **désactivés**, servant uniquement de placeholders si des fonctionnalités spécifiques doivent être ajoutées à l’avenir.

***

### Détails techniques

| Événement                    | Statut    | Fonctionnalité associée                   |
| ---------------------------- | --------- | ----------------------------------------- |
| **ReceiveBeginPlay**         | Désactivé | Pour initialisation au lancement (vide)   |
| **ReceiveActorBeginOverlap** | Désactivé | Pour détection d’overlap (vide)           |
| **ReceiveTick**              | Désactivé | Pour exécuter du code chaque frame (vide) |

***

### Fonctionnement

#### 1. **ReceiveBeginPlay**

* **Déclenchement prévu** : Quand le jeu commence ou que l’acteur est spawné.
* **Statut actuel** : Désactivé.
*   **Commentaire associé** :

    ```
    Ce nœud est désactivé et ne sera pas appelé.
    Faites glisser les broches pour générer des fonctionnalités.
    ```

**Utilité potentielle** :

* Initialisation du PNJ spécifique au runtime (comportement, animation, état initial).

***

#### 2. **ReceiveActorBeginOverlap**

* **Déclenchement prévu** : Quand un autre acteur entre en collision (overlap) avec le PNJ.
* **Statut actuel** : Désactivé.
* **Paramètre disponible** :
  * **OtherActor** : Référence de l’acteur entrant en contact.
*   **Commentaire associé** :

    ```
    Ce nœud est désactivé et ne sera pas appelé.
    Faites glisser les broches pour générer des fonctionnalités.
    ```

**Utilité potentielle** :

* Réactions du PNJ à une interaction physique (par ex. : début de dialogue, animation spéciale, détection du joueur).

***

#### 3. **ReceiveTick**

* **Déclenchement prévu** : Chaque frame.
* **Statut actuel** : Désactivé.
* **Paramètre disponible** :
  * **DeltaSeconds** : Temps écoulé depuis la dernière frame.
*   **Commentaire associé** :

    ```
    Ce nœud est désactivé et ne sera pas appelé.
    Faites glisser les broches pour générer des fonctionnalités.
    ```

**Utilité potentielle** :

* Exécuter des comportements dynamiques du PNJ frame par frame (ex : regard caméra, déplacements autonomes, timers…).

***

### Bonnes pratiques recommandées

* **Laisser désactivés** les nœuds inutilisés pour préserver les performances.
* **Activer uniquement si un besoin précis apparaît** :
  * BeginPlay : Initialisation comportement spécifique.
  * Overlap : Interaction avec le joueur ou environnement.
  * Tick : Usage léger et conditionné (éviter du code lourd).

***

### Suggestions d’amélioration

* **Ajouter des conditions réseau (HasAuthority)** si les PNJs ont un comportement spécifique serveur/client.
* **Prévoir un booléen d’activation de debug** si certains comportements doivent être testés temporairement.
* Regrouper la logique PNJ récurrente dans des **fonctions dédiées**, appelées uniquement si nécessaire.

***

### Exemple de commentaire Unreal à insérer sur chaque événement désactivé :

```
Événement désactivé – prêt à être utilisé pour [initialisation / interaction / comportement dynamique] du PNJ.
Laisser désactivé pour optimisation tant que non utilisé.
```
