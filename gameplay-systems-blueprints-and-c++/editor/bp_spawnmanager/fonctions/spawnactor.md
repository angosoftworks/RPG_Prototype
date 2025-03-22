---
description: >-
  Convertit une Map de relations en tableau structuré pour un traitement plus
  flexible.
icon: function
---

# SpawnActor

#### 📝 **Description générale**

La fonction **SpawnActor** est utilisée pour générer dynamiquement des acteurs dans le monde, depuis une des zones de spawn disponibles.

Elle vérifie d'abord si le nombre maximal d'acteurs n'est pas dépassé, puis choisit une zone aléatoirement, et y fait apparaître un acteur du type défini.

***

#### ⚙️ **Détails techniques**

| **Nom de la fonction** | `SpawnActor`                                |
| ---------------------- | ------------------------------------------- |
| **Type**               | Function Blueprint (`K2Node_FunctionEntry`) |
| **Accessibilité**      | Editable (modifiable dans le Blueprint)     |
| **Catégorie**          | Par défaut                                  |
| **Entrées**            | Aucun input spécifique                      |
| **Sortie**             | Exécution (`Exec`)                          |

***

#### 🔄 **Fonctionnement interne**

1. **Vérification du nombre d'acteurs déjà spawns :**
   * La variable **SpawnedActors** est un array stockant tous les acteurs déjà générés.
   * La fonction vérifie si la longueur de **SpawnedActors** est inférieure à **MaxSpawnedActors**.
2. **Choix d'une zone de spawn aléatoire :**
   * Sélectionne aléatoirement un élément de l'array **SpawnZones** (de type **BP\_SpawnZone\_C**).
3. **Détermination d'une position aléatoire :**
   * Appelle la fonction **GetRandomPointInZone** sur la zone choisie pour obtenir une position précise dans la zone.
4. **Spawn de l'acteur :**
   * Utilise **SpawnActorFromClass** pour faire apparaître l’acteur à la position choisie.
   * L’acteur spawné est du type défini par la variable **ActorToSpawn**.
   * La position est convertie en Transform via **Conv\_VectorToTransform**.
5. **Ajout de l'acteur dans la liste :**
   * Ajoute l’acteur fraîchement spawné à l'array **SpawnedActors** pour le suivi.

***

#### 🗺️ **Flow visuel simplifié :**

```
[SpawnActor]
 └── Si (SpawnedActors.Length < MaxSpawnedActors)
      └── Choisir une SpawnZone aléatoire
           └── Obtenir un point aléatoire dans la zone
                └── Spawn Actor (ActorToSpawn) à cette position
                     └── Ajouter l'acteur à SpawnedActors
```

***

#### 📋 **Variables utilisées**

| **Variable**         | **Type**                  | **Rôle**                                      |
| -------------------- | ------------------------- | --------------------------------------------- |
| **SpawnedActors**    | Array d'Actor             | Liste des acteurs déjà spawns                 |
| **MaxSpawnedActors** | Integer                   | Nombre maximum d'acteurs pouvant être générés |
| **SpawnZones**       | Array de BP\_SpawnZone\_C | Zones disponibles pour le spawn               |
| **ActorToSpawn**     | Classe d'Actor            | Classe d'acteur à instancier                  |

***

#### 🚀 **Utilisation prévue**

* Appelée périodiquement par la fonction **StartSpawnLoop**, tant que la limite de spawn n'est pas atteinte.
* Permet de remplir le monde progressivement avec des acteurs.

***

#### ✅ **Bonnes pratiques appliquées**

1. **Vérification avant spawn :**
   * Excellente pratique : évite un dépassement du nombre d’acteurs en comparant avec **MaxSpawnedActors**.
2. **Gestion dynamique des zones :**
   * Sélection aléatoire d'une zone permet une distribution variée.
3. **Centralisation du suivi :**
   * Tous les acteurs spawnés sont référencés dans **SpawnedActors**, facilitant un éventuel despawn ou reset.

***

#### 🌟 **Suggestions d'amélioration possible**

1. **Nettoyage des SpawnedActors :**
   * Ajouter une logique pour supprimer les entrées invalides ou détruire les acteurs quand ils ne sont plus nécessaires (par ex. sur changement de scène).
2. **Paramètres dynamiques :**
   * Permettre de définir le type d’acteur à spawn via un paramètre d’entrée, pour plus de flexibilité.
3. **Pooling :**
   * Pour de meilleures performances, envisager un système d'object pooling plutôt qu'un spawn/destroy constant.

***

### 🏷️ **Résumé rapide**

| **Responsabilité principale** | Faire apparaître un acteur dans une zone aléatoire |
| ----------------------------- | -------------------------------------------------- |
| **Contrôle de conditions**    | MaxSpawnedActors                                   |
| **Dépendances**               | SpawnZones, SpawnedActors, ActorToSpawn            |
| **Technologie utilisée**      | Array\_Length, Random Array, SpawnActorFromClass   |
| **Évolutions possibles**      | Object pooling, nettoyage, paramètres dynamiques   |
