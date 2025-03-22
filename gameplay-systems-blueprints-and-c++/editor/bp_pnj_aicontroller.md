# BP\_PNJ\_AIController

#### 📝 **Description générale**

`BP_PNJ_AIController` est le contrôleur AI attribué aux PNJs du village.\
Il est responsable de la gestion des comportements, des déplacements et des décisions prises par les PNJs, en fonction des données initialisées et des stimuli du jeu.

Ce contrôleur sert d’intermédiaire entre les systèmes du village (données, états du jeu) et le comportement autonome des PNJs.

***

#### ⚙️ **Détails techniques**

| **Propriété**        | **Valeur**                                    |
| -------------------- | --------------------------------------------- |
| **Nom du Blueprint** | `BP_PNJ_AIController`                         |
| **Parent Class**     | `AIController` (ou custom parent si existant) |
| **Type**             | Blueprint Class                               |
| **Utilisé par**      | Tous les PNJs du village                      |
| **Catégorie**        | IA / PNJ                                      |
| **Accessibilité**    | Editable, configurable dans les PNJs          |

***

#### 🔄 **Fonctionnalités principales**

**1. Prise en charge du comportement IA :**

* Gère l’assignation des **Behavior Trees** (arbres de comportement) spécifiques aux PNJs.
* Peut contenir des **Blackboard Keys** liés aux données du PNJ (position, objectifs, état...).

**2. Communication avec le BP\_Manager :**

* Possibilité d’obtenir les informations du PNJ via des références ou interfaces pour accéder aux données initialisées.

**3. Gestion des stimuli :**

* Peut inclure un **Perception Component** (vue, ouïe, etc.) pour réagir à l’environnement.

***

#### 🗺️ **Flow visuel simplifié :**

```
[BP_PNJ_AIController] ---> [BehaviorTree] ---> [BlackboardData]
                        |
                        ---> [Perception Component] ---> [Stimuli Response]
```

***

#### 🚀 **Utilisation prévue**

* Assigné automatiquement aux PNJs lors de leur spawn.
* Contrôle les décisions d’IA pendant tout le cycle de vie du PNJ (déplacements, interactions, réactions aux joueurs ou événements du jeu).

***

#### ✅ **Bonnes pratiques recommandées**

1. **Modularité :**\
   Laisser les comportements spécifiques aux PNJs configurables (via variables exposées ou DataTables).
2. **Centralisation des références :**\
   Utiliser des interfaces ou des variables propres pour récupérer les données du PNJ (éviter les dépendances directes fortes avec BP\_Manager).
3. **Utilisation cohérente des Behavior Trees :**\
   Chaque PNJ ou groupe de PNJs peut utiliser un BT spécifique selon son rôle (marchand, villageois, garde...).
4. **Documentation dans Unreal :**\
   Ajouter un commentaire général dans la classe :\
   &#xNAN;_"Contrôleur AI des PNJs du village, chargé de gérer leurs comportements et interactions."_

***

#### 🌟 **Suggestions d’amélioration possible**

* **Ajout de logs ou tags de debug :**\
  Pour faciliter le suivi des décisions prises par les PNJs, surtout en phase de développement IA.
* **Gestion multijoueur :**\
  Si applicable, s’assurer que le contrôle de l’IA ne provoque pas de désynchronisation entre serveur et clients.
* **Paramétrage dynamique :**\
  Ajouter la possibilité de changer dynamiquement certains comportements du PNJ via des événements (par ex. changement d’état du village).

***

### 🏷️ **Résumé rapide**

| **Responsabilité principale** | Contrôler l’IA et le comportement des PNJs   |
| ----------------------------- | -------------------------------------------- |
| **Composants clés**           | BehaviorTree, Blackboard, Perception         |
| **Utilisé par**               | Tous les PNJs du village                     |
| **Interaction principale**    | Avec BP\_Manager, PNJ Data, Stimuli          |
| **Évolutions possibles**      | Logs, support multijoueur, modularité accrue |
