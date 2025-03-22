---
icon: function
---

# FormatRelationsArray

#### **Description générale :**

`FormatRelationsArray` est une fonction du Blueprint `BP_Manager` permettant de **convertir un tableau de relations PNJ** (de type struct `Struct_RelationEntry`) en une chaîne de caractères formatée, lisible et exploitable pour l’affichage, le debug ou le stockage.

***

#### **Détails techniques :**

| Propriété              | Détail                                             |
| ---------------------- | -------------------------------------------------- |
| **Nom de la fonction** | `FormatRelationsArray`                             |
| **Type de fonction**   | Function Blueprint (`K2Node_FunctionEntry`)        |
| **Accessibilité**      | Public                                             |
| **Entrées**            | `RelationsArray` (Array of `Struct_RelationEntry`) |
| **Sorties**            | `FormattedRelationsString` (String)                |

***

#### **Détails du `Struct_RelationEntry` :**

Chaque élément du tableau `RelationsArray` est une structure contenant :

* **RelationName** : Nom de la relation (String)
* **RelationScore** : Score/valeur de la relation (Integer)

***

#### **Fonctionnement :**

**Étapes internes :**

1. **Loop sur `RelationsArray` :**
   * Utilisation d’un **For Each Loop** sur chaque élément du tableau.
2. **Formatage individuel :**
   * Pour chaque relation, le nom et le score sont extraits.
   * Un format texte est appliqué, par exemple :\
     `"NomRelation : ScoreRelation"`
3. **Concaténation :**
   * Toutes les relations formatées sont concaténées en une seule chaîne.
   * Possibilité d'ajouter des séparateurs comme des retours à la ligne () ou des virgules.
4. **Résultat :**
   * La chaîne finale est assignée à **FormattedRelationsString**.

***

#### **Flow visuel simplifié :**

```
[RelationsArray (Array)]
   └──> For Each → FormatText (Nom : Score)
          └──> Append to String
               └──> Output → FormattedRelationsString
```

***

#### **Exemple d’entrée et sortie :**

**Entrée :**

```json
[
  { "RelationName": "Alice", "RelationScore": 50 },
  { "RelationName": "Bob", "RelationScore": 30 }
]
```

**Sortie :**

```
"Alice : 50\nBob : 30"
```

***

#### **Utilisation typique :**

Utilisée en conjonction avec la fonction **FormatPNJData** :

* Permet d’afficher ou stocker proprement les relations d’un PNJ après leur conversion depuis un `Map` grâce à la fonction `ConvertMapToArray`.
* Idéale pour **debug logs**, **UI affichage détaillé**, **exports texte**.

***

#### **Bonnes pratiques recommandées :**

1. **Séparateur personnalisable :**
   * Ajouter un paramètre facultatif pour changer le séparateur (, `,`, `;`).
2. **Gestion des cas vides :**
   * Retourner un message par défaut si aucune relation n’existe (ex. `"Aucune relation"`).
3. **Prévoir l’internationalisation :**
   * Utiliser des `Text` plutôt que des `String` si tu veux une version localisable.
