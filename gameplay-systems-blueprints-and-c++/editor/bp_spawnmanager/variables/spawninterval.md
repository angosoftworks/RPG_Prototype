---
description: Volumes définissant les zones valides pour le spawn dynamique.
icon: rectangle-wide
---

# SpawnInterval

#### Description générale

`SpawnInterval` est une variable de type **float (double précision)** utilisée pour définir l'intervalle de temps (en secondes) entre deux spawns consécutifs d’acteurs. Elle contrôle la cadence à laquelle le système de spawn génère de nouveaux acteurs dans le jeu.

***

#### Détails techniques

| Propriété                      | Valeur                                 |
| ------------------------------ | -------------------------------------- |
| **Nom de la variable**         | SpawnInterval                          |
| **Type**                       | Réel (`double`)                        |
| **Catégorie**                  | Par défaut                             |
| **Instance modifiable**        | Non                                    |
| **Blueprint en lecture seule** | Non                                    |
| **Exposer à l’apparition**     | Non                                    |
| **Privé**                      | Non (accessible aux autres Blueprints) |
| **Réplicable**                 | Non                                    |
| **Condition de réplication**   | Aucune                                 |
| **Valeur par défaut**          | `0.0`                                  |

***

#### Comportement

* **Contrôle du timing** : Cette variable agit comme une minuterie pour espacer les spawns successifs.
* **Non modifiable à l’instanciation** : La valeur doit être définie soit par défaut, soit modifiée dynamiquement via script ou Blueprint.
* **Locale** : La variable n'est pas répliquée — elle est propre à l’instance locale (client ou serveur).

***

#### Utilisation prévue

`SpawnInterval` est principalement utilisée pour :

* Réguler la fréquence d'apparition des acteurs générés par le système de spawn.
* Offrir un contrôle simple pour ajuster la difficulté ou l'intensité du jeu (plus l'intervalle est court, plus les spawns sont fréquents).
* Servir dans des minuteries (Timers) ou des boucles contrôlées.

***

#### Bonnes pratiques

* **Validation** : Toujours s’assurer que la valeur est strictement positive avant utilisation pour éviter des spawns simultanés ou des comportements non désirés.
* **Paramétrage dynamique** : Elle peut être ajustée en fonction du contexte de jeu (par exemple : réduire l'intervalle en fonction du niveau ou du temps écoulé).
* **Documentation** : Ajouter une description dans Unreal expliquant son rôle précis.
* **Éviter les valeurs extrêmes** : Ne pas définir de valeur trop faible (proche de 0) pour préserver les performances et éviter une surcharge d’acteurs.

***

#### Suggestions d’améliorations

| Suggestion                     | Détail                                                                                            |
| ------------------------------ | ------------------------------------------------------------------------------------------------- |
| **Catégorisation**             | Créer une catégorie personnalisée (ex. : \`Gameplay                                               |
| **Description**                | Ajouter une description explicite dans Unreal (tooltip) pour expliquer sa fonction.               |
| **Blueprint en lecture seule** | Activer cette option si la variable doit uniquement être consultée durant le gameplay.            |
| **Réplicabilité future**       | Envisager la réplication si le système de spawn doit être cohérent et synchronisé en multijoueur. |

***

#### Exemple visuel _(optionnel pour enrichir le GitBook)_ :

* Capture d’écran d’une configuration de **Timer** utilisant `SpawnInterval` pour lancer une fonction de spawn à intervalles réguliers.
* Exemple d'un graphique montrant l'effet de différentes valeurs d'intervalle sur la densité des spawns.

***

**Résumé :**\
Avec **SpawnInterval**, tu maîtrises précisément la fréquence des spawns, offrant un levier important pour équilibrer rythme et difficulté dans ton gameplay.
