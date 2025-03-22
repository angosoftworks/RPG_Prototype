---
icon: arrow-right-to-bracket
---

# Event BeginPlay

### Description générale

L’événement **ReceiveBeginPlay** est appelé automatiquement lorsque l’acteur **BP\_PNJ** est chargé dans le niveau ou spawné en jeu.\
Actuellement, ce nœud est **désactivé** et n’exécute aucune logique.\
Il est présent pour permettre, si nécessaire, une initialisation spécifique des PNJs lors du début du jeu ou après leur apparition.

***

### Détails techniques

| Propriété                  | Valeur                                  |
| -------------------------- | --------------------------------------- |
| **Nom de l’événement**     | ReceiveBeginPlay                        |
| **Classe parente**         | `Actor`                                 |
| **Override**               | Oui (`bOverrideFunction=True`)          |
| **Statut**                 | **Désactivé** (`EnabledState=Disabled`) |
| **Position dans le graph** | Y: 0                                    |

***

### Fonctionnement actuel

* **État** : Le nœud est désactivé, il ne sera pas exécuté.
*   **Commentaire existant** :

    ```
    Ce nœud est désactivé et ne sera pas appelé.
    Faites glisser les broches pour générer des fonctionnalités.
    ```

***

### Utilisation potentielle

L’événement **BeginPlay** est souvent utilisé pour :

* Initialiser des comportements spécifiques au runtime.
* Déclencher une séquence ou une animation particulière pour le PNJ.
* Mettre en place des états par défaut (AI, dialogues...).

Dans le contexte actuel, il peut être utilisé pour :

* Appeler la fonction **InitializePNJ** si elle n'est pas déjà déclenchée ailleurs.
* Appliquer des paramètres dynamiques (niveau de difficulté, comportements spéciaux selon le contexte du niveau).

***

### Bonnes pratiques recommandées

* **Ne l’activer que si nécessaire**, pour éviter d’avoir des appels inutiles au runtime.
* Ajouter une **validation conditionnelle** (par ex. tag, variable booléenne) si plusieurs types de PNJs doivent avoir des comportements différents à l’initialisation.
* Centraliser la logique de configuration dans des fonctions dédiées pour garder un graph lisible (par ex. appeler `SetupPNJBehavior()`).

***

### Suggestion d’amélioration

* Si besoin, activer **BeginPlay** uniquement pour les PNJs nécessitant un comportement dynamique particulier.
* Ajouter une vérification réseau avec **`HasAuthority`** si certains comportements doivent se produire uniquement côté serveur.

***

### Exemple de commentaire à insérer dans Unreal :

```
Événement désactivé. À activer si le PNJ nécessite une logique spécifique au lancement du jeu (comportement, état, animation...).
```
