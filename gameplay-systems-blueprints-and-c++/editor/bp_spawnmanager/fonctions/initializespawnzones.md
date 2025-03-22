---
description: Initialise les données du village, en chargeant les informations des PNJs.
icon: function
---

# InitializeSpawnZones

#### 📝 **Description générale**

`InitializeSpawnZones` est une fonction interne du Blueprint **BP\_SpawnManager**.\
Elle est chargée de détecter et référencer toutes les zones de spawn présentes dans le niveau, en les stockant dans une variable accessible pour les autres systèmes (spawning PNJ, événements, gameplay dynamique).

***

#### ⚙️ **Détails techniques**

| **Nom de la fonction** | `InitializeSpawnZones`                      |
| ---------------------- | ------------------------------------------- |
| **Type**               | Function Blueprint (`K2Node_FunctionEntry`) |
| **Accessibilité**      | Editable (modifiable dans le Blueprint)     |
| **Catégorie**          | Par défaut                                  |
| **Entrées**            | Aucun input personnalisé                    |
| **Sortie**             | Exécution (`Exec`)                          |

***

#### 🔄 **Fonctionnement interne**

1. **Recherche des Spawn Zones :**
   * Utilise la fonction **GetAllActorsOfClass** pour récupérer tous les acteurs du type **BP\_SpawnZone** présents dans le niveau.
2. **Stockage :**
   * Le résultat est stocké dans la variable **SpawnZones** (type : Array d’acteurs BP\_SpawnZone).

***

#### 🗺️ **Flow visuel simplifié :**

```
[InitializeSpawnZones] ---> [GetAllActorsOfClass(BP_SpawnZone)] ---> [Set SpawnZones Array]
```

***

#### 🚀 **Utilisation prévue**

* Appelée automatiquement au **BeginPlay** du jeu ou du niveau par le **BP\_SpawnManager**.
* Peut être relancée après une modification du niveau ou lors d'un reset pour rafraîchir la liste des zones disponibles.
* Sert de base à tout système de spawning dynamique (PNJs, objets, ennemis…).

***

#### ✅ **Bonnes pratiques recommandées**

1. **Vérification du résultat :**
   * Après l’appel de **GetAllActorsOfClass**, il est pertinent d’ajouter un log ou une validation pour s’assurer qu’au moins une zone de spawn a été trouvée (éviter des comportements inattendus si aucune zone).
2. **Centralisation de la variable :**
   * La variable **SpawnZones** peut être exposée ou accessible via getter pour permettre à d'autres Blueprints de connaître les zones disponibles.
3. **Optimisation multijoueur :**
   * Si applicable, vérifier que cette fonction est appelée uniquement sur le serveur (éviter duplication d’acteurs côté client).

***

#### 🌟 **Suggestions d’amélioration possible**

* **Ajout d’un paramètre d’entrée (Filtre) :**
  * Par exemple, permettre de filtrer les zones en fonction d’un tag ou d’une propriété (si plusieurs types de zones sont implémentés).
* **Sortie booléenne (Success) :**
  * Ajouter une sortie indiquant si des zones ont bien été détectées.
* **Événement déclenché post-initialisation :**
  * Ajouter un **Custom Event** ou **Delegate** déclenché une fois les zones initialisées, pour permettre aux autres systèmes de s’abonner.

***

### 🏷️ **Résumé rapide**

| **Responsabilité principale** | Initialiser et référencer les zones de spawn du niveau                         |
| ----------------------------- | ------------------------------------------------------------------------------ |
| **Dépendances**               | BP\_SpawnZone, BP\_SpawnManager                                                |
| **Quand l’appeler**           | BeginPlay, reset du niveau, ou mise à jour dynamique                           |
| **Variable principale**       | SpawnZones (Array d’acteurs BP\_SpawnZone)                                     |
| **Évolutions possibles**      | Validation du résultat, sortie booléenne, filtrage avancé, support multijoueur |
