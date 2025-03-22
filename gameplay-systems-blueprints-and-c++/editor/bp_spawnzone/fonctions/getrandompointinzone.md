---
description: Initialise les données du village, en chargeant les informations des PNJs.
icon: function
---

# GetRandomPointInZone

#### Description générale

`GetRandomPointInZone` est une fonction définie dans le Blueprint **BP\_SpawnZone**. Elle est utilisée pour calculer un point aléatoire à l’intérieur d’une zone définie par un **BoxComponent**, permettant ainsi de déterminer dynamiquement des positions valides pour le spawn d’acteurs.

Cette fonction combine l’étendue (extent) du Box et sa position, puis génère aléatoirement un point dans les limites de la boîte.

***

#### Détails techniques

| Propriété                | Valeur                                    |
| ------------------------ | ----------------------------------------- |
| **Nom de la fonction**   | GetRandomPointInZone                      |
| **Définie dans**         | `/Game/Blueprints/BP_SpawnZone`           |
| **Retour**               | `Vector` (coordonnées du point aléatoire) |
| **Editable**             | Oui                                       |
| **Paramètres en entrée** | Aucun                                     |
| **Paramètre en sortie**  | `Vector`                                  |

***

#### Comportement

1. **Récupération du Box Component** :
   * La fonction utilise la variable `Box` (un **BoxComponent**) définie dans **BP\_SpawnZone** pour obtenir les dimensions et la position de la zone.
2. **Calcul de l’étendue (Extent)** :
   * Appel à **GetScaledBoxExtent** pour récupérer l’étendue du Box prenant en compte l’échelle.
3. **Récupération de la position du Box** :
   * Utilisation de **K2\_GetComponentLocation** pour obtenir la position du Box dans l’espace monde.
4. **Génération aléatoire des coordonnées (X, Y, Z)** :
   * Pour chaque axe (X, Y, Z), la fonction génère une valeur aléatoire comprise entre **-Extent** et **+Extent** via **RandomFloatInRange**.
5. **Construction du vecteur résultat** :
   * Les trois valeurs aléatoires sont combinées pour former un vecteur.
   * Ce vecteur est ensuite additionné à la position du Box, fournissant un point relatif à la zone dans le monde.
6. **Retour du point calculé** :
   * La fonction retourne ce point sous forme de **Vector**.

***

#### Utilisation prévue

* **Système de spawn** : Déterminer dynamiquement des positions de spawn valides pour des PNJs, objets ou ennemis.
* **Gameplay aléatoire** : Créer de la variabilité dans le positionnement des entités.
* **Zones paramétrables** : Fonctionne avec n’importe quel BoxComponent configuré, offrant une flexibilité totale.

***

#### Bonnes pratiques

* **Validation** : Toujours s’assurer que le BoxComponent est correctement configuré (taille, position, échelle) avant d’utiliser cette fonction.
* **Utilisation combinée** : Appelée typiquement depuis un SpawnManager pour distribuer les spawns sur plusieurs zones.
* **Optimisation** : Fonction pure, légère, sans logique complexe – idéale pour appel fréquent.

***

#### Suggestions d’améliorations

| Suggestion                                | Détail                                                                                            |
| ----------------------------------------- | ------------------------------------------------------------------------------------------------- |
| **Ajout d’un paramètre Seed (optionnel)** | Permettrait de rendre le point pseudo-aléatoire réplicable si besoin (pour du multijoueur).       |
| **Ajout d’une option 2D uniquement (XY)** | Si certains usages n’utilisent que le plan XY, ajouter un booléen pour ignorer la Z.              |
| **Documentation interne**                 | Ajouter une description directement dans le Blueprint expliquant brièvement la logique du calcul. |

***

#### Exemple visuel _(pour GitBook si besoin)_

* Capture d’écran du Blueprint montrant clairement les étapes :
  1. Récupération de l’extent.
  2. Génération aléatoire X, Y, Z.
  3. Addition avec la position du Box.
  4. Retour du Vector.

***

#### Remarque

Cette fonction est un élément essentiel pour garantir des spawns variés tout en restant confinés dans des zones définies, offrant un parfait équilibre entre contrôle et aléatoire.
