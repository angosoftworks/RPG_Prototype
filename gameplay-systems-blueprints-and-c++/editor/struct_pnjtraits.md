# Struct\_PNJTraits

#### 📝 **Description générale**

`Struct_PNJTraits` est une sous-structure utilisée dans **Struct\_PNJData**.\
Elle regroupe les **traits de personnalité** et caractéristiques comportementales du PNJ.\
Ces valeurs peuvent influencer le comportement du PNJ en jeu, ses interactions, et les décisions prises par l’IA (via le AIController et les Behavior Trees).

***

#### ⚙️ **Détails techniques**

| **Nom de la structure**       | `Struct_PNJTraits`                  |
| ----------------------------- | ----------------------------------- |
| **Type**                      | Structure Blueprint                 |
| **Utilisation**               | Incluse dans `Struct_PNJData`       |
| **Modifiable dans l'éditeur** | Oui (toutes les variables exposées) |
| **Sauvegarde possible**       | Oui (certaines variables cochées)   |

***

#### 🔑 **Contenu de la structure**

| **Nom du champ** | **Type**      | **Modifiable** | **Enregistrer le jeu** | **Description**                                                  |
| ---------------- | ------------- | -------------- | ---------------------- | ---------------------------------------------------------------- |
| `Ambition`       | Nombre entier | ✅              | ❌                      | Niveau d’ambition du PNJ, pouvant influencer objectifs et quêtes |
| `Loyauté`        | Nombre entier | ✅              | ❌                      | Fidélité du PNJ envers le village, le clan, ou d’autres PNJs     |
| `Sociabilité`    | Nombre entier | ✅              | ❌                      | Tendance du PNJ à interagir avec d’autres personnages            |

***

#### 🗂️ **Détail des champs spécifiques**

**1. Ambition**

* Type : Nombre entier
* Peut impacter la propension du PNJ à chercher des promotions, prendre des initiatives, ou déclencher certains comportements IA.

**2. Loyauté**

* Type : Nombre entier
* Détermine à quel point le PNJ est fidèle au village, son clan, ou un groupe donné.
* Peut conditionner des réactions en cas de trahison, guerre, ou choix critiques.

**3. Sociabilité**

* Type : Nombre entier
* Influence la fréquence ou la qualité des interactions avec d’autres PNJs ou le joueur.
* Peut moduler les dialogues, quêtes sociales, ou événements de groupe.

***

#### 🚀 **Utilisation prévue**

* Affecte les comportements IA contrôlés par **BP\_PNJ\_AIController**.
* Utilisé pour personnaliser chaque PNJ via la DataTable ou lors de l'initialisation dans **BP\_Manager**.
* Peut être référencé dans UI (affichage du profil PNJ), ou dans des systèmes d'événements/décisions.

***

#### ✅ **Bonnes pratiques recommandées**

1. **Valeurs normalisées :**\
   Définir une plage de valeurs cohérente (par ex. 0 à 100) pour faciliter les comparaisons et équilibrages.
2. **Réutilisation :**\
   Si de nouveaux traits sont nécessaires (ex : Courage, Intelligence), les ajouter ici pour centraliser.
3. **Impact sur IA & Gameplay :**\
   S'assurer que ces valeurs sont bien exploitées dans les Behavior Trees ou autres systèmes décisionnels.

***

#### 🌟 **Suggestions d’amélioration possible**

* Ajouter des **bornes minimales/maximales** (exposées ou fixées) pour contrôler l’équilibrage.
* Ajouter un système de **progression** (les traits évoluent avec le temps ou via des événements).
* Prendre en compte une **influence sociale** : par exemple, un PNJ très sociable peut augmenter la sociabilité des PNJs voisins via un système d'interactions récurrentes.

***

### 🏷️ **Résumé rapide**

| **Responsabilité principale** | Définir les traits comportementaux du PNJ            |
| ----------------------------- | ---------------------------------------------------- |
| **Champs clés**               | Ambition, Loyauté, Sociabilité                       |
| **Utilisé par**               | Struct\_PNJData, BP\_PNJ\_AIController               |
| **Évolutions possibles**      | Nouveaux traits, bornes de valeurs, système évolutif |
