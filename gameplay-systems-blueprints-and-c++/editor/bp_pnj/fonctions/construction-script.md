---
icon: function
---

# Construction Script

### Description générale

Le **UserConstructionScript** est une fonction native du Blueprint **BP\_PNJ** qui est exécutée **lors de la construction** ou **modification** du PNJ dans l’éditeur ou lors du spawn runtime.\
Il permet de configurer ou pré-initialiser certains éléments visuels ou logiques **avant** que le jeu ne démarre.

***

### Détails techniques

| Propriété              | Valeur                                       |
| ---------------------- | -------------------------------------------- |
| **Nom de la fonction** | UserConstructionScript                       |
| **Type**               | Function Blueprint (K2Node\_FunctionEntry)   |
| **Classe parente**     | Actor                                        |
| **Exécution**          | Éditeur et runtime (lors de la construction) |
| **Entrées**            | Aucun input personnalisé                     |
| **Sortie**             | Exécution (Exec)                             |

***

### Fonctionnement actuel

* **Contenu** :\
  Actuellement, le **UserConstructionScript** ne contient aucune logique spécifique. Il est prêt à être utilisé si des comportements liés à la construction du PNJ doivent être ajoutés (par exemple, ajustements visuels dynamiques dans l’éditeur).

***

### Objectif principal

Permettre la configuration dynamique des propriétés ou composants du PNJ **avant le lancement du jeu**, que ce soit en **éditeur** ou lors du **spawn runtime**.

Exemples d'utilisation typiques :

* Modifier visuellement le PNJ dans l’éditeur en fonction de certaines variables (ex : couleur, mesh, accessoires...).
* Préparer des éléments sans attendre le **BeginPlay** (utile pour avoir un aperçu en temps réel dans l’éditeur).

***

### Bonnes pratiques recommandées

* **Limiter la logique lourde** : Le **Construction Script** est appelé fréquemment dans l’éditeur, donc éviter d’y mettre des traitements coûteux.
* **Utiliser pour visualisation uniquement** : Préférer y placer des ajustements visuels (matériaux, meshes...) plutôt que du gameplay pur.
* **Conditionner si besoin** : Ajouter des conditions pour différencier l’exécution en éditeur ou en runtime (`IsRunningGame()` si nécessaire).

***

### Suggestions d’amélioration possible

* Intégrer un paramètre configurable (ex : preview mode) pour afficher certains états spéciaux du PNJ en éditeur.
* Utiliser des **Dynamic Materials** pour changer les couleurs, logos ou autres caractéristiques visuelles en fonction du **PNJData**.
* Coupler avec des **Editor Utility Widgets** si besoin d’une interface avancée d’édition des PNJs.

***

### Exemple de commentaire à insérer dans Unreal :

```
Permet d’ajuster dynamiquement les propriétés visuelles du PNJ lors de la construction (éditeur ou runtime).
Actuellement vide, à utiliser si besoin de prévisualisation ou configuration préalable.
```
