# Struct\_RelationEntry

#### 📝 **Description générale**

`Struct_RelationEntry` est une structure utilisée pour modéliser une relation individuelle entre un PNJ et une autre entité (autre PNJ, clan, faction, etc.).\
Elle contient le **nom de l’entité liée** ainsi qu’un **score numérique** représentant l’état de la relation.\
Elle est pensée pour être utilisée dans un tableau ou une map afin de suivre et gérer les relations dynamiques des PNJs.

***

#### ⚙️ **Détails techniques**

| **Nom de la structure**       | `Struct_RelationEntry`                                             |
| ----------------------------- | ------------------------------------------------------------------ |
| **Type**                      | Structure Blueprint                                                |
| **Utilisation**               | Contenue dans une Map ou Array des relations dans `Struct_PNJData` |
| **Modifiable dans l'éditeur** | Oui (toutes les variables exposées)                                |
| **Sauvegarde possible**       | Oui (certaines variables cochées)                                  |

***

#### 🔑 **Contenu de la structure**

| **Nom du champ** | **Type**      | **Modifiable** | **Enregistrer le jeu** | **Description**                                          |
| ---------------- | ------------- | -------------- | ---------------------- | -------------------------------------------------------- |
| `RelationName`   | Chaîne        | ✅              | ❌                      | Nom de l’entité concernée par cette relation (PNJ, clan) |
| `RelationScore`  | Nombre entier | ✅              | ❌                      | Valeur représentant la qualité de la relation            |

***

#### 🗂️ **Détail des champs spécifiques**

**1. RelationName**

* Type : Chaîne
* Sert d’identifiant pour l’entité liée (autre PNJ, faction, groupe).
* Peut être utilisé comme clé dans une Map ou pour affichage UI.

**2. RelationScore**

* Type : Nombre entier
* Indique l’état de la relation :
  * Valeur positive → Relation amicale.
  * Valeur neutre/0 → Relation indifférente/neutre.
  * Valeur négative → Relation hostile.
* Peut évoluer dynamiquement en fonction des actions du joueur, événements, quêtes...

***

#### 🚀 **Utilisation prévue**

* Inséré dans une Map ou Array pour stocker plusieurs relations d’un PNJ (dans **Struct\_PNJData**).
* Utilisé par le système d’IA ou les interactions sociales pour déterminer le comportement d’un PNJ envers les autres.

***

#### ✅ **Bonnes pratiques recommandées**

1. **Uniformité des noms :**\
   Standardiser les noms dans `RelationName` pour éviter les doublons ou incohérences (par ex. utiliser un ID unique au lieu du nom affiché).
2. **Bornes sur RelationScore :**\
   Définir une plage de valeurs logique (ex : -100 à 100) pour normaliser les impacts sur gameplay.
3. **Sauvegarde dynamique :**\
   Si les relations évoluent beaucoup pendant la partie, cocher "Enregistrer le jeu" pour assurer leur persistance.

***

#### 🌟 **Suggestions d’amélioration possible**

* Ajouter un **Type de Relation** (ex: amicale, rivalité, commerciale) si les interactions varient selon le contexte.
* Ajouter un **Historique des interactions** (liste des événements marquants ayant impacté la relation).
* Prévoir une **décroissance naturelle du score** avec le temps (si pas d’interactions, la relation se détériore ou revient à neutre).

***

### 🏷️ **Résumé rapide**

| **Responsabilité principale** | Stocker les informations sur une relation individuelle |
| ----------------------------- | ------------------------------------------------------ |
| **Champs clés**               | RelationName, RelationScore                            |
| **Utilisé par**               | Struct\_PNJData (via Map/Array)                        |
| **Évolutions possibles**      | Type de relation, historique, décroissance automatique |
