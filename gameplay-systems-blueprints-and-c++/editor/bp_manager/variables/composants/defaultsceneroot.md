---
icon: rectangle-wide
---

# DefaultSceneRoot

### Description générale

`DefaultSceneRoot` est un composant de type **Scene Component**, automatiquement ajouté par Unreal Engine lorsqu’aucun autre composant racine n’est spécifié dans un Blueprint Actor.

Il sert de point de référence racine (root) pour positionner et hiérarchiser les autres composants attachés à cet acteur.

### Détails techniques

* **Nom de la variable :** `DefaultSceneRoot`
* **Type :** `Scene Component`
* **Exposer à la cinématique :** Non
* **Catégorie :** Par défaut
* **Valeur par défaut :** Aucun (par défaut, c’est simplement un transform vide)

### Comportement

* **Rôle principal :** Sert de racine pour l’acteur si aucun autre composant racine n’a été assigné.
* Tous les autres composants visuels, collision ou logiques que tu ajoutes dans ce Blueprint seront automatiquement attachés au `DefaultSceneRoot` sauf si remplacé.
* Peut être remplacé par un autre composant racine spécifique (comme un `StaticMeshComponent` ou un `CapsuleComponent`) pour donner un comportement ou une représentation visuelle particulière à l’acteur.

### Événements liés

La variable expose trois événements par défaut, liés aux comportements du composant :

| Événement                  | Description                                                                                                     |
| -------------------------- | --------------------------------------------------------------------------------------------------------------- |
| `Physics Volume Changed`   | Déclenché quand l’acteur change de volume physique (par ex. entrer/sortir d’un volume d'eau, zone spéciale).    |
| `On Component Activated`   | Déclenché lorsque le composant est activé (peut être utilisé pour déclencher des comportements à l'activation). |
| `On Component Deactivated` | Déclenché lorsque le composant est désactivé.                                                                   |

### Utilisation prévue

Le `DefaultSceneRoot` n’a pas de comportement spécifique en lui-même, il est simplement là pour assurer que l’acteur a une base hiérarchique stable.\
Il est souvent laissé par défaut si l’acteur n’a pas besoin d’un composant visible ou physique particulier.

Si tu as besoin que ton acteur ait une **collision**, un **mesh visible**, ou un **comportement spécifique (ex: capsule pour le joueur)**, il est courant de remplacer le `DefaultSceneRoot` par un composant plus approprié.

### Bonnes pratiques

1. Remplacer le `DefaultSceneRoot` si l’acteur doit avoir un comportement physique, visuel ou interactif spécifique.
2. Laisser le `DefaultSceneRoot` uniquement pour des Blueprints purement logiques ou managers sans représentation dans le monde.
3. Si utilisé, les transformations appliquées à l’acteur (position, rotation, échelle) passent par ce composant.
4. Ne pas laisser d’éléments critiques dépendants directement du `DefaultSceneRoot` si celui-ci est destiné à être remplacé ultérieurement.

### Suggestions d'améliorations

* **Catégorie personnalisée :** Peut être ignorée ici, le composant n’a pas besoin d’être reclassé sauf si tu veux uniformiser l’apparence de tes variables.
* **Nom personnalisé :** Si tu choisis de garder un composant racine par défaut mais souhaite clarifier son rôle (ex: `RootTransform`, `ManagerRoot`), renommer peut être pertinent.
* À chaque spawn d’un PNJ :
  * Ajouter sa référence à `SpawnedPNJArray`.
* Lors de la destruction d’un PNJ :
  * Retirer la référence du tableau.
* Lors d’une action globale (ex : “freeze all PNJs”) :
  * Boucler sur `SpawnedPNJArray` pour envoyer l’instruction à chaque PNJ actif.
