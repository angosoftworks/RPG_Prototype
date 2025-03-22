---
icon: gamepad-modern
---

# Dynamic Zone Ecosystem System

### **1. Concept Overview**

**Titre :** Dynamic Zone Danger & Social Ecosystem\
**Pitch :**\
Créer un monde composé de **zones autonomes** (quartiers, districts, villages) possédant des statistiques dynamiques influencées par les actions des PNJ, les événements aléatoires, et les interventions du joueur. Chaque zone évolue indépendamment, pouvant devenir prospère ou chaotique, et influençant la vie, les comportements et les missions disponibles dans ces zones.

***

### **2. Objectives**

* **Créer un écosystème systémique où chaque quartier/zones a sa propre "vie".**
* Les zones peuvent **se détériorer ou prospérer** sans intervention.
* Influencer directement :
  * **Types de PNJ présents.**
  * **Événements dynamiques.**
  * **Missions proposées.**
  * **Migration et comportement des PNJ.**
* Offrir au joueur la possibilité d’interagir avec ce système : **empirer la situation ou stabiliser la zone.**
* Possibilité d’atteindre des **seuils critiques déclenchant des événements massifs** (ex : intervention militaire, lockdown, émeutes).

***

### **3. Core Components**

#### **A. Zone Variables (par quartier)**

| Variable                   | Description                                               |
| -------------------------- | --------------------------------------------------------- |
| Dangerosité (%)            | Niveau de criminalité, influence événements violents      |
| Population criminelle (%)  | Proportion de criminels présents                          |
| Stabilité économique (%)   | Richesse, ouverture commerces, qualité de vie             |
| Présence policière (%)     | Contrôle du quartier, influence immédiate sur dangerosité |
| Moral / Sentiment social   | Bien-être général, humeur des PNJ                         |
| Réputation du joueur local | Perception du joueur par la population locale             |

***

#### **B. Zone Evolution Logic**

**Les variables évoluent uniquement par événements déclencheurs, pas par timer arbitraire.**

| Événement                                 | Impact immédiat sur Zone                                           |
| ----------------------------------------- | ------------------------------------------------------------------ |
| Fusillade / Bagarre                       | +1-5% Dangerosité, +1% Population criminelle                       |
| Cambriolage réussi                        | +2% Dangerosité, -2% Stabilité économique                          |
| Intervention policière réussie            | -3% Dangerosité, +5% Présence policière                            |
| Missions de nettoyage / actions positives | -10% Dangerosité, +10% Stabilité                                   |
| Joueur commet crime répété                | +5% Dangerosité, impact réputation                                 |
| PNJ criminels migrent                     | +5% Population criminelle                                          |
| Aucun événement majeur pendant X minutes  | Aucun effet (tu choisis de ne PAS faire de décrémentation passive) |

***

#### **C. Seuils Critiques & Événements Massifs**

| Variable                    | Seuil Critique                                                   | Effet déclenché |
| --------------------------- | ---------------------------------------------------------------- | --------------- |
| Dangerosité > 80%           | Quartier passe en Zone Rouge                                     |                 |
| Population Criminelle > 70% | Disparition des commerces, policiers absents, PNJ civils fuient  |                 |
| Dangerosité > 95%           | Intervention militaire, lockdown du quartier, missions spéciales |                 |

***

### **4. Zone Influence on PNJ**

Les PNJ adaptent leur comportement et migration selon l’état du quartier :

| Zone State               | PNJ Behavior                                  |
| ------------------------ | --------------------------------------------- |
| Dangerosité élevée       | PNJ violents apparaissent, civils fuient      |
| Stabilité forte          | PNJ civils et commerçants affluent            |
| Présence policière forte | PNJ criminels moins présents                  |
| Joueur mal vu            | PNJ refusent d’interagir, commerçants ferment |

**Les PNJ peuvent aussi être "attirés" ou "repoussés" selon leurs traits :**

* Un PNJ méchant → attiré par zones chaotiques.
* Un PNJ sociable → fuit les zones en ruine.

***

### **5. Zone Impact on Dynamic Missions**

L’état du quartier influence directement les quêtes proposées :

| Zone State         | Possible Missions Générées                                        |
| ------------------ | ----------------------------------------------------------------- |
| Quartier prospère  | Opportunités criminelles (vol, racket)                            |
| Quartier dégradé   | Missions de nettoyage (gangs, émeutes)                            |
| Zone Rouge         | Quêtes spéciales : évacuer civils, infiltrer gangs                |
| Lockdown militaire | Missions pour briser les checkpoints, collaboration avec factions |

***

### **6. Propagation & Systemic Pressure**

Les zones **influencent les quartiers voisins** :

* Quartier A (Zone Rouge) → peut faire augmenter la Dangerosité de Quartier B.
* Les migrations PNJ peuvent déséquilibrer les zones paisibles.
* La pression sociale pousse certains PNJ à changer de comportement (un PNJ civil pacifique peut devenir délinquant après avoir survécu trop longtemps en zone rouge).

***

### **7. World Feedback Loop**

| Action                          | Immediate Result                                   | Long-term Systemic Impact                     |
| ------------------------------- | -------------------------------------------------- | --------------------------------------------- |
| Joueur nettoie quartier         | Dangerosité baisse                                 | Plus de civils, commerces rouvrent            |
| Joueur ignore quartier en ruine | Dangerosité monte, intervention militaire possible | PNJ fuient ou deviennent criminels            |
| Quartier dépasse seuil critique | Lockdown militaire, missions spéciales             | Réputation globale affectée, gameplay modifié |

***

### **8. Optional: Memory & NPC Commentary**

Les PNJ et médias peuvent **se souvenir** des événements majeurs d’un quartier :

* Radio / PNJ discussions ("Tu te souviens quand ils ont dû envoyer l’armée à Easttown ?").
* Certains PNJ peuvent refuser d’aller vivre/travailler dans un quartier avec une mauvaise réputation même après reset.

***

### **9. Deliverables Prioritaires (MVP)**

| Feature                           | Implementation Goal                                   |
| --------------------------------- | ----------------------------------------------------- |
| Zone Variables                    | Implémentation complète avec seuils et interrelations |
| Event Impact Logic                | Lien événement → modification des stats               |
| Seuils Critiques & Lockdown Logic | Système de seuils et intervention spéciale            |
| PNJ Migration Behavior            | PNJ déplacés/mutés selon état du quartier             |
| Dynamic Mission Integration       | Simple mission templates conditionnels                |
| Player Feedback                   | Notification système + réactions PNJ locales          |

***

## **Conclusion:**

**Ce système remplace le besoin de designer manuellement la difficulté ou le contenu de chaque quartier.**\
Il garantit un monde **évolutif, cohérent et unique à chaque partie**, capable de produire des cycles :

1. **Calme → Montée du chaos → Climax → Reset possible → Mémoire du chaos.**
