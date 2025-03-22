---
description: >-
  Charge les données des PNJs depuis la DataTable et remplit le tableau interne
  des PNJs.
icon: function
---

# LoadPNJData

#### **Description générale :**

`LoadPNJData` est une fonction interne du Blueprint `BP_Manager`.\
Elle est responsable du chargement des données des PNJs du village à partir d’une DataTable, et du stockage de ces données dans un tableau accessible au reste du projet. Cette fonction est appelée par `InitializeVillageData` pour assurer que les informations des PNJs sont disponibles dès le début du jeu ou après réinitialisation.

***

#### **Détails techniques :**

| Propriété              | Détail                                      |
| ---------------------- | ------------------------------------------- |
| **Nom de la fonction** | `LoadPNJData`                               |
| **Type de fonction**   | Function Blueprint (`K2Node_FunctionEntry`) |
| **Accessibilité**      | Editable (modifiable dans le Blueprint)     |
| **Catégorie**          | Par défaut                                  |
| **Entrées**            | Aucun input personnalisé                    |
| **Sortie**             | Exécution (`Exec`)                          |

***

#### **Fonctionnement :**

**Étapes internes :**

1. **Récupération des noms de lignes de la DataTable :**\
   Utilisation de la fonction `GetDataTableRowNames` pour obtenir tous les noms des lignes de la DataTable `DT_PNJData`.
2. **Boucle ForEach sur chaque ligne :**\
   Parcours de chaque nom de ligne avec un `ForEachLoop`.
3. **Récupération des données de chaque PNJ :**\
   Utilisation de `GetDataTableRow` pour extraire les données de chaque PNJ.
4. **Traitement des données :**\
   Chaque ligne récupérée est passée à la fonction interne `FormatPNJData` qui formate les informations du PNJ (nom, métier, clan, traits, relations).
5. **Affichage Debug :**\
   Les informations formatées sont affichées dans le log et à l'écran via `PrintString` pour faciliter le debug.
6. **Stockage :**\
   Les données du PNJ sont ajoutées au tableau interne `PNJDataArray`.

***

#### **Flow visuel simplifié :**

```
[LoadPNJData]
    └──> GetDataTableRowNames (DT_PNJData)
        └──> ForEach RowName
            └──> GetDataTableRow
                └──> FormatPNJData
                    └──> PrintString (Debug)
                        └──> Add to PNJDataArray
```

***

#### **Utilisation prévue :**

* Appelée exclusivement par `InitializeVillageData`.
* Chargée au lancement du jeu ou après un reset du village.
* Permet aux systèmes de spawning, AI, UI ou sauvegarde d'accéder aux données PNJ correctement structurées.

***

#### **Bonnes pratiques recommandées :**

1. **Validation :**\
   Vérifier la validité de chaque ligne récupérée (`Row Found` vs `Row Not Found`).
2. **Centralisation des sources de données :**\
   Pour plus de flexibilité, prévoir la possibilité d'utiliser différentes DataTables ou sources (à terme, avec un input optionnel par exemple).
3.  **Documentation Unreal :**\
    Ajouter un commentaire dans la fonction :

    > _"Charge les données des PNJs depuis la DataTable et remplit le tableau interne des PNJs."_
4. **Multijoueur :**\
   Si utilisé en multijoueur, exécuter uniquement côté serveur (similaire à `InitializeVillageData`).

***

#### **Suggestions d’améliorations possibles :**

* Ajouter un **output booléen (Success)** pour indiquer si le chargement des données s'est bien déroulé.
* Gérer les éventuelles erreurs : par ex., afficher un warning/log si une ligne n’est pas trouvée.
* Intégrer une option **Force Reload** pour rafraîchir les données à la volée en jeu.
* Si le système devient plus complexe, externaliser le traitement (actuellement dans `FormatPNJData`) pour supporter différentes structures de données.

***

#### **Exemple d'utilisation dans le Blueprint :**

```
[InitializeVillageData]
    └──> [LoadPNJData]
```
