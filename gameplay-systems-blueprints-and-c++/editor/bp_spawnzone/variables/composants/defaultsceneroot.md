---
icon: rectangle-wide
---

# DefaultSceneRoot

#### Description générale

`DefaultSceneRoot` est le composant racine par défaut pour l’acteur Blueprint. C’est un **Scene Component**, servant de point d’ancrage principal pour tous les autres composants attachés à l’acteur. Par défaut, il n’a pas de comportement visuel ni de collision, mais il définit la position, rotation et échelle de l’acteur dans l’espace 3D.

***

#### Détails techniques

| Propriété                    | Valeur                                                                                                                 |
| ---------------------------- | ---------------------------------------------------------------------------------------------------------------------- |
| **Nom du composant**         | DefaultSceneRoot                                                                                                       |
| **Type de composant**        | Scene Component                                                                                                        |
| **Catégorie**                | Par défaut                                                                                                             |
| **Exposer à la cinématique** | Non                                                                                                                    |
| **Valeur par défaut**        | None (aucun composant spécifique défini)                                                                               |
| **Indicateurs de propriété** | `BlueprintVisible`, `ZeroConstructor`, `InstancedReference`, `NonTransactional`, `NoDestructor`, `HasGetValueTypeHash` |

***

#### Comportement

* **Racine de l’acteur** : Tous les autres composants sont attachés à ce composant.
* **Position / Rotation / Échelle** : Détermine la transformation spatiale de l’acteur dans le monde.
* **Aucun composant visuel** : Il ne rend rien à l’écran par défaut.
* **Aucune collision** : Il n'interagit pas avec la physique ou les collisions.

***

#### Événements disponibles

| Événement                    | Description                                                           |
| ---------------------------- | --------------------------------------------------------------------- |
| **On Component Activated**   | Déclenché lorsque le composant est activé.                            |
| **On Component Deactivated** | Déclenché lorsque le composant est désactivé.                         |
| **Physics Volume Changed**   | Déclenché lorsque le composant entre ou sort d'un volume de physique. |

***

#### Utilisation prévue

* **Structure de base** : Sert à structurer l’acteur même si aucun autre composant n’est ajouté.
* **Peut être remplacé** : Il est souvent remplacé par un autre composant (par ex. un StaticMeshComponent) si l’acteur doit avoir un visuel ou une collision par défaut.

***

#### Bonnes pratiques

* **Remplacement si nécessaire** : Pour les acteurs ayant un visuel ou comportement spécifique, il est conseillé de remplacer le `DefaultSceneRoot` par un composant plus approprié.
* **Nom explicite si personnalisé** : Si jamais tu crées une variante du composant racine, pense à le renommer pour refléter sa fonction (ex : `RootCollider`, `VisualRoot`…).

***

#### Suggestions d’améliorations

| Suggestion             | Détail                                                                                             |
| ---------------------- | -------------------------------------------------------------------------------------------------- |
| **Description Unreal** | Ajouter une description dans l’inspecteur expliquant qu'il s'agit du composant racine par défaut.  |
| **Catégorisation**     | Si le projet contient plusieurs composants personnalisés, envisager une catégorie du type \*\*Core |
