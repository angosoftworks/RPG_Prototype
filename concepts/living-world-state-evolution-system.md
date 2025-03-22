---
icon: gamepad-modern
---

# Living World State Evolution System

### 1️⃣ **Pitch Résumé**

Créer un monde vivant, cohérent et riche, basé sur une **trame principale fixe**, dans lequel chaque élément du monde (villages, forêts, factions, PNJ) évolue dynamiquement au fil du temps via un système d’**états persistants**.

Le système génère plusieurs décennies/siècles d’histoire avant l’entrée en jeu, garantissant :

* **Cohérence historique**.
* **Absence de contradictions ou d’événements aléatoires absurdes**.
* Une **réactivité crédible du monde** face aux événements majeurs et secondaires.

***

### 2️⃣ **Objectifs**

* **Combiner narration maîtrisée et génération procédurale profonde**.
* Assurer la **logique d’évolution du monde** (chaque changement visible a une cause historique).
* **Rejouabilité** avec des variantes à chaque partie, tout en respectant les éléments clés de la trame principale.
* Créer des **PNJ, factions, lieux riches d’un passé historique unique** à chaque partie.

***

### 3️⃣ **Composants principaux**

#### **A. Trame principale (Fixed Story Spine)**

* Définie à la main : événements clés, personnages majeurs, lieux critiques.
* Certains **slots géographiques ou historiques réservés**.
* Ces éléments restent constants entre parties.

***

#### **B. World Elements with States**

Chaque élément du monde (ville, forêt, faction, PNJ, lieu) possède :

| Composant               | Description                                                                           |
| ----------------------- | ------------------------------------------------------------------------------------- |
| **Unique ID**           | Identifiant                                                                           |
| **Type**                | Ex : Village, Forêt, Faction, PNJ                                                     |
| **Current State**       | État actuel (ex : prospère, ruiné, rasé, conquis)                                     |
| **Possible States**     | Liste d'états possibles avec transitions                                              |
| **State History**       | Historique complet des états + dates                                                  |
| **Tags / Metadata**     | Influence culturelle, ressources, traits (ex : “religious hub”, “former battlefield”) |
| **Control / Ownership** | Qui contrôle le lieu ou le PNJ (faction, famille)                                     |

***

#### **C. State Machines**

Chaque type d’élément dispose d’un **graph de transitions d’état prédéfini** :

**Exemple pour un Village :**

| From State      | Event Trigger               | To State        |
| --------------- | --------------------------- | --------------- |
| Forest          | Settlement founded          | Small Village   |
| Small Village   | Economic growth, peace      | Prosperous Town |
| Prosperous Town | War, plague, famine         | Ruins           |
| Ruins           | Recolonization, new faction | Small Village   |

***

#### **D. Historical Simulation Engine**

* Simule **des siècles d’histoire** avant l’entrée du joueur :
  * Croissance démographique, guerres, alliances, catastrophes, migrations.
  * Application de règles générales mais influencées par la trame principale.
  * Chaque événement potentiellement déclencheur de **state transitions**.

***

#### **E. Event System & Hooks**

* Événements (batailles, trahisons, catastrophes) impactent les éléments du monde.
* Certains événements liés directement au **scénario principal**.
* D'autres événements **proc-générés** affectent les transitions des éléments dynamiquement.

***

#### **F. World Memory System**

* Tout événement ou changement de state est **consigné**.
* Accessible par les systèmes de quêtes, dialogues, comportements PNJ.
* Permet des quêtes secondaires générées basées sur l’historique réel du monde.

***

### 4️⃣ **Pipeline**

#### **Step 1 : Input**

* Trame principale fixée + slots géographiques définis.
* Templates des types d’éléments (villages, factions, PNJ).

***

#### **Step 2 : Initial World Build**

* Placement initial des forêts, villes, factions, ressources.
* Chaque élément possède un état initial (Forêt vierge, Clan naissant, etc.).

***

#### **Step 3 : Historical Simulation**

* Tick par tick (année ou décennie) :
  * Application des règles : croissance, guerres, dynasties.
  * Transition des states selon triggers.
  * Factions conquièrent ou disparaissent.
  * Villages prospèrent ou sont rasés.
  * PNJ changent de rôle (soldat → chef de faction → mort/exilé).

***

#### **Step 4 : Consistency Enforcement**

* Slots du scénario principal sont vérifiés et respectés :
  * Les lieux clés existent toujours, mais peuvent avoir des variations (prospérité, contrôle).

***

#### **Step 5 : Game Start**

* Le joueur entre dans un monde riche, logique, cohérent.
* Chaque village, ruine, faction et PNJ a un **passé traçable**.

***

#### **Step 6 : Quest & Content Generation**

* Utilisation du **World Memory** pour créer des quêtes secondaires :
  * Vengeance d'un PNJ dont le village a été rasé il y a 30 ans.
  * Rumeurs d'une ancienne guerre ayant laissé des artefacts.
  * Factions encore marquées par des guerres ou alliances passées.

***

### 5️⃣ **Visual Example – Village State Machine**

```
[Forest] 
   ↓ (Settlement Founded)
[Small Village]
   ↓ (Economic Boom / Peace)
[Prosperous Town]
   ↓ (War / Famine)
[Ruins]
   ↘ (New settlers)
[Small Village] 
```

***

### 6️⃣ **Technological Implementation**

| Component          | Possible Tech                                                                    |
| ------------------ | -------------------------------------------------------------------------------- |
| Data-Driven Config | JSON, YAML, database for all world elements, state transitions                   |
| Simulation Engine  | Custom procedural simulation loop (could be Python prototype → C++/C# in engine) |
| Graph Storage      | Graph Database (Neo4j) or in-memory graph                                        |
| Asset Swapping     | Unreal/Unity integration, state-driven prefabs/assets                            |
| Quest Hooks        | Rule-based system + optional LLM for dynamic dialogue                            |

***

### 7️⃣ **Advantages**

| Feature                          | Benefit                                                          |
| -------------------------------- | ---------------------------------------------------------------- |
| **State-based evolution**        | Cohérence forte, logique temporelle                              |
| **Historical simulation**        | Profondeur & richesse du monde                                   |
| **Control via trame principale** | Pas de casse scénaristique, slots réservés                       |
| **Rejouabilité infinie**         | Même trame principale, mondes différents                         |
| **Narrative integration**        | PNJ, factions et quêtes émergent naturellement du passé du monde |

***

### 8️⃣ **Potential Expansion**

* Moddable templates → permettre aux joueurs/développeurs de créer leurs propres timelines et factions.
* Plugging procedural story generation (LLMs, planners) to create complex emergent quests from world memory.
* Persistent world across multiple games (meta-simulation).
