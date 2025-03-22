---
description: Volumes définissant les zones valides pour le spawn dynamique.
icon: rectangle-wide
---

# bUsePooling

#### Description générale

`bUsePooling` est une variable booléenne utilisée pour activer ou désactiver l'utilisation d'un système de **pooling** (réutilisation d’acteurs) lors du spawn. Le pooling permet d'améliorer les performances en évitant la destruction et recréation fréquente d’acteurs, en les recyclant à la place.

***

#### Détails techniques

| Propriété                      | Valeur                                 |
| ------------------------------ | -------------------------------------- |
| **Nom de la variable**         | bUsePooling                            |
| **Type**                       | Booléen (`bool`)                       |
| **Catégorie**                  | Par défaut                             |
| **Instance modifiable**        | Non                                    |
| **Blueprint en lecture seule** | Non                                    |
| **Exposer à l’apparition**     | Non                                    |
| **Privé**                      | Non (accessible aux autres Blueprints) |
| **Réplicable**                 | Non                                    |
| **Condition de réplication**   | Aucune                                 |
| **Valeur par défaut**          | `False`                                |

***

#### Comportement

* **Activation/Désactivation du pooling** : Si la variable est définie sur `True`, le système de spawn utilisera un pool d’acteurs pour réutiliser les instances existantes. Si `False`, chaque spawn créera un nouvel acteur sans réutilisation.
* **Non modifiable à l’instanciation** : La variable est configurée avant ou pendant l’exécution via Blueprint ou code.
* **Locale** : Aucun comportement de réplication — la variable reste locale au contexte (client ou serveur).

***

#### Utilisation prévue

`bUsePooling` est particulièrement utile pour :

* **Optimisation des performances**, en limitant le coût des opérations de spawn/despawn massifs.
* **Réduction du garbage collector**, car les acteurs sont conservés et remis en circulation au lieu d’être détruits.
* **Contrôle souple** : Elle offre la possibilité d’activer/désactiver facilement cette optimisation sans modifier la logique principale du système de spawn.

***

#### Bonnes pratiques

* **Validation** : Vérifier que le système de pooling est bien implémenté avant d’activer cette option.
* **Nettoyage** : S’assurer que les acteurs non utilisés sont correctement désactivés ou cachés lorsqu’ils retournent dans le pool.
* **Flexibilité** : Utiliser cette variable en conjonction avec des paramètres du système pour ajuster dynamiquement la taille du pool si nécessaire.
* **Documentation** : Ajouter une description claire dans l’éditeur pour signaler son rôle essentiel en optimisation.

***

#### Suggestions d’améliorations

| Suggestion                     | Détail                                                                                           |
| ------------------------------ | ------------------------------------------------------------------------------------------------ |
| **Catégorisation**             | Ajouter une catégorie personnalisée (ex. : \`Gameplay                                            |
| **Description**                | Ajouter une description explicite dans Unreal pour préciser l’impact de l'activation du pooling. |
| **Blueprint en lecture seule** | Activer si cette option est définie en début de session et ne doit pas être changée en runtime.  |
| **Réplicabilité future**       | Envisager la réplication si le pooling doit être synchronisé dans un contexte multijoueur.       |

***

#### Exemple visuel _(facultatif pour ton GitBook)_ :

* Diagramme simple montrant la différence entre spawn classique (création/destruction) et pooling (réutilisation d’acteurs).
* Capture d’écran d’un Blueprint conditionnant l’utilisation du pooling via `bUsePooling`.

***

#### Remarque

**bUsePooling** fonctionne très bien en synergie avec les variables comme **SpawnedActors** et **MaxSpawnedActors**, pour améliorer les performances globales tout en gardant un contrôle précis sur le nombre d’acteurs présents.
