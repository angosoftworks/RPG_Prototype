---
description: Volumes définissant les zones valides pour le spawn dynamique.
icon: table-cells
---

# SpawnZoneVolume

### Description générale

`SpawnZoneVolume` est une variable de type **Array (tableau)**, contenant des références d’acteurs de type **Acteur**.\
Elle est utilisée pour stocker une liste de volumes définissant des zones spécifiques où les entités (PNJs, objets, ennemis, etc.) peuvent apparaître dynamiquement.

### Détails techniques

* **Nom de la variable :** `SpawnZoneVolume`
* **Type :** `Array` de références vers des **Acteurs**
* **Catégorie :** Par défaut (aucune catégorisation spécifique)
* **Instance modifiable :** **Oui** (modifiable depuis l’inspecteur Unreal)
* **Blueprint en lecture seule :** Non
* **Exposer à l’apparition :** **Oui** (modifiable à la création de l’acteur dans le niveau)
* **Privé :** Non (accessible par d’autres Blueprints)
* **Réplicable :** Non
* **Condition de réplication :** Aucune

### Comportement

La variable est **modifiable directement dans l’éditeur**, permettant aux level designers ou aux développeurs d’attribuer facilement les volumes de spawn à chaque instance d’acteur qui utilise ce tableau.

Elle est également **exposée à l’apparition**, donc chaque instance placée dans le niveau peut avoir ses propres volumes assignés sans ouvrir le Blueprint source.

Cette variable **n’est pas répliquée**, ce qui signifie qu’elle n’est pas synchronisée automatiquement sur un réseau multijoueur. Elle fonctionne en local uniquement.

### Valeur par défaut

* Initialisée avec **0 élément(s)** (vide par défaut).
* Les volumes doivent être assignés manuellement via l'éditeur ou dynamiquement en runtime.

### Utilisation prévue

`SpawnZoneVolume` est utilisée pour :

* Définir des **zones physiques spécifiques** où les acteurs peuvent apparaître.
* Offrir une gestion flexible des zones de spawn pour chaque instance d’un spawner ou d’un manager.
* Permettre la randomisation ou la gestion conditionnelle de spawn dans différents volumes.

Exemples d’acteurs pouvant être référencés :

* Trigger Volumes
* Custom Spawn Volumes
* Box Volumes délimitant une zone

### Bonnes pratiques

1. Vérifier que chaque volume référencé est valide avant d’effectuer une opération de spawn.
2. Ajouter des **tags** ou noms descriptifs aux volumes pour faciliter la compréhension (ex: `SpawnZone_Forest`, `SpawnZone_City`).
3. Si plusieurs volumes se recouvrent, prévoir une logique pour éviter le double-spawn.
4. Nettoyer ou actualiser la liste si des volumes sont déplacés ou supprimés dans le niveau.

### Suggestions d'améliorations

* **Catégorie personnalisée :** Recommandé de les regrouper sous un dossier spécifique, ex : `Level | Spawn Zones` pour plus de lisibilité dans l'inspecteur.
* **Description Unreal :** Ajouter une description claire pour guider les level designers, ex : _"Volumes définissant les zones valides pour le spawn dynamique."_
* **Blueprint lecture seule :** Activer si la variable ne doit être modifiée qu’à l’édition et jamais au runtime.

### Exemple d'utilisation

* Au lancement du jeu ou d’un événement spécifique :
  * Boucler sur le tableau `SpawnZoneVolume`.
  * Sélectionner un volume aléatoirement ou selon condition.
  * Utiliser les dimensions ou le bounds du volume pour calculer la position du spawn.
* Possibilité de lier cela avec un système d’évitement d’obstacles pour s’assurer qu’un acteur spawné n’apparaisse pas dans des zones bloquées.
