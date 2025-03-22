---
icon: function
---

# SpawnALLPNJs

#### **Description générale :**

`SpawnAllPNJs` est une fonction du Blueprint **`BP_Manager`** qui permet de **spawner dynamiquement tous les PNJs** définis dans un tableau de données (struct `Struct_PNJData`). Chaque PNJ est instancié avec ses informations spécifiques (nom, profession, relations, traits, etc.) et positionné aléatoirement sur un des points de spawn ou volumes définis.

***

#### **Détails techniques :**

| Propriété              | Détail                                      |
| ---------------------- | ------------------------------------------- |
| **Nom de la fonction** | `SpawnAllPNJs`                              |
| **Type de fonction**   | Function Blueprint (`K2Node_FunctionEntry`) |
| **Accessibilité**      | Public                                      |
| **Entrées**            | Aucune                                      |
| **Sorties**            | Aucune (tout est géré en interne)           |

***

#### **Variables utilisées :**

| Variable           | Type                      | Description                                                                                            |
| ------------------ | ------------------------- | ------------------------------------------------------------------------------------------------------ |
| `PNJDataArray`     | Array of `Struct_PNJData` | Tableau contenant les données de chaque PNJ à instancier.                                              |
| `SpawnPointsArray` | Array of `Actor`          | Liste d’acteurs servant de points de spawn fixes pour les PNJs.                                        |
| `SpawnZoneVolume`  | Array of `Actor`          | Liste d’acteurs représentant des volumes où les PNJs peuvent être spawnés de manière aléatoire.        |
| `SpawnedPNJArray`  | Array of `BP_PNJ`         | Tableau contenant les références des PNJs une fois spawnés (pour réutilisation ou gestion ultérieure). |

***

#### **Fonctionnement :**

**Étapes internes :**

1. **Boucle ForEach sur `PNJDataArray`:**
   * Parcourt chaque struct contenant les infos d’un PNJ.
2. **Détermination d’un point de spawn :**
   * Deux options :
     * Sélection d’un **SpawnPoint** aléatoire parmi `SpawnPointsArray`.
     * OU sélection d’un **SpawnZoneVolume** aléatoire.
3. **Récupération de la position :**
   * Récupération du vecteur position du point sélectionné.
4. **Transformation :**
   * Conversion du vecteur en **Transform** pour l’utiliser lors du spawn.
5. **Spawn du PNJ :**
   * Utilisation de **SpawnActorFromClass** pour instancier un **`BP_PNJ`** en passant :
     * Le struct `PNJData` correspondant.
     * Le Transform calculé.
6. **Stockage du PNJ :**
   * Le PNJ spawné est ajouté à **`SpawnedPNJArray`**.
7. **Debug Log (optionnel) :**
   * Affichage du nom du PNJ spawné via un **Print String**.

***

#### **Flow visuel simplifié :**

```
[PNJDataArray]
 └──> ForEach → Sélection SpawnPoint/Zone (aléatoire)
                 └──> Get Location → VectorToTransform
                        └──> SpawnActorFromClass (BP_PNJ)
                               └──> Ajout à SpawnedPNJArray
                                     └──> Print Log PNJ Nom (debug)
```

***

#### **Comportement spécifique :**

* **Randomisation :**
  * Un **RandomIntegerInRange** est utilisé pour choisir aléatoirement un point ou volume parmi les arrays.
* **Sécurité :**
  * La sélection aléatoire tient compte de la longueur des arrays pour éviter les erreurs d'index.
* **Données passées au PNJ :**
  * Le PNJ reçoit directement les données du `Struct_PNJData` (Nom, Profession, Relations, etc.).

***

#### **Exemple d'utilisation typique :**

* Lors du **début de partie** ou d’un événement spécifique, appeler `SpawnAllPNJs` permet de peupler la scène avec des PNJs variés disposés aux bons endroits.

***

#### **Améliorations possibles suggérées :**

1. **Ajout d’un paramètre pour filtrer par profession/clan avant le spawn.**
2. **Ajout d’un flag pour désactiver l’affichage debug.**
3. **Gestion d’un fallback si les arrays de spawn sont vides (éviter soft crash).**
