---
description: Liste des points de spawn utilisables par ce système.
icon: table-cells
---

# SpawnPointsArray

### Description générale

`SpawnPointsArray` est une variable de type **Array (tableau)**, contenant des références d’acteurs de type **Acteur**.\
Elle sert à stocker une liste de points de spawn présents dans le niveau, utilisés pour placer dynamiquement d'autres acteurs (ex: PNJs, objets, ennemis).

### Détails techniques

* **Nom de la variable :** `SpawnPointsArray`
* **Type :** `Array` de références vers des **Acteurs**
* **Catégorie :** Par défaut (non catégorisée)
* **Instance modifiable :** **Oui** (modifiable depuis l'inspecteur)
* **Blueprint en lecture seule :** Non
* **Exposer à l’apparition :** **Oui** (visible et modifiable à l'instanciation dans l'éditeur)
* **Privé :** Non (accessible par d'autres Blueprints)
* **Réplicable :** Non
* **Condition de réplication :** Aucune

### Comportement

Cette variable est conçue pour être remplie manuellement dans l'éditeur Unreal.\
Chaque entrée correspond à un acteur placé dans la scène servant de point de spawn.

Grâce à l'option **Instance modifiable** activée, il est possible de renseigner les références de ces spawn points directement sur chaque instance de l’acteur contenant la variable.

Elle est également **exposée à l’apparition**, ce qui signifie qu'à chaque fois que l’acteur est placé dans le niveau, le level designer peut personnaliser les spawn points utilisés sans ouvrir le Blueprint.

### Valeur par défaut

* Initialisé à **0 élément(s)**.
* Les références doivent être assignées manuellement dans l’éditeur sur chaque instance, ou par script.

### Utilisation prévue

`SpawnPointsArray` est typiquement utilisé pour :

* Stocker les emplacements possibles où des acteurs peuvent apparaître (PNJs, objets interactifs, ennemis, etc.).
* Offrir aux level designers la possibilité de contrôler les emplacements de spawn par instance sans toucher au Blueprint.
* Permettre une logique de sélection aléatoire ou conditionnelle d’un point de spawn parmi ceux listés.

### Bonnes pratiques

1. **Toujours valider la référence avant d'utiliser chaque point** (éviter les références nulles).
2. Si nécessaire, trier ou taguer les points de spawn pour les classifier (ex: SpawnPoint\_North, SpawnPoint\_Boss).
3. Nettoyer ou actualiser la liste en cas de changements majeurs dans la scène (par exemple via un outil d’édition).
4. Si un système dynamique est prévu (ex: génération procédurale), envisager une alternative où les spawn points sont détectés automatiquement.

### Suggestions d'améliorations

* **Catégorie personnalisée :** Recommander d’ajouter une catégorie du type `Level | Spawn` pour mieux organiser dans l’inspecteur.
* **Description dans Unreal :** Ajouter une explication, ex : _"Liste des points de spawn utilisables par ce système."_
* **Option Lecture seule :** Si les points doivent uniquement être assignés dans l'éditeur et jamais modifiés en runtime, tu pourrais activer l'option "Blueprint en lecture seule".

### Exemple d'utilisation

* Lors du **BeginPlay** ou d’un appel d’événement :
  * Parcours de `SpawnPointsArray`.
  * Sélection d’un ou plusieurs points pour spawn un acteur.
* Possibilité d’implémenter des systèmes comme :
  * Spawn aléatoire parmi les points disponibles.
  * Spawn conditionnel (par type de PNJ ou zone).
  * Gestion d’occupation (éviter de respawn sur un point déjà utilisé).
