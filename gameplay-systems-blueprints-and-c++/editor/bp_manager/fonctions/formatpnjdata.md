---
description: >-
  Formate les données d’un PNJ pour affichage : Nom, Profession, Clan, Traits et
  Relations.
icon: function
---

# FormatPNJData

#### **Description générale :**

`FormatPNJData` est une fonction interne du Blueprint `BP_Manager`.\
Elle est responsable de recevoir une structure **PNJData** représentant les données d’un PNJ (nom, profession, clan, traits, relations) et de formater ces informations sous forme de chaînes de caractères prêtes à être affichées, par exemple dans une UI ou un log.

***

#### **Détails techniques :**

| Propriété              | Détail                                      |
| ---------------------- | ------------------------------------------- |
| **Nom de la fonction** | `FormatPNJData`                             |
| **Type de fonction**   | Function Blueprint (`K2Node_FunctionEntry`) |
| **Accessibilité**      | Editable (modifiable dans le Blueprint)     |
| **Entrée**             | `PNJDataInput` (Struct : `Struct_PNJData`)  |
| **Sorties**            | `FormattedName` (String)                    |
|                        | `FormattedProfession` (String)              |
|                        | `FormattedClan` (String)                    |
|                        | `FormattedTraits` (String)                  |
|                        | `FormattedRelations` (String)               |

***

#### **Fonctionnement :**

**Étapes internes :**

1. **Décomposition du PNJData :**\
   Utilisation de `Break Struct` sur la structure `Struct_PNJData` pour accéder aux éléments suivants :
   * Name (String)
   * Profession (String)
   * Clan (String)
   * Traits (Struct\_PNJTraits)
   * Relations (Map String → Int)
2. **Formatage des Relations :**
   * Appel à la fonction **`ConvertMapToArray`** pour convertir la Map des relations en un tableau structuré.
   * Passage du tableau à la fonction **`FormatRelationsArray`** qui retourne une string lisible représentant les relations du PNJ.
3. **Formatage des Traits :**
   * Décomposition du `Struct_PNJTraits` (Ambition, Loyauté, Sociabilité).
   * Utilisation de **`FormatText`** pour formater les valeurs sous forme de string lisible :\
     &#xNAN;_"Ambition = X, Loyauté = Y, Sociabilité = Z"_
   * Conversion du texte en string via **`Conv_TextToString`**.
4. **Assemblage des résultats :**
   * Nom, profession, clan pris directement du `Struct_PNJData`.
   * Traits et relations formatés sont affectés aux sorties.

***

#### **Flow visuel simplifié :**

```
[PNJDataInput (Struct_PNJData)]
   └──> Break Struct
         ├──> Name → FormattedName
         ├──> Profession → FormattedProfession
         ├──> Clan → FormattedClan
         ├──> Traits → Break Struct → FormatText → Conv_TextToString → FormattedTraits
         └──> Relations → ConvertMapToArray → FormatRelationsArray → FormattedRelations
```

***

#### **Utilisation prévue :**

* **Affichage formaté** des données d’un PNJ dans une interface utilisateur, log ou fichier.
* Permet de convertir une structure brute en plusieurs chaînes prêtes à l’emploi.

***

#### **Bonnes pratiques recommandées :**

1.  **Clarté visuelle dans le Blueprint :**\
    Ajouter un commentaire sur le nœud principal :

    > _"Formate les données d’un PNJ pour affichage : Nom, Profession, Clan, Traits et Relations."_
2. **Extensibilité :**
   * Prévoir des options pour personnaliser les séparateurs ou les formats (par exemple via un paramètre optionnel).
   * Faciliter l’ajout d'autres attributs si la structure évolue.
3. **Validation :**
   * Vérifier que les données reçues (nom, profession) ne sont pas nulles ou vides si utilisé dans un contexte sensible (affichage joueur, etc.).

***

#### **Exemple d'utilisation :**

Dans un Widget ou une fonction d’affichage :

```
[PNJDataInput (Struct)]
   └──> [FormatPNJData]
           ├──> FormattedName → Affichage
           ├──> FormattedProfession → Affichage
           ├──> FormattedClan → Affichage
           ├──> FormattedTraits → Affichage
           └──> FormattedRelations → Affichage
```

***

#### **Suggestions d'améliorations possibles :**

* Ajouter une option pour **traduire/adapter dynamiquement** les professions ou clans selon la langue.
* Permettre une personnalisation du texte final pour s'adapter aux styles UI différents.
* Possibilité d’ajouter une sortie **JSON** ou autre format si besoin d’export.
