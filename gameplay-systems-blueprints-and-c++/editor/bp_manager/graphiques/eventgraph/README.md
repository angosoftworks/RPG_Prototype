---
icon: diagram-project
---

# EventGraph

### Description générale

Le **EventGraph** du Blueprint `BP_Manager` contient les événements clés liés à l'initialisation et à la gestion du village.\
Il centralise principalement :

* Le déclenchement de l'initialisation des données du village.
* Le spawn des PNJs au lancement du jeu.

Certaines fonctions sont également préparées mais désactivées par défaut (comme l’overlap ou le tick).

***

### Détails techniques

| Événement                    | Statut    | Fonctionnalité associée                             |
| ---------------------------- | --------- | --------------------------------------------------- |
| **ReceiveBeginPlay**         | Actif     | Initialise les données du village et spawn les PNJs |
| **ReceiveActorBeginOverlap** | Désactivé | Prêt pour détection d'overlaps si activé            |
| **ReceiveTick**              | Désactivé | Prêt pour exécuter du code chaque frame si activé   |

***

### Fonctionnement principal

#### 1. **ReceiveBeginPlay**

Événement appelé automatiquement au début du jeu ou lorsque l'acteur est spawné.

**Flow d'exécution :**

```
[ReceiveBeginPlay]
    ↓
[KismetSystemLibrary → PrintString : "BP_Manager → Village Initialization Started"]
    ↓
[InitializeVillageData]
    ↓
[SpawnAllPNJs]
```

**Détails :**

* **PrintString** :
  * Affiche `"BP_Manager → Village Initialization Started"` à l'écran & log.
  * Utilisé pour confirmer visuellement le lancement du système.
* **InitializeVillageData** :
  * Appelle la fonction dédiée pour charger les données des PNJs du village.
* **SpawnAllPNJs** :
  * Fait apparaître tous les PNJs en fonction des données précédemment chargées.

***

#### 2. **ReceiveActorBeginOverlap** _(Désactivé)_

* Ce nœud est désactivé par défaut.
* Commentaire :\
  `"Ce nœud est désactivé et ne sera pas appelé. Faites glisser les broches pour générer des fonctionnalités."`

**Utilité possible :**

* Pour détecter des interactions entre l’acteur `BP_Manager` et d'autres acteurs via collisions (ex : déclencher un événement au contact).

***

#### 3. **ReceiveTick** _(Désactivé)_

* Également désactivé par défaut.
* Même commentaire que le précédent.

**Utilité possible :**

* Pour exécuter des actions à chaque frame (non recommandé ici sauf besoin spécifique, car BP\_Manager semble orienté data).

***

### Bonnes pratiques recommandées

* **Laisser les nœuds désactivés non utilisés** pour éviter des coûts inutiles en performance.
* **Commenter** les nœuds actifs, notamment :
  * Pourquoi on utilise `PrintString` (debug, confirmation visuelle).
  * Ce que fait chaque appel (`InitializeVillageData`, `SpawnAllPNJs`).
* **Prévoir une vérification dans le Print ou après `InitializeVillageData`** pour s’assurer que les données sont correctement chargées.

***

### Suggestions d’amélioration

* Ajouter une **condition serveur** (`HasAuthority`) autour du `BeginPlay` si le jeu devient multijoueur.
* Utiliser un **booléen de debug** pour activer/désactiver facilement le `PrintString` en développement.
* Activer `ReceiveActorBeginOverlap` uniquement si un besoin concret (ex : trigger zone) apparaît, pour garder le graph clean.
