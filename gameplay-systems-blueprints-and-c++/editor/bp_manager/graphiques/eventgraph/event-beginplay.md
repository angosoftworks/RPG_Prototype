---
icon: arrow-right-to-bracket
---

# Event BeginPlay

### Description générale

L’événement **ReceiveBeginPlay** est déclenché automatiquement lorsque l’acteur `BP_Manager` est chargé dans le monde ou lorsque le jeu commence.\
Il sert ici de point de départ pour initialiser les données critiques du village et préparer les PNJs pour le gameplay.

***

### Détails techniques

| Propriété                  | Valeur                         |
| -------------------------- | ------------------------------ |
| **Nom de l’événement**     | ReceiveBeginPlay               |
| **Classe parente**         | `Actor`                        |
| **Override**               | Oui (`bOverrideFunction=True`) |
| **Position dans le graph** | Y: -608                        |
| **Statut**                 | Actif                          |

***

### Fonctionnement

#### Flow d'exécution :

```
[ReceiveBeginPlay]
    ↓
[KismetSystemLibrary → PrintString : "BP_Manager → Village Initialization Started"]
    ↓
[InitializeVillageData]
    ↓
[SpawnAllPNJs]
```

#### Détail des étapes :

1. **PrintString**
   *   Utilise `KismetSystemLibrary → PrintString` pour afficher le message :

       ```
       mathematicaCopierModifierBP_Manager → Village Initialization Started
       ```
   * Paramètres :
     * **Affichage à l’écran** : Oui
     * **Affichage dans le log** : Oui
     * **Couleur du texte** : Cyan (R=0, G=0.66, B=1)
     * **Durée d’affichage** : 2 secondes
   * Utilité : Debug visuel confirmant que le système du village a bien démarré.
2. **InitializeVillageData**
   * Appelle la fonction interne responsable de charger les données des PNJs et du village.
   * Garantit que les données sont prêtes avant de spawner les PNJs.
3. **SpawnAllPNJs**
   * Fait apparaître tous les PNJs configurés en fonction des données précédemment chargées.
   * Prépare le village pour l’interaction joueur et les systèmes de gameplay.

***

### Objectif principal

Initialiser le système de gestion du village dès le lancement du jeu, avec une confirmation visuelle, le chargement des données et le spawning des PNJs.

***

### Bonnes pratiques recommandées

* **Condition serveur (Multijoueur)** : Ajouter une vérification `HasAuthority` pour s’assurer que l’initialisation ne se fait que sur le serveur.
* **Toggle Debug Print** : Ajouter un booléen (`bDebugMode`) pour activer ou désactiver l’affichage du `PrintString` en production.
* **Gestion d’erreur** : Intégrer un retour (par exemple, booléen de succès) dans `InitializeVillageData` pour détecter d’éventuels échecs de chargement.
*   **Commentaires dans Unreal** :\
    Ajouter un commentaire directement sur l’événement pour résumer :

    ```
    nginxCopierModifierInitialise le système du village au démarrage : 
    affiche un message de debug, charge les données des PNJs et lance le spawn des PNJs.
    ```

***

### Suggestion d’amélioration future

* **Ajout de conditions sur le type de niveau** (ex : ne pas initialiser le village sur un niveau de menu).
* **Centralisation de l'initialisation dans une fonction dédiée unique** si d’autres systèmes doivent être initialisés.
