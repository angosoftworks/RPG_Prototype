---
description: Liste des PNJs actuellement spawnés et gérés par le système.
icon: table-cells
---

# SpawnedPNJArray

### Description générale

`SpawnedPNJArray` est une variable de type **Array (tableau)**, contenant des références d’acteurs du type **BP\_PNJ** (Blueprint des PNJs présents dans le jeu).

Elle est utilisée pour conserver et accéder à la liste des instances de PNJs actuellement spawnées en jeu.

### Détails techniques

* **Nom de la variable :** `SpawnedPNJArray`
* **Type :** `Array` de références vers le Blueprint `BP_PNJ`
* **Catégorie :** Par défaut (pas de catégorisation définie)
* **Instance modifiable :** Non
* **Blueprint en lecture seule :** Non
* **Exposer à l’apparition :** Non
* **Privé :** Non (accessible aux autres Blueprints)
* **Réplicable :** Non
* **Condition de réplication :** Aucune

### Comportement

Cette variable conserve **les instances des PNJs actuellement présents dans le monde**.

Elle n'est ni exposée, ni modifiable directement depuis l'éditeur, ce qui signifie que sa gestion est entièrement dynamique, au runtime, par le Blueprint qui la contrôle (probablement ton Manager ou un Spawner).

La variable **n'est pas répliquée**, donc uniquement locale au client ou serveur où elle est instanciée.

### Valeur par défaut

* **0 élément(s)** initialement (tableau vide).
* Les références des PNJs sont ajoutées dynamiquement lorsqu’ils sont spawnés via le système de spawn.

### Utilisation prévue

Le tableau `SpawnedPNJArray` est conçu pour :

* Garder une trace de tous les PNJs actuellement spawnés.
* Pouvoir accéder facilement à leurs références pour :
  * Mettre à jour leur état.
  * Les supprimer/despawn proprement.
  * Gérer leurs interactions globales (ex : IA, dialogue, combat).
  * Appliquer des comportements massifs (pause, disparition, effet global).

### Bonnes pratiques

1. Vérifier la validité de chaque référence avant toute opération.
2. Nettoyer le tableau en cas de destruction d’un PNJ pour éviter les références nulles.
3. Utiliser des boucles sur le tableau avec précaution, surtout si les PNJs peuvent être détruits pendant l’itération.
4. Si en multijoueur, penser à la logique de réplication éventuelle (à implémenter si les PNJs doivent être synchronisés).

### Suggestions d'améliorations

* **Catégorie personnalisée :** Regrouper sous un dossier `Gameplay | PNJ` ou `Runtime | PNJ Management` pour plus de lisibilité dans l’inspecteur.
* **Description dans Unreal :** Ajouter une courte explication, ex : _"Liste des PNJs actuellement spawnés et gérés par le système"_.
* **Blueprint en lecture seule :** Peut être activé si aucun autre Blueprint ne doit modifier la liste directement, uniquement lire.
* **Réplication :** Si les PNJs doivent exister sur tous les clients (cas multijoueur), envisage une réplication conditionnelle contrôlée.

### Exemple d'utilisation

* À chaque spawn d’un PNJ :
  * Ajouter sa référence à `SpawnedPNJArray`.
* Lors de la destruction d’un PNJ :
  * Retirer la référence du tableau.
* Lors d’une action globale (ex : “freeze all PNJs”) :
  * Boucler sur `SpawnedPNJArray` pour envoyer l’instruction à chaque PNJ actif.
