# DT\_PNJData

#### 📝 **Description générale**

`DataTable_PNJData` est une table de données contenant l’ensemble des informations de base pour chaque PNJ du village.\
Elle est construite à partir de la structure **Struct\_PNJData** et sert de source principale pour initialiser les PNJs lors du lancement du jeu ou à la réinitialisation.

Chaque ligne représente un PNJ unique avec ses caractéristiques propres : identité, profession, clan, traits de personnalité et relations.

***

#### ⚙️ **Détails techniques**

| **Nom de la DataTable**        | `DataTable_PNJData`                                                                    |
| ------------------------------ | -------------------------------------------------------------------------------------- |
| **Structure associée**         | `Struct_PNJData`                                                                       |
| **Utilisation**                | Chargée au lancement via `InitializeVillageData`                                       |
| **Nombre de lignes actuelles** | 10 PNJs (ex : Alrik, Bjorn, Helga...)                                                  |
| **Options d’importation**      | <p>Ignore Extra/Missing Fields : désactivé<br>Preserve Existing Values : désactivé</p> |

***

#### 🔑 **Contenu de la DataTable**

Chaque ligne contient les informations suivantes, héritées de `Struct_PNJData` :

| **Champ**    | **Type**                       | **Exemple (PNJ Alrik)**                     |
| ------------ | ------------------------------ | ------------------------------------------- |
| `Name`       | Chaîne                         | Alrik                                       |
| `Profession` | Chaîne                         | Forgeron                                    |
| `Clan`       | Chaîne                         | Clan Marteau                                |
| `Traits`     | Struct\_PNJTraits              | { Ambition: 6, Loyauté: 8, Sociabilité: 4 } |
| `Relations`  | Liste de Struct\_RelationEntry | { Bjorn: 6, Cedric: -4, Runa: 8 }           |

***

#### 📄 **Exemple de ligne (Alrik)**

| **Champ**  | **Valeur**                              |
| ---------- | --------------------------------------- |
| Name       | Alrik                                   |
| Profession | Forgeron                                |
| Clan       | Clan Marteau                            |
| Traits     | Ambition: 6, Loyauté: 8, Sociabilité: 4 |
| Relations  | Bjorn: 6, Cedric: -4, Runa: 8           |

***

#### 🚀 **Utilisation prévue**

* **Chargement automatique** par le **BP\_Manager** via la fonction `LoadPNJData`, appelée dans `InitializeVillageData`.
* Référence principale pour instancier et configurer les PNJs au **BeginPlay**.
* Source de vérité pour les systèmes IA (via **BP\_PNJ\_AIController**) et les UI (fiches PNJ, relations...).

***

#### ✅ **Bonnes pratiques recommandées**

1. **Cohérence des données :**
   * S’assurer que les noms (Name, RelationName) sont uniques ou gérés via IDs.
   * Garder des valeurs homogènes pour les traits (plages normalisées).
2. **Éviter les doublons :**\
   Vérifier que chaque relation n’a pas de redondance croisée (ex: si Alrik → Bjorn, gérer si Bjorn → Alrik est nécessaire).
3. **Édition facilitée :**\
   Utiliser l’éditeur de ligne Unreal pour modifier facilement traits et relations.

***

#### 🌟 **Suggestions d’amélioration possible**

* **Ajout de nouvelles colonnes** :\
  Ajouter un champ pour un **Unique ID**, âge, statut de santé, ou autres caractéristiques si besoin.
* **Intégration multilingue :**\
  Envisager l’utilisation de **DataTables localisées** pour profession, clan ou autres champs affichés.
* **Système d’import/export :**\
  Définir un fichier source CSV/JSON pour permettre un remplissage ou édition externe (non défini actuellement).

***

### 🏷️ **Résumé rapide**

| **Responsabilité principale** | Stocker les données initiales de chaque PNJ                                           |
| ----------------------------- | ------------------------------------------------------------------------------------- |
| **Basée sur**                 | Struct\_PNJData                                                                       |
| **Utilisé par**               | BP\_Manager, BP\_PNJ, AIController                                                    |
| **Nombre de PNJs actuels**    | 10                                                                                    |
| **Évolutions possibles**      | Ajout de champs (ID unique, âge…), intégration localisation, import/export automatisé |
