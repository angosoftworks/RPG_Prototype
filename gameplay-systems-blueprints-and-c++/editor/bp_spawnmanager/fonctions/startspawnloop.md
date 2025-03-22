---
description: >-
  Charge les données des PNJs depuis la DataTable et remplit le tableau interne
  des PNJs.
icon: function
---

# StartSpawnLoop

#### 📝 **Description générale**

`StartSpawnLoop` est une fonction interne du Blueprint **BP\_SpawnManager**.\
Elle est responsable de démarrer une boucle périodique de spawn d’acteurs dans les zones de spawn initialisées.\
Elle s'assure qu'il existe des zones valides avant d'initialiser le timer.

***

#### ⚙️ **Détails techniques**

| **Nom de la fonction** | `StartSpawnLoop`                            |
| ---------------------- | ------------------------------------------- |
| **Type**               | Function Blueprint (`K2Node_FunctionEntry`) |
| **Accessibilité**      | Editable (modifiable dans le Blueprint)     |
| **Catégorie**          | Par défaut                                  |
| **Entrées**            | Aucun input personnalisé                    |
| **Sortie**             | Exécution (`Exec`)                          |

***

#### 🔄 **Fonctionnement interne**

1. **Vérification des zones de spawn :**
   * Récupère la longueur de la variable **SpawnZones** (Array d’acteurs BP\_SpawnZone).
   * Si au moins une zone est présente (`Array_Length > 0`), continue l’exécution.
   * Sinon, affiche un message d'erreur avec **PrintString** : `"No Spawn Zones! Check Initialize"`.
2. **Initialisation du Timer :**
   * Utilise **KismetSystemLibrary::K2\_SetTimer** pour lancer la boucle.
   * Le timer appelle régulièrement la fonction **SpawnActor**.
   * Le délai entre chaque appel est défini par la variable **SpawnInterval**.
   * Le timer est configuré en **boucle infinie** (Looping = True).

***

#### 🗺️ **Flow visuel simplifié :**

```
[StartSpawnLoop]
    └── Vérifie si SpawnZones.length > 0 ?
         ├── Oui : Lance le Timer → Appelle SpawnActor à intervalle régulier
         └── Non : Print "No Spawn Zones! Check Initialize"
```

***

#### 🚀 **Utilisation prévue**

* Appelée après **InitializeSpawnZones** pour démarrer le processus de spawn.
* Peut être relancée à tout moment si le système doit être redémarré ou après modification des SpawnZones.

***

#### ✅ **Bonnes pratiques recommandées**

1. **Sécurité :**
   * Très bonne pratique d’avoir ajouté la vérification des SpawnZones avant de démarrer la boucle, évitant des erreurs runtime.
2. **Logs et Debug :**
   * Garder le **PrintString** uniquement activé en développement (déjà bien configuré avec `DevelopmentOnly`).
3. **TimerHandle optionnel :**
   * Tu peux envisager de stocker le **TimerHandle** retourné si besoin de stopper le spawn loop plus tard (via ClearTimer).

***

#### 🌟 **Suggestions d’amélioration possible**

* **Paramètre d’entrée dynamique :**
  * Ajouter un paramètre d’entrée pour customiser le **SpawnInterval** à la volée si besoin (plutôt qu’une variable fixe).
* **Flexibilité sur la fonction appelée :**
  * Rendre la fonction appelée par le timer configurable (actuellement fixée à `"SpawnActor"`).
* **Condition multijoueur :**
  * S'assurer que cette fonction est appelée uniquement côté serveur si applicable, afin d'éviter des duplications d’acteurs côté client.

***

### 🏷️ **Résumé rapide**

| **Responsabilité principale** | Lancer une boucle périodique pour le spawn d’acteurs               |
| ----------------------------- | ------------------------------------------------------------------ |
| **Dépendances**               | BP\_SpawnZone, SpawnInterval, SpawnActor                           |
| **Vérification initiale**     | Vérifie la présence de zones valides                               |
| **Technologie utilisée**      | Timer avec `K2_SetTimer`, looping activé                           |
| **Évolutions possibles**      | Paramètres dynamiques, TimerHandle exposé, flexibilité multijoueur |
