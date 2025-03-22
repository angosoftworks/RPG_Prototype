---
icon: rectangle-wide
---

# Box

#### Description générale

`Box` est un composant de type **Box Collision**, utilisé pour définir une zone de collision en forme de boîte (parallélépipède rectangle) au sein d’un acteur Blueprint. Il est principalement utilisé pour détecter des collisions, déclencher des événements d’overlap ou servir de volume de référence (par exemple dans un système de spawn).

***

#### Détails techniques

| Propriété                    | Valeur                                                                                                                 |
| ---------------------------- | ---------------------------------------------------------------------------------------------------------------------- |
| **Nom du composant**         | Box                                                                                                                    |
| **Type de composant**        | Box Collision (BoxComponent)                                                                                           |
| **Catégorie**                | Par défaut                                                                                                             |
| **Exposer à la cinématique** | Non                                                                                                                    |
| **Valeur par défaut**        | None (aucun composant assigné initialement)                                                                            |
| **Indicateurs de propriété** | `BlueprintVisible`, `ZeroConstructor`, `InstancedReference`, `NonTransactional`, `NoDestructor`, `HasGetValueTypeHash` |

***

#### Comportement

* **Zone de collision en boîte** : Permet de détecter quand un acteur ou un composant entre ou sort de la zone définie.
* **Aucun visuel par défaut** : Ne possède pas de rendu visuel, utilisé uniquement pour la détection de collisions.
* **Peut être redimensionné et repositionné** : Les dimensions et la position sont ajustables dans l’inspecteur ou via Blueprint.

***

#### Événements disponibles

| Événement                                      | Description                                                                       |
| ---------------------------------------------- | --------------------------------------------------------------------------------- |
| **On Component Hit**                           | Déclenché lorsqu’un autre composant entre en collision physique avec cette boîte. |
| **On Component Begin Overlap**                 | Déclenché lorsqu’un autre composant entre en overlap avec la boîte.               |
| **On Component End Overlap**                   | Déclenché lorsqu’un autre composant sort de l’overlap.                            |
| **On Component Wake / Sleep**                  | Relatif au sommeil/réveil physique du composant.                                  |
| **On Component Physics State Changed**         | Changements d’état physique du composant.                                         |
| **On Begin / End Cursor Over**                 | Détecte si le curseur survole la boîte (utile pour l’interaction UI 3D).          |
| **On Clicked / On Released**                   | Interaction via clic sur la boîte.                                                |
| **On Input Touch Begin / End / Enter / Leave** | Détection tactile (mobiles/écrans tactiles).                                      |
| **Physics Volume Changed**                     | Lorsque le composant change de volume de physique.                                |

***

#### Utilisation prévue

* **Zones de Spawn** : Sert souvent à délimiter une zone dans laquelle des acteurs peuvent apparaître aléatoirement.
* **Détection d’Overlaps** : Déclenchement d’événements pour spawn, gameplay, ou logiques spécifiques.
* **Volume d’interaction** : Peut être utilisé pour capter des clics ou interactions dans l’environnement.

***

#### Bonnes pratiques

* **Nom explicite** : Si plusieurs boîtes sont utilisées, il est conseillé de renommer le composant pour refléter son rôle (ex. : `SpawnZoneVolume`, `TriggerBox`…).
* **Dimension adéquate** : Ajuster précisément la taille du Box pour éviter les overlaps inutiles ou trop larges.
* **Utilisation des événements** : Implémenter les événements nécessaires uniquement (BeginOverlap, EndOverlap) pour éviter des appels inutiles.

***

#### Suggestions d’améliorations

| Suggestion                                   | Détail                                                                                         |
| -------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| **Description Unreal**                       | Ajouter une description dans le composant pour clarifier son rôle dans l’inspecteur.           |
| **Catégorisation**                           | Organiser sous une catégorie personnalisée comme \*\*Gameplay                                  |
| **Activer uniquement les événements requis** | Pour des performances optimisées, désactiver les événements inutilisés via le panneau Détails. |
