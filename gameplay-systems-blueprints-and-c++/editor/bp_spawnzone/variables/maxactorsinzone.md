---
icon: rectangle-wide
---

# MaxActorsInZone

#### Description générale

`MaxActorsInZone` est une variable entière utilisée dans le Blueprint **BP\_SpawnZone**. Elle détermine le nombre maximal d'acteurs autorisés simultanément dans une zone donnée. Cette variable est essentielle pour contrôler la densité de spawn et éviter une surcharge d'acteurs dans une même zone.

***

#### Détails techniques

| Propriété                      | Valeur                                                                            |
| ------------------------------ | --------------------------------------------------------------------------------- |
| **Nom de la variable**         | MaxActorsInZone                                                                   |
| **Type**                       | Integer (int)                                                                     |
| **Catégorie**                  | Par défaut                                                                        |
| **Instance modifiable**        | Oui (modifiable dans l’inspecteur)                                                |
| **Blueprint en lecture seule** | Non                                                                               |
| **Exposer à l’apparition**     | Non                                                                               |
| **Privé**                      | Non (accessible aux autres Blueprints)                                            |
| **Réplicable**                 | Non                                                                               |
| **Condition de réplication**   | Aucune                                                                            |
| **Valeur par défaut**          | 0                                                                                 |
| **Description**                | "Nombre max d’acteurs autorisés dans la zone" (affichée dans l’inspecteur Unreal) |

***

#### Comportement

Cette variable fixe la limite supérieure du nombre d'acteurs pouvant être présents dans la zone associée. Elle est principalement utilisée dans les fonctions comme **IsZoneAvailable**, où elle est comparée avec la longueur du tableau des acteurs déjà présents (via **SpawnedActorsInZone**) pour décider si la zone est encore disponible pour le spawn.

***

#### Utilisation prévue

* **Contrôle du gameplay** : Évite qu’une zone soit saturée par trop d’acteurs.
* **Condition dans le système de spawn** : Vérifiée à chaque tentative de spawn dans la fonction **IsZoneAvailable**.
* **Paramétrage designer-friendly** : Peut être ajustée facilement depuis l’inspecteur Unreal sans modification du code.

***

#### Bonnes pratiques

* **Valeurs raisonnables** : Toujours définir des valeurs adaptées aux capacités de la zone (taille, type d’acteurs).
* **Utilisation de catégories personnalisées** : Envisager de la déplacer sous une catégorie spécifique (ex. `Spawn Settings | Zone`) pour une meilleure organisation.
* **Documentation** : Bien conserver ou enrichir le tooltip pour guider les designers (déjà présent ici, ce qui est parfait !).

***

#### Suggestions d’améliorations

| Suggestion                           | Détail                                                                                                                    |
| ------------------------------------ | ------------------------------------------------------------------------------------------------------------------------- |
| **Clamp possible**                   | Ajouter une logique dans le Blueprint ou Construction Script pour empêcher des valeurs négatives.                         |
| **Réglage dynamique**                | Si besoin, exposer cette variable via une interface utilisateur pour qu’elle soit ajustable à runtime.                    |
| **Ajout d'une réplicabilité future** | Si ton projet devient multijoueur, envisager une réplication pour que le nombre max soit cohérent côté client et serveur. |
