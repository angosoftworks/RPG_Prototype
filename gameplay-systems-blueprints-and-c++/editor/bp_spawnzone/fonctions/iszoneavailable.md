---
description: >-
  Charge les données des PNJs depuis la DataTable et remplit le tableau interne
  des PNJs.
icon: function
---

# IsZoneAvailable

#### Description générale

`IsZoneAvailable` est une fonction définie dans le Blueprint **BP\_SpawnZone**. Elle sert à déterminer si une zone de spawn est disponible pour accueillir un nouvel acteur. La disponibilité est calculée en fonction de plusieurs conditions sur le nombre d’acteurs présents dans la zone, l’état de la zone et un éventuel cooldown.

***

#### Détails techniques

| Propriété                | Valeur                                                 |
| ------------------------ | ------------------------------------------------------ |
| **Nom de la fonction**   | IsZoneAvailable                                        |
| **Définie dans**         | `/Game/Blueprints/BP_SpawnZone`                        |
| **Retour**               | `Booléen` (Vrai si la zone est disponible, Faux sinon) |
| **Editable**             | Oui                                                    |
| **Paramètres en entrée** | Aucun                                                  |
| **Paramètre en sortie**  | `IsAvailable` (booléen)                                |

***

#### Comportement

La fonction évalue la disponibilité d'une zone en combinant plusieurs conditions logiques :

1. **Condition 1 : Nombre d'acteurs spawnés < Maximum autorisé**
   * Accès au tableau **SpawnedActorsInZone**.
   * Utilisation de **Array\_Length** pour obtenir le nombre actuel d'acteurs présents.
   * Comparaison avec la variable **MaxActorsInZone** via un opérateur **Less ( < )**.
2. **Condition 2 : Zone activée**
   * Vérification de la variable booléenne **bIsZoneEnabled** (true si la zone est active).
3. **Condition 3 : Cooldown terminé**
   * Vérification de la variable booléenne **bCooldownOver** (true si le cooldown est terminé).
4. **Combinaison des conditions**
   * Les trois conditions sont combinées à l'aide d'un opérateur logique **AND**.
   * Le résultat final (True ou False) est renvoyé dans le paramètre de sortie **IsAvailable**.

***

#### Utilisation prévue

Cette fonction est appelée avant tout spawn d’acteur pour vérifier que :

* La zone n’a pas atteint sa capacité maximale.
* La zone est activée.
* Le cooldown éventuel est terminé.

Elle est typiquement utilisée dans des systèmes de **Spawn Manager** pour filtrer les zones valides avant de procéder au spawn.

***

#### Bonnes pratiques

* **Séparer la logique** : La logique est claire et modulaire, ce qui facilite la maintenance et les ajouts futurs (ex : ajouter une nouvelle condition).
* **Commentaires** : Ajouter des commentaires explicites dans le Blueprint sur chaque condition.
* **Optimisation** : La fonction est légère, aucune opération coûteuse, donc sans impact sur les performances même si appelée fréquemment.

***

#### Suggestions d’améliorations

| Suggestion                                   | Détail                                                                                                                         |
| -------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| **Exposer les paramètres dans l’inspecteur** | Si souhaité, rendre certains paramètres (comme MaxActorsInZone) modifiables plus facilement via des catégories personnalisées. |
| **Condition personnalisable**                | Ajouter un paramètre facultatif pour des conditions de disponibilité spécifiques selon les cas de gameplay.                    |
| **Log ou Debug**                             | Ajouter un log temporaire (via PrintString) pour déboguer pourquoi une zone est indisponible si besoin.                        |

***

#### Exemple visuel _(pour ton GitBook si besoin)_

* Capture d’écran du Blueprint montrant clairement :
  1. Vérification du nombre d’acteurs.
  2. Check du flag **bIsZoneEnabled**.
  3. Vérification de **bCooldownOver**.
  4. Opérateur AND combinant les trois conditions.

***

#### Remarque

Cette fonction est un excellent point de contrôle pour garantir que les conditions de gameplay relatives aux zones de spawn sont respectées de manière fiable et propre.
