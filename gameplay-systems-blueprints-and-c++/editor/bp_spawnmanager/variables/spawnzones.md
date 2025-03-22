---
icon: table-cells
---

# SpawnZones

#### Description générale

`SpawnZones` est une variable de type **Array d'objets**, contenant des références aux instances du Blueprint `BP_SpawnZone`. Elle est utilisée pour centraliser et gérer l'ensemble des zones de spawn disponibles dans le jeu, permettant un contrôle précis des emplacements où les entités peuvent apparaître.

***

#### Détails techniques

| Propriété                      | Valeur                                                                         |
| ------------------------------ | ------------------------------------------------------------------------------ |
| **Nom de la variable**         | SpawnZones                                                                     |
| **Type**                       | Array d'objets : `BP_SpawnZone_C` (classe dérivée du Blueprint `BP_SpawnZone`) |
| **Catégorie**                  | Par défaut                                                                     |
| **Instance modifiable**        | Oui (ExposeOnSpawn activé)                                                     |
| **Blueprint en lecture seule** | Non                                                                            |
| **Exposer à l’apparition**     | Oui                                                                            |
| **Privé**                      | Non (accessible aux autres Blueprints)                                         |
| **Réplicable**                 | Non (aucune réplication réseau définie)                                        |
| **Condition de réplication**   | Aucune                                                                         |

***

#### Comportement

* **Modifiabilité** : La variable est exposée à l’apparition, ce qui permet de définir la liste des zones de spawn lors de l’instanciation d’un acteur.
* **Répartition** : Non répliquée — les informations relatives aux zones de spawn sont locales et non synchronisées entre client et serveur.
* **Gestion** : Les zones doivent être assignées soit manuellement dans l’éditeur, soit dynamiquement via des scripts Blueprints ou du code.

***

#### Utilisation prévue

`SpawnZones` sert à référencer les différentes zones où des entités (PNJs, objets, etc.) peuvent apparaître. Typiquement, elle est utilisée dans un système de gestion de spawn pour sélectionner aléatoirement ou méthodiquement une zone disponible parmi celles référencées.

Chaque élément du tableau représente une instance du Blueprint `BP_SpawnZone`, lequel peut contenir des informations supplémentaires telles que :

* Position et dimensions de la zone
* Critères spécifiques d'apparition (types d'entités autorisées, conditions particulières, etc.)
* Comportement particulier lié à l'activation ou désactivation de la zone

***

#### Bonnes pratiques

* **Validation** : Toujours vérifier que chaque référence contenue dans le tableau est valide (non null).
* **Centralisation** : Assurez-vous que la gestion des zones de spawn est faite depuis un système central (ex : un manager), pour éviter les duplications ou incohérences.
* **Exposition sur spawn** : Bien utiliser l’option _ExposeOnSpawn_ uniquement si nécessaire pour la configuration des zones via l’éditeur ou depuis d'autres Blueprints à l'initialisation.
* **Performance** : Si les zones sont nombreuses, envisager des algorithmes optimisés pour choisir la zone la plus pertinente (par exemple en fonction de la distance au joueur).

***

#### Suggestions d’améliorations

| Suggestion                     | Détail                                                                                              |
| ------------------------------ | --------------------------------------------------------------------------------------------------- |
| **Catégorisation**             | Définir une catégorie personnalisée (ex. : \`Gameplay                                               |
| **Description**                | Ajouter une description dans Unreal pour expliquer le rôle de la variable au survol dans l’éditeur. |
| **Blueprint en lecture seule** | Activer cette option si les zones ne doivent pas être modifiées en runtime.                         |
| **Réplicabilité future**       | Envisager la réplication si le système de spawn doit être cohérent en multijoueur.                  |
