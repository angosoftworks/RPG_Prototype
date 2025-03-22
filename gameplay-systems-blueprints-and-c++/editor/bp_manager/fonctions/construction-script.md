---
icon: function
---

# Construction Script

#### **Description générale :**

La fonction **`UserConstructionScript`** est un événement spécial dans Unreal Engine, déclenché à chaque fois qu'une instance de l’acteur **BP\_Manager** est placée ou modifiée dans l'éditeur. Son but est généralement d'initialiser ou configurer des composants et variables **au moment de la construction dans l’éditeur** (et non en runtime).

***

#### **Propriétés techniques :**

| Propriété              | Détail                                                                                        |
| ---------------------- | --------------------------------------------------------------------------------------------- |
| **Nom de la fonction** | `UserConstructionScript`                                                                      |
| **Type de fonction**   | **Override** de la fonction native `UserConstructionScript` d'Actor                           |
| **Appelé**             | Automatiquement **à l'édition** : lors du drag & drop ou de modifications dans les propriétés |
| **Entrées/Sorties**    | Exécution simple (`Exec` pins), pas de paramètres externes                                    |

***

#### **Détails :**

**Fonction actuelle :**

* **Aucun nœud interne particulier** n'est défini dans la version actuelle que tu m'as fournie.
* Le script est pour l’instant **vide**, il se limite à une connexion de sortie d'exécution (`then` pin) sans action.

***

#### **Utilisations typiques possibles (non encore implémentées) :**

Voici des cas d’usage classiques pour cette fonction :

| Cas d'usage                              | Exemple                                                                                            |
| ---------------------------------------- | -------------------------------------------------------------------------------------------------- |
| Initialisation de variables d'éditeur    | Pré-remplir des arrays, structs ou valeurs visibles dans l'éditeur.                                |
| Placement automatique de sous-composants | Ajuster la position ou la taille d’un volume, mesh ou collider à l’édition.                        |
| Visualisation helpers                    | Ajouter des éléments de debug visuels pour voir zones d’influence, spawn points, etc.              |
| Gestion dynamique d’enfants              | Modifier dynamiquement des enfants ou composants du blueprint selon certaines propriétés exposées. |

***

#### **Remarques spécifiques pour BP\_Manager :**

Tu pourrais par exemple envisager d’ajouter dans **`UserConstructionScript`** :

* Une boucle qui visualise les **SpawnPointsArray** ou **SpawnZoneVolume** en les colorant différemment dans l’éditeur.
* Un contrôle pour générer des **Preview PNJ** juste à l'édition (non persistent en jeu).
* Initialiser des valeurs par défaut dans les arrays si aucun n’est rempli, pour éviter d'oublier en design time.

***

#### **Comportement runtime :**

⚠️ **Important :**

* Le `UserConstructionScript` **n’est exécuté qu’en mode éditeur**.
* Il **ne s'exécute pas au runtime (jeu lancé)**, sauf si tu recharges un niveau contenant l’acteur.
* Pour toute logique de jeu dynamique, il vaut mieux privilégier le **BeginPlay**.

***

#### **Exemple d'implémentation recommandée (idée) :**

```unreal
ForEach Loop → SpawnZoneVolume Array:
   → Draw Debug Box (Visible only in editor)
```
