---
icon: function
---

# Construction Script

#### Description générale

`UserConstructionScript` est une fonction spéciale intégrée dans chaque Blueprint héritant d'**Actor**, appelée automatiquement lors de la construction ou modification d'un acteur dans l'éditeur. Elle permet d'exécuter du code spécifique au moment où l'acteur est placé ou mis à jour, sans avoir besoin de lancer le jeu.

Dans ton Blueprint **BP\_SpawnManager**, cette fonction peut être utilisée pour configurer des valeurs, instancier des composants, ou préparer dynamiquement l'apparence ou le comportement de l’acteur dès sa mise en place.

***

#### Détails techniques

| Propriété              | Valeur                                                       |
| ---------------------- | ------------------------------------------------------------ |
| **Nom de la fonction** | UserConstructionScript                                       |
| **Type de graphe**     | Function                                                     |
| **Défini dans**        | `/Game/Blueprints/BP_SpawnManager`                           |
| **Accessible depuis**  | Éditeur (au moment du placement ou modification de l’acteur) |
| **Appelée en runtime** | Non                                                          |
| **Définie par défaut** | Oui (héritée de la classe `Actor`)                           |

***

#### Comportement

* **Événement Éditeur uniquement** : Cette fonction est appelée **uniquement dans l’éditeur** lorsque l’acteur est placé, déplacé ou modifié. Elle n’est pas exécutée à l’exécution du jeu.
* **Personnalisation visuelle ou logique** : Permet d’ajouter dynamiquement des éléments visibles, ajuster des propriétés, ou générer du contenu basé sur des paramètres définis dans l’éditeur.
* **Ne pas inclure de logique gameplay** : Éviter d'y inclure des éléments critiques pour le gameplay, car elle n'est pas appelée en jeu.

***

#### Utilisation prévue

Dans le cadre du **BP\_SpawnManager**, la fonction `UserConstructionScript` peut être utilisée pour :

* Initialiser ou ajuster visuellement les zones de spawn.
* Pré-remplir certaines variables visibles dans l’éditeur à des fins de preview.
* Mettre à jour dynamiquement des composants ou repères (par exemple, des volumes ou gizmos liés aux zones de spawn).
* Valider certaines configurations à l'édition (par exemple, vérifier si certaines références comme `SpawnZones` ou `ActorToSpawn` sont correctement assignées).

***

#### Bonnes pratiques

* **Limiter aux tâches visuelles ou d’édition** : Éviter d’y inclure de la logique métier ou de gameplay.
* **Optimisation** : Ne pas surcharger cette fonction, car elle est appelée fréquemment lors de modifications.
* **Validation** : Utiliser des checks (par ex. : `IsValid`) pour s’assurer que les modifications n’introduisent pas d’erreurs dans l’éditeur.
* **Commentaires** : Documenter clairement le but de chaque section dans le script, car les comportements ne sont visibles qu’en édition.

***

#### Suggestions d’améliorations

| Suggestion                 | Détail                                                                                                                             |
| -------------------------- | ---------------------------------------------------------------------------------------------------------------------------------- |
| **Organisation du graphe** | Ajouter des commentaires visuels et regrouper les nœuds pour plus de lisibilité.                                                   |
| **Validation visuelle**    | Ajouter des repères (debug shapes) pour représenter les zones de spawn en temps réel dans l’éditeur.                               |
| **Optimisation**           | Si certaines opérations sont lourdes, les conditionner pour éviter qu'elles ne s’exécutent inutilement à chaque changement minime. |

***

#### Exemple visuel _(optionnel pour ton GitBook)_ :

* Capture d’écran du Blueprint **UserConstructionScript** avec des commentaires expliquant chaque bloc logique.
* Exemple d'affichage dynamique de **zones de spawn** ou **gizmos** visibles dans l’éditeur grâce à cette fonction.

***

#### Remarque

**UserConstructionScript** est un outil puissant pour configurer et visualiser des comportements ou apparences personnalisés à l'édition, tout en gardant la logique du runtime propre et séparée (dans **BeginPlay** ou d'autres événements).
