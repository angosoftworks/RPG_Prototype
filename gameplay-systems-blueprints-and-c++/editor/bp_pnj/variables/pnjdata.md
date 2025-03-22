---
description: Volumes définissant les zones valides pour le spawn dynamique.
icon: rectangle-wide
---

# PNJData

### Description générale

**PNJData** est une variable structurée contenue dans le Blueprint **BP\_PNJ**.\
Elle contient l’ensemble des informations propres à chaque PNJ (nom, profession, clan, traits, relations, etc.), encapsulées dans une structure personnalisée **Struct\_PNJData**.

Cette variable est essentielle pour initialiser et configurer le comportement et l’apparence du PNJ à sa création.

***

### Détails techniques

| Propriété                      | Valeur                                                 |
| ------------------------------ | ------------------------------------------------------ |
| **Nom de la variable**         | PNJData                                                |
| **Type de variable**           | Struct PNJData                                         |
| **Type exact**                 | `Struct_PNJData` (structure définie par l’utilisateur) |
| **Instance modifiable**        | **Oui** (modifiable dans les instances)                |
| **Blueprint en lecture seule** | Non                                                    |
| **Exposer à l’apparition**     | **Oui** (visible lors du spawn)                        |
| **Privé**                      | Non                                                    |
| **Catégorie**                  | Par défaut                                             |
| **Répartition (Replication)**  | Aucun                                                  |

***

### Fonctionnalité

La variable **PNJData** contient les données suivantes (d’après la struct associée) :

* **Nom** : Nom du PNJ.
* **Profession** : Métier ou rôle du PNJ.
* **Clan** : Clan ou affiliation.
* **Traits** : Structure contenant les caractéristiques spécifiques du PNJ.
* **Relations** : Dictionnaire (Map) des relations du PNJ avec d’autres entités.

***

### Utilisation prévue

* **Initialisation** : Utilisée par la fonction **InitializePNJ** pour configurer le PNJ après spawn.
* **Éditeur** : Grâce à l’option **Instance modifiable** et **Exposer à l’apparition**, les designers peuvent configurer les données de chaque PNJ directement dans l’inspecteur Unreal lors du placement dans le niveau ou lors du spawn dynamique.
* **Gameplay** : Fournit toutes les informations nécessaires pour le comportement, l’apparence ou les interactions du PNJ.

***

### Bonnes pratiques recommandées

* **Struct proprement documentée** : Ajouter des descriptions à chaque champ de **Struct\_PNJData** pour faciliter l’édition.
* **Validation** : Lors de l’utilisation runtime, ajouter des vérifications pour s’assurer que **PNJData** est correctement initialisé avant d’accéder à ses propriétés.
* **Centralisation** : Utiliser **PNJData** comme source unique d’information sur le PNJ pour éviter les redondances.

***

### Suggestions d’amélioration

* **Support multijoueur** : Si les données des PNJs doivent être synchronisées entre serveur et clients, envisager d’activer la **réplication** pour **PNJData**.
* **Catégorisation** : Définir une catégorie spécifique (ex : "PNJ Configuration") pour mieux organiser les variables dans l’inspecteur Unreal.
* **Description interne** : Ajouter une description dans le champ prévu ("Contient les données de configuration du PNJ (Nom, Profession, Clan, Traits, Relations)").

***

### Exemple de commentaire à insérer dans Unreal :

```
Structure contenant toutes les informations relatives au PNJ : nom, profession, clan, traits et relations.
Modifiable à l’apparition pour personnalisation individuelle.
```
