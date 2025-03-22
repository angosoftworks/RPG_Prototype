---
icon: rectangle-wide
---

# DefaultSceneRoot

#### Description générale

`DefaultSceneRoot` est un composant de type **Scene Component** servant de racine hiérarchique pour l’acteur auquel il est attaché. Par défaut, il assure la position, la rotation et l’échelle de base pour tous les autres composants enfants attachés à l’acteur. Si aucun autre composant racine n’est défini, **DefaultSceneRoot** est utilisé automatiquement par Unreal Engine.

***

#### Détails techniques

| Propriété                    | Valeur           |
| ---------------------------- | ---------------- |
| **Nom du composant**         | DefaultSceneRoot |
| **Type**                     | Scene Component  |
| **Catégorie**                | Par défaut       |
| **Exposer à la cinématique** | Non              |
| **Valeur par défaut**        | Aucun (None)     |

***

#### Comportement

* **Racine hiérarchique** : Sert de point d’ancrage pour la hiérarchie des composants dans l’acteur.
* **Transformations** : Définit la position, la rotation et l’échelle par défaut du Blueprint ou de l’acteur.
* **Remplaçable** : Peut être remplacé par un autre composant racine personnalisé si besoin (par ex. un **Static Mesh**, **Skeletal Mesh**, ou tout autre composant).

***

#### Utilisation prévue

`DefaultSceneRoot` est principalement utilisé :

* Comme composant racine par défaut pour les acteurs ne nécessitant pas de mesh ou composant spécifique en racine.
* Pour gérer simplement la transformation globale de l’acteur.
* Pour maintenir une structure propre lorsque l’acteur est composé uniquement de composants logiques ou visuels secondaires.

***

#### Bonnes pratiques

* **Remplacement explicite** : Si l’acteur doit avoir un composant visuel ou fonctionnel particulier comme racine (par exemple un **StaticMeshComponent**), il est préférable de remplacer le **DefaultSceneRoot**.
* **Propreté hiérarchique** : Ne pas laisser des composants orphelins sans racine si vous supprimez ou remplacez le **DefaultSceneRoot**.
* **Utilisation dans Blueprints** : Peu d’interactions directes requises en Blueprint. Son usage est principalement structurel.
* **Transformation globale** : Utiliser ce composant pour appliquer des transformations globales à l’ensemble des composants enfants.

***

#### Suggestions d’améliorations

| Suggestion                 | Détail                                                                                              |
| -------------------------- | --------------------------------------------------------------------------------------------------- |
| **Catégorisation**         | Définir une catégorie personnalisée si le projet comporte plusieurs types de racines distinctes.    |
| **Nom personnalisé**       | Renommer le composant si un rôle spécifique lui est attribué dans l’acteur (ex. : `RootTransform`). |
| **Événements spécifiques** | Si besoin, exploiter les événements liés (`OnComponentActivated`, `OnComponentDeactivated`).        |

***

#### Événements disponibles

* **Physics Volume Changed** : Déclenché lorsque le composant entre ou sort d'un volume physique.
* **On Component Activated** : Déclenché lorsque le composant est activé.
* **On Component Deactivated** : Déclenché lorsque le composant est désactivé.

***

#### Exemple visuel _(pour GitBook si besoin)_ :

* Capture d’écran du Blueprint montrant le **DefaultSceneRoot** comme racine, avec des composants enfants attachés.
* Illustration d’une transformation appliquée directement sur le **DefaultSceneRoot** affectant tous les composants.

***

#### Remarque

Le **DefaultSceneRoot** est un élément fondamental dans Unreal pour garantir que chaque acteur possède une racine hiérarchique valide, même en l’absence de composants visuels.
