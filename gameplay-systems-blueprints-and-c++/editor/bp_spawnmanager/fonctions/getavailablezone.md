---
description: >-
  Formate les données d’un PNJ pour affichage : Nom, Profession, Clan, Traits et
  Relations.
icon: function
---

# GetAvailableZone

#### 📝 **Description générale**

La fonction **GetAvailableZone** parcourt toutes les zones de spawn présentes dans le monde (de type **BP\_SpawnZone\_C**) et retourne la première zone disponible.

Elle repose sur une vérification dynamique à chaque appel, garantissant que la zone retournée est prête pour le spawn.

***

#### ⚙️ **Détails techniques**

| **Nom de la fonction** | `GetAvailableZone`                                      |
| ---------------------- | ------------------------------------------------------- |
| **Type**               | Function Blueprint (`K2Node_FunctionEntry`)             |
| **Accessibilité**      | Editable (modifiable dans le Blueprint)                 |
| **Catégorie**          | Par défaut                                              |
| **Entrées**            | Aucun input spécifique                                  |
| **Sortie**             | **AvailableZone** – Référence à un **BP\_SpawnZone\_C** |

***

#### 🔄 **Fonctionnement interne**

1. **Récupération des zones de spawn :**
   * Utilise **GetAllActorsOfClass** pour récupérer tous les acteurs de type **BP\_SpawnZone\_C** présents dans le monde.
2. **Boucle sur chaque zone :**
   * Un **ForEachLoop** parcourt toutes les zones récupérées.
3. **Vérification de disponibilité :**
   * Pour chaque zone, la fonction appelle **IsZoneAvailable** (fonction définie dans **BP\_SpawnZone\_C**).
   * Si la zone est disponible (`true`), la fonction sort de la boucle immédiatement et retourne cette zone.
4. **Résultat :**
   * Si une zone disponible est trouvée, elle est renvoyée via l’output **AvailableZone**.
   * Si aucune zone disponible n’est trouvée, aucune zone n’est retournée (peut être complété pour un fallback, comme renvoyer `None` ou un comportement alternatif).

***

#### 🗺️ **Flow visuel simplifié :**

```
[GetAvailableZone]
 └── GetAllActorsOfClass (BP_SpawnZone_C)
      └── For Each Zone
            └── Check IsZoneAvailable
                  ├── Si Oui → Retourne la zone (Function Result)
                  └── Si Non → Continue à la prochaine
```

***

#### 📋 **Variables utilisées**

| **Variable / Node**        | **Type**                           | **Rôle**                           |
| -------------------------- | ---------------------------------- | ---------------------------------- |
| **GetAllActorsOfClass**    | Fonction GameplayStatics           | Récupère tous les BP\_SpawnZone\_C |
| **ForEachLoop**            | Macro Standard                     | Parcours chaque zone               |
| **IsZoneAvailable**        | Fonction dans BP\_SpawnZone\_C     | Vérifie si la zone est libre       |
| **AvailableZone (Output)** | BP\_SpawnZone\_C Référence d’objet | Zone disponible retournée          |

***

#### ✅ **Points forts**

1. **Recherche dynamique :**
   * Pas besoin de maintenir manuellement une liste des zones, le système utilise le monde pour récupérer toutes les instances.
2. **Sortie immédiate dès qu'une zone est trouvée :**
   * Optimise la boucle en évitant de parcourir toutes les zones inutilement.
3. **Modularité :**
   * La disponibilité est déléguée à **IsZoneAvailable**, rendant le système flexible (les critères peuvent évoluer dans le BP\_SpawnZone).

***

#### 🌟 **Suggestions d'amélioration possible**

1. **Gestion si aucune zone disponible :**
   * Ajouter une logique (par ex. un **PrintString** ou une valeur par défaut) si aucune zone n’est disponible à la fin du loop.
2. **Priorisation des zones :**
   * Si plusieurs zones sont disponibles, possibilité d’implémenter une priorité (via une variable **Priority** par exemple).
3. **Performance :**
   * Si le nombre de zones est très élevé, envisager de maintenir une liste locale et de l'actualiser uniquement lorsque nécessaire (plutôt que d’utiliser **GetAllActorsOfClass** à chaque appel).

***

#### 🏷️ **Résumé rapide**

| **Responsabilité principale** | Trouver et retourner une zone disponible pour le spawn |
| ----------------------------- | ------------------------------------------------------ |
| **Contrôle de conditions**    | Appel à IsZoneAvailable()                              |
| **Dépendances**               | BP\_SpawnZone\_C, IsZoneAvailable()                    |
| **Technologie utilisée**      | GetAllActorsOfClass, ForEachLoop, Function Result      |
| **Évolutions possibles**      | Gestion de fallback, priorisation des zones            |
