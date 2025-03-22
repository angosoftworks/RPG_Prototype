---
description: Initialise les données du village, en chargeant les informations des PNJs.
icon: function
---

# InitializeVillageData

### Description générale :

`InitializeVillageData` est une fonction interne du Blueprint **BP\_Manager**.\
Elle est chargée de **préparer et initialiser les données relatives au village**, notamment en s’assurant que les informations des PNJs sont correctement chargées au lancement du jeu ou à la réinitialisation.

***

### Détails techniques :

* **Nom de la fonction :** `InitializeVillageData`
* **Type de fonction :** Function Blueprint (K2Node\_FunctionEntry)
* **Accessibilité :** Editable (modifiable dans le Blueprint)
* **Catégorie :** Par défaut
* **Entrées :** Aucun input personnalisé
* **Sortie :** Exécution (`Exec`)

***

### Fonctionnement :

La fonction contient actuellement l’appel suivant :

#### **Appel interne :**

* **LoadPNJData()**
  * Cette fonction est appelée dès l’exécution de `InitializeVillageData`.
  * Son rôle est de **charger les données des PNJs** depuis les sources définies (DataTables, fichiers de sauvegarde, variables).

***

### Logique :

1. **Déclenchement :**
   * Lorsque `InitializeVillageData` est appelé, il exécute immédiatement la fonction `LoadPNJData`.
2. **Objectif principal :**
   * Préparer la liste et les informations des PNJs du village avant que d'autres systèmes du jeu ne les utilisent.
   * S'assurer que toutes les données PNJ sont disponibles pour le spawning, le comportement, ou l’affichage des informations.

***

### Flow visuel simplifié :

```
[InitializeVillageData] ---> [LoadPNJData]
```

***

### Utilisation prévue :

`InitializeVillageData` est typiquement appelée :

* Lors du **BeginPlay** du jeu ou du niveau.
* Après un reset ou une réinitialisation du village.
* Avant tout système nécessitant des informations à jour sur les PNJs du village.

***

### Bonnes pratiques recommandées :

1. **Ajout de validation** : Il peut être pertinent d’ajouter à terme une vérification pour s’assurer que les données sont bien chargées après l’appel de `LoadPNJData` (ex: check si `PNJDataArray` n’est pas vide).
2. **Séparation claire des responsabilités** : Cette fonction doit rester focalisée sur l’initialisation et déléguer le traitement spécifique (chargement, parsing, affectation) aux fonctions comme `LoadPNJData`.
3. **Documentation dans Unreal** : Ajouter un commentaire directement dans la fonction pour décrire rapidement son rôle (par ex. _"Initialise les données du village, en chargeant les informations des PNJs"_).

***

### Suggestions d’amélioration possible :

* Ajouter une sortie booléenne (`Success`) si le système doit vérifier si l'initialisation s’est bien déroulée.
* Permettre une flexibilité supplémentaire en ajoutant des paramètres d’entrée (par ex. un booléen pour forcer un reload, ou sélectionner une source spécifique des données).
* Si le projet est en multijoueur, prévoir une condition pour ne lancer cette fonction que sur le serveur.
