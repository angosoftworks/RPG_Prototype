# BPI\_SpawnZone

#### Description générale

Le **BPI\_SpawnZone** est une **Blueprint Interface** dédiée à la communication et l’interaction avec les zones de spawn (Spawn Zones) du jeu. Cette interface sert à garantir que tout acteur ou système pouvant interagir avec une zone de spawn dispose d’un ensemble commun de fonctions exposées.

***

#### Détail actuel des Fonctions

| Fonction actuelle | Détails                                                                                                                                                                                                                                                                                                                   |
| ----------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **NewFunction**   | <p>- <strong>Nom de fonction :</strong> <code>NewFunction</code><br>- <strong>Description :</strong> Vide<br>- <strong>Catégorie :</strong> Par défaut<br>- <strong>Mots-clés :</strong> Aucun<br>- <strong>Entrées / Sorties :</strong> Aucune pour le moment<br>- <strong>Appel dans l'éditeur :</strong> Désactivé</p> |

***

#### Paramètres de la fonction

| Propriété                 | Valeur actuelle  |
| ------------------------- | ---------------- |
| **Nom**                   | `NewFunction`    |
| **Catégorie**             | Par défaut       |
| **Description**           | (Non renseignée) |
| **Titre de nœud compact** | (Non renseigné)  |
| **Appel dans l'éditeur**  | Désactivé        |
| **Entrées**               | Aucune           |
| **Sorties**               | Aucune           |

***

#### Analyse

Pour l’instant, cette interface contient uniquement une **fonction placeholder (NewFunction)** qui n’a pas encore de paramètres définis, ni de logique associée.

***

#### Suggestions d’amélioration

| Action proposée                                                                                   | Pourquoi ?                                                                                       |
| ------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------ |
| Renommer `NewFunction` en une fonction claire (ex : `IsZoneAvailable`, `RequestSpawnPoint`, etc.) | Donner un sens explicite à la fonction pour décrire l’interaction attendue avec la zone.         |
| Ajouter des **Entrées** ou **Sorties** pertinentes (bool, vector, actor, etc.)                    | Permet de réellement transmettre des informations nécessaires (par ex. : position, statut, etc.) |
| Remplir la **Description** et les **Mots-clés**                                                   | Pour mieux documenter et retrouver la fonction facilement via la recherche.                      |
| Organiser les fonctions par **Catégorie** si tu comptes en ajouter plusieurs                      | Plus lisible, surtout si plusieurs zones ou comportements liés à différentes fonctionnalités.    |

***

#### Exemple d’une fonction typique dans une Interface SpawnZone :

| Nom fonction           | Type de retour | Entrées possibles                 | Utilité                                                            |
| ---------------------- | -------------- | --------------------------------- | ------------------------------------------------------------------ |
| `IsZoneAvailable`      | Bool           | Aucun ou Acteur appelant          | Vérifie si la zone est disponible pour le spawn                    |
| `RequestSpawnLocation` | Vector         | Acteur ou Classe d’acteur à spawn | Retourne un point de spawn valide dans la zone                     |
| `OnActorSpawned`       | Void           | Acteur spawné                     | Notifie que l’acteur vient d’être spawné, pour mise à jour interne |

***

#### Conclusion

Actuellement, la **BPI\_SpawnZone** est prête pour être étoffée. Elle est bien intégrée dans ton système (comme vu précédemment avec son implémentation dans le BP\_SpawnZone), mais mérite qu’on lui ajoute les fonctions concrètes nécessaires pour faciliter la gestion du système de spawn.
