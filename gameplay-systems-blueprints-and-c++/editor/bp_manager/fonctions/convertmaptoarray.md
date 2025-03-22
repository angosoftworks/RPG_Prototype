---
description: >-
  Convertit une Map de relations en tableau structuré pour un traitement plus
  flexible.
icon: function
---

# ConvertMapToArray

#### **Description générale :**

`ConvertMapToArray` est une fonction interne du Blueprint `BP_Manager`.\
Elle est conçue pour convertir une Map (dictionnaire) de paires **String → Int** en un tableau d’éléments de structure personnalisée `Struct_RelationEntry`.\
Cette conversion facilite le traitement des données relationnelles dans les systèmes qui attendent des tableaux plutôt que des Maps.

***

#### **Détails techniques :**

| Propriété              | Détail                                         |
| ---------------------- | ---------------------------------------------- |
| **Nom de la fonction** | `ConvertMapToArray`                            |
| **Type de fonction**   | Function Blueprint (`K2Node_FunctionEntry`)    |
| **Accessibilité**      | Editable (modifiable dans le Blueprint)        |
| **Catégorie**          | Par défaut                                     |
| **Entrées**            | `InputMap` (Map : **String → Int**)            |
| **Sortie**             | `OutputArray` (Array : `Struct_RelationEntry`) |
| **Variables locales**  | `TempArray` (Array de `Struct_RelationEntry`)  |

***

#### **Fonctionnement :**

**Étapes internes :**

1. **Extraction des clés de la Map :**\
   Utilisation de `Map_Keys` pour récupérer toutes les clés du `InputMap`.
2. **Boucle ForEach sur les clés :**\
   Pour chaque clé du dictionnaire :
   * **Récupération de la valeur associée :**\
     Avec `Map_Find` pour obtenir l’entier lié à la clé.
   * **Création d’une entrée de relation :**\
     Utilisation du `MakeStruct RelationEntry` pour remplir :
     * `RelationName` = clé (String)
     * `RelationScore` = valeur (Int)
   * **Ajout au tableau temporaire :**\
     Utilisation de `Array_Add` pour ajouter la nouvelle entrée à `TempArray`.
3. **Sortie du tableau rempli :**\
   La variable locale `TempArray` est renvoyée en sortie via `OutputArray`.

***

#### **Flow visuel simplifié :**

```
[InputMap (Map)] 
   └──> Map_Keys
        └──> ForEach Key
              └──> Map_Find (key)
                    └──> Make Struct RelationEntry
                          └──> Array_Add to TempArray
                               └──> OutputArray
```

***

#### **Utilisation prévue :**

* Conversion d'une Map (String → Int) en Array structuré.
* Utile pour systèmes nécessitant un tableau (par exemple : UI, sauvegarde, tri).
* Compatible avec la structure `Struct_RelationEntry` qui contient :
  * **RelationName** (String)
  * **RelationScore** (Int)

***

#### **Bonnes pratiques recommandées :**

1. **Validation :**
   * Vérifier que la Map d’entrée n’est pas vide avant traitement, si nécessaire.
   * Ajouter éventuellement un log si aucune clé n’est trouvée.
2. **Clarté du Blueprint :**
   *   Ajouter un commentaire directement dans Unreal :

       > _"Convertit une Map de relations en tableau structuré pour un traitement plus flexible."_
3. **Optimisation possible :**
   * Si appelé fréquemment, envisager un système de cache ou vérifier si une conversion a déjà été faite pour éviter les recalculs inutiles.

***

#### **Suggestions d’améliorations possibles :**

* Ajouter une sortie booléenne **Success** pour indiquer si la conversion a réussi.
* Supporter d'autres types de Maps (ex : possibilité de passer une Map avec d'autres types de valeurs via surcharge ou fonction générique).
* Ajouter une option pour trier le tableau en sortie (par score ou nom par exemple).

***

#### **Exemple d'utilisation dans le Blueprint :**

```
[InputMap]
   └──> [ConvertMapToArray]
           └──> [OutputArray]
```
