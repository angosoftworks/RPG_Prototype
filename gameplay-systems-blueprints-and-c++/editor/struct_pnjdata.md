# Struct\_PNJData

#### 📝 **Description générale**

`Struct_PNJData` est une structure utilisée pour stocker les informations essentielles d’un PNJ dans le jeu.\
Elle centralise les données relatives à l'identité, la profession, le clan, les traits et les relations du PNJ.\
Elle permet une gestion facile, que ce soit pour le chargement depuis des DataTables, la sauvegarde ou l'interaction avec les systèmes IA et UI.

***

#### ⚙️ **Détails techniques**

| **Nom de la structure**       | `Struct_PNJData`                                         |
| ----------------------------- | -------------------------------------------------------- |
| **Type**                      | Structure Blueprint                                      |
| **Utilisation**               | Référencée dans BP\_Manager, BP\_PNJ, AIController, etc. |
| **Sauvegarde possible**       | Oui (certaines variables cochées "Enregistrer le jeu")   |
| **Modifiable dans l’éditeur** | Oui (certaines variables modifiables exposées)           |

***

#### 🔑 **Contenu de la structure**

| **Nom du champ** | **Type**                | **Modifiable** | **Enregistrer le jeu** | **Description**                                                          |
| ---------------- | ----------------------- | -------------- | ---------------------- | ------------------------------------------------------------------------ |
| `Name`           | Chaîne                  | ✅              | ❌                      | Nom du PNJ (affiché dans UI, dialogues...)                               |
| `Profession`     | Chaîne                  | ✅              | ❌                      | Profession actuelle du PNJ                                               |
| `Clan`           | Chaîne                  | ✅              | ❌                      | Appartenance clanique/familiale                                          |
| `Traits`         | Struct PNJTraits        | ✅              | ❌                      | Ensemble des traits du PNJ (personnalité, compétences…)                  |
| `Relations`      | Carte (Chaîne → Entier) | ✅              | ❌                      | Relations du PNJ avec d'autres entités (nom du PNJ → niveau relationnel) |

***

#### 🗂️ **Détail des champs spécifiques**

**1. Name**

* Type : Chaîne
* Sert à identifier le PNJ.
* Modifiable dans l’éditeur.

**2. Profession**

* Type : Chaîne
* Définit le rôle ou la fonction du PNJ dans le village.

**3. Clan**

* Type : Chaîne
* Utilisé pour indiquer le clan ou la lignée du PNJ (utile pour systèmes de relations, quêtes, événements).

**4. Traits**

* Type : `Struct_PNJTraits`
* Sous-structure regroupant les caractéristiques propres du PNJ.
* Peut contenir par ex. : valeurs de courage, loyauté, compétences spécifiques (dépend de ton Struct\_PNJTraits).

**5. Relations**

* Type : Map (Chaîne → Nombre entier)
* Stocke les relations avec d'autres PNJs ou factions.
* La clé correspond au nom/ID d'une autre entité, la valeur est un score représentant l’état de la relation (amitié, rivalité…).

***

#### 🚀 **Utilisation prévue**

* Chargement des données PNJ depuis **DataTables** ou sauvegardes.
* Base de données locale pour chaque PNJ (référencée dans BP\_PNJ, AIController, etc.).
* Accès rapide aux infos dans les systèmes IA, UI, dialogues, quêtes…

***

#### ✅ **Bonnes pratiques recommandées**

1. **Cohérence des noms :**\
   Utiliser des noms normalisés pour les clans, professions, et PNJ afin de garder un système relationnel robuste.
2. **Sauvegarde :**\
   Cocher les champs critiques si besoin d’une persistance à travers les sessions (par ex. Relations si elles évoluent beaucoup).
3. **Évolutivité :**\
   Si besoin d’ajouter des éléments (ex : âge, préférences, historique), privilégier l’ajout dans des sous-structures comme `Traits` ou un éventuel `History`.

***

#### 🌟 **Suggestions d’amélioration possible**

* Ajouter un champ **UniqueID** (type GUID ou int) si plusieurs PNJs peuvent avoir le même nom, profession, ou clan.
* Ajouter un champ **Age** ou **Gender** si ces informations sont nécessaires pour gameplay ou IA.
* Prévoir une compatibilité multilingue en cas de localisation (par exemple, profession traduite via DataTable multilingue).

***

### 🏷️ **Résumé rapide**

| **Responsabilité principale** | Stocker toutes les informations clés d’un PNJ                |
| ----------------------------- | ------------------------------------------------------------ |
| **Champs clés**               | Name, Profession, Clan, Traits, Relations                    |
| **Utilisé par**               | BP\_Manager, BP\_PNJ, AIController                           |
| **Évolutions possibles**      | Ajout ID unique, localisation, nouveaux traits ou historique |
