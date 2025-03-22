---
description: Initialise les données du village, en chargeant les informations des PNJs.
icon: function
---

# InitializePNJ

### Description générale

`InitializePNJ` est une fonction interne du Blueprint **BP\_PNJ**.\
Elle est appelée après le spawn du PNJ, avec pour rôle principal de configurer l’apparence visuelle et les caractéristiques du PNJ à partir des données contenues dans **PNJData**.

Actuellement, la configuration est **minimale** : elle se concentre sur l'extraction des informations de base et l'affichage d'un message de debug, mais elle peut être étendue facilement.

***

### Détails techniques

| Propriété              | Valeur                                     |
| ---------------------- | ------------------------------------------ |
| **Nom de la fonction** | InitializePNJ                              |
| **Type**               | Function Blueprint (K2Node\_FunctionEntry) |
| **Accessibilité**      | Editable (modifiable dans le Blueprint)    |
| **Entrées**            | Aucun input personnalisé                   |
| **Sortie**             | Exécution (Exec)                           |

***

### Fonctionnement

#### Étapes principales :

1. **Récupération des données PNJ**
   * La variable **PNJData** est utilisée comme source d’information (type : `Struct_PNJData`).
   * Elle est décomposée via un **Break Struct** pour obtenir :
     * **Name** (Nom du PNJ)
     * **Profession**
     * **Clan**
     * **Traits** (Struct PNJTraits)
     * **Relations** (Map de relations)
2. **Affichage debug**
   *   Construction d’un message texte personnalisé :

       ```
       InitializePNJ : {Name}
       ```

       Le nom est directement récupéré depuis les données du PNJ.
   * Le message est converti en chaîne et affiché via `KismetSystemLibrary → PrintString` :
     * **Affichage à l’écran** : Oui
     * **Affichage dans le log** : Oui
     * **Couleur** : Cyan
     * **Durée** : 2 secondes

***

### Objectif principal

Configurer l’apparence et les caractéristiques de base du PNJ après son apparition dans le monde, à partir de **PNJData**.

***

### Bonnes pratiques recommandées

* **Validation des données** :
  * Ajouter des vérifications pour s’assurer que **PNJData** est correctement initialisé avant d’accéder aux propriétés.
* **Évolutivité** :
  * Ajouter des étapes pour appliquer visuellement la profession ou le clan (ex : changement de mesh, couleur, comportement IA).
* **Nettoyage debug** :
  * Prévoir un booléen **bDebugPNJInit** pour pouvoir désactiver facilement le `PrintString` en production.
* **Séparation claire** :
  * Si la logique devient plus complexe, envisager de séparer les responsabilités :
    * Une fonction pour l’apparence
    * Une pour les comportements/traits
    * Une pour les relations

***

### Suggestions d’amélioration

* **Paramètres d’entrée personnalisés** (ex : forcer certaines valeurs lors de l'initialisation manuelle).
* **Ajout d’un booléen de succès** en sortie pour savoir si l'initialisation s'est correctement effectuée.
* **Support multijoueur** : Si nécessaire, restreindre certaines configurations côté serveur uniquement.

***

### Exemple de commentaire à insérer dans Unreal :

```
Initialise les propriétés du PNJ après le spawn à partir du PNJData (nom, profession, clan...).
Affiche un message debug indiquant le nom du PNJ.
À étendre pour configurer l’apparence et le comportement complet.
```
