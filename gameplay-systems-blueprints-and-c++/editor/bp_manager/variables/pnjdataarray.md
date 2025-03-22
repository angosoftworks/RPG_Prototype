---
icon: table-cells
---

# PNJDataArray

### Description générale

`PNJDataArray` est une variable de type **Array (tableau)**, contenant des éléments du type **Struct PNJData**.\
Elle est utilisée pour stocker des informations relatives aux PNJs (Personnages Non Joueurs) du jeu, regroupées sous forme de structures.

### Détails techniques

* **Nom de la variable :** `PNJDataArray`
* **Type :** `Array` de `Struct PNJData`
* **Catégorie :** Par défaut (aucune catégorisation personnalisée)
* **Instance modifiable :** Non
* **Blueprint en lecture seule :** Non
* **Exposer à l’apparition :** Non
* **Privé :** Non (accessible aux autres Blueprints)
* **Réplicable :** Non (aucune réplication réseau définie)
* **Condition de réplication :** Aucune

### Comportement

Cette variable **n’est pas modifiable dans l’inspecteur (Instance modifiable désactivé)** et **n’est pas exposée** lors de l’instanciation d’acteurs. Elle est principalement gérée par le système lui-même, sans besoin d’intervention externe via l'éditeur.

Aucune réplication réseau n’est configurée sur cette variable, ce qui signifie qu’elle est locale et non synchronisée entre clients et serveur.

### Valeur par défaut

* Initialisée à **0 élément(s)** (vide).
* Les éléments doivent être ajoutés dynamiquement (via Blueprints ou code) durant l'exécution ou dans l'éditeur selon le besoin.

### Utilisation prévue

`PNJDataArray` sert à stocker les données structurées pour plusieurs PNJs. Typiquement, chaque élément contient des informations comme :

* Identifiants du PNJ
* Nom
* Position
* Statistiques spécifiques
* Comportements ou états prédéfinis

Cela permet une gestion centralisée des PNJs dans le manager ou système où cette variable est utilisée.

### Bonnes pratiques

1. Toujours vérifier la validité des données avant l’utilisation.
2. Privilégier les opérations en batch (sur l’ensemble du tableau) plutôt que des appels fréquents par index si performance critique.
3. Ajouter des commentaires dans le Blueprint précisant la nature exacte du `Struct PNJData` pour chaque champ.
4. Si le projet devient multijoueur, envisager d'ajouter une logique de réplication si certains PNJ doivent être synchronisés.

### Suggestions d'améliorations

* **Catégorisation :** Définir une catégorie personnalisée pour mieux organiser les variables dans l’inspecteur, par exemple : `Gameplay | PNJ`.
* **Description :** Ajouter une description dans Unreal pour qu’elle apparaisse au survol de la variable dans l'éditeur (actuellement vide).
* **Blueprint en lecture seule :** Activer cette option si la variable ne doit pas être modifiée dans le gameplay, seulement lue.
