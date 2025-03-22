---
icon: gamepad-modern
---

# Procédural Story-Driven Open World

### 🏹 **Nom de code : "Living Lore"**

***

### 1️⃣ **Pitch Résumé**

Créer un monde ouvert où la **trame principale est écrite et fixée**, mais tout le reste (l'histoire du monde, les factions, les PNJ, les lieux secondaires) est **généré procéduralement en cohérence avec cette trame principale**.

**Idée clé :**

> On part d'un squelette narratif (quêtes principales) + "slots réservés", et on construit un monde dynamique, crédible et différent à chaque partie autour de cet axe.

***

### 2️⃣ **Pipeline Global**

#### **Étape 1 : Définition des éléments fixes**

* **Trame principale** :
  * Scénario principal écrit manuellement.
  * Personnages centraux définis.
  * Événements majeurs clés.
* **Slots géographiques réservés** :
  * Capitales, donjons majeurs, forêts sacrées, lieux critiques.
  * Chaque slot a des **assets prédéfinis**, adaptables visuellement selon le contexte secondaire.

***

#### **Étape 2 : Génération des trames secondaires (World History Generator)**

* Simulation d’une **timeline historique** :
  * Guerres.
  * Factions montantes et déchues.
  * Alliances et trahisons.
  * Catastrophes naturelles ou magiques.
  * Dynasties PNJ (héritages, assassinats, mariages...).
* **PNJ secondaires & factions** créés dynamiquement :
  * Chaque PNJ a une origine, des traits de personnalité, des objectifs.
  * Relations inter-factions définies.

***

#### **Étape 3 : World Geography Generation**

* **Positionnement des villages, châteaux, routes, ruines** influencé par :
  * Histoire secondaire simulée (ex: ancienne bataille = ruines à cet endroit).
  * Terrains logiques : rivières, montagnes.
* **Respect des slots fixes :**
  * Les zones réservées restent intactes pour accueillir les éléments du scénario principal.
  * Option : adapter esthétiquement ces zones selon les factions dominantes alentours.

***

#### **Étape 4 : Environmental Dressing & Assets Injection**

* Les décors sont "habillés" selon le contexte :
  * Architecture influencée par les factions locales.
  * Décorations, graffitis, ruines, monuments liés aux événements secondaires.
  * PNJ secondaires répartis avec routines dynamiques.

***

#### **Étape 5 : Quest Injection**

* Les **quêtes secondaires** sont générées en fonction de l’histoire simulée :
  * Vengeance d’une famille ruinée.
  * Quête politique entre factions rivales créées procéduralement.
  * Recherche d’un artefact perdu durant une guerre simulée.

***

***

### 3️⃣ **Visuel du Pipeline**

```
scssCopierModifier┌──────────────────────────────┐
│     Trame principale fixe     │
│  (scénario, lieux clés slots) │
└──────────────┬───────────────┘
               │
               ▼
┌───────────────────────────────────────────┐
│  Génération trames secondaires & PNJ      │
│  (historiques, guerres, factions, dynasties) │
└──────────────┬────────────────────────────┘
               │
               ▼
┌──────────────────────────────────────────────────┐
│   Génération géographique (villages, routes...)   │
│     Respect des slots fixes                      │
└──────────────┬──────────────────────────────────┘
               │
               ▼
┌────────────────────────────────────────┐
│ Habillage esthétique & placement assets│
│ Selon factions, événements secondaires │
└──────────────┬─────────────────────────┘
               │
               ▼
┌─────────────────────────────────────┐
│  Insertion quêtes secondaires dynamiques │
│   liées aux trames secondaires          │
└─────────────────────────────────────┘
```

***

### 4️⃣ **Exemples Concrets**

#### **Exemple de génération :**

1. **Trame principale** :
   * Le joueur doit empêcher un culte ancien de ressusciter une divinité.
   * Le temple final est un slot fixe.
2. **Trames secondaires générées :**
   * Faction A a conquis la région il y a 50 ans.
   * Une famine a mené à un exode vers le sud.
   * Un roi a été assassiné, créant une guerre civile.
3. **Impact sur le monde :**
   * La ville proche du temple est sous contrôle militaire.
   * Ruines et villages abandonnés jonchent les routes.
   * Certains PNJ t'en veulent à cause des actions d’une faction que tu rencontres.
4. **Quête secondaire :**
   * Un PNJ veut récupérer un artefact dans une ruine issue d’une ancienne bataille générée dynamiquement.

***

### 5️⃣ **Tech Stack & Technologies Possibles :**

* **World History Generator :**
  * Système inspiré de Dwarf Fortress / Crusader Kings simulations (simplifié).
* **Geography Generator :**
  * Noise-based terrain generation (Perlin, Voronoi), mais modifié selon les besoins narratifs.
* **Slot System :**
  * Zones "reserved" avec balises (comme des "anchor points").
* **Asset Dressing System :**
  * Pools d'assets modifiables (architecture, décos) selon factions/events.
* **Quest Generator :**
  * Rule-based system + optional LLM integration for richer dynamic dialogue/quests.

***

### 6️⃣ **Pourquoi ce système est puissant :**

| **Avantage**                      | **Impact**                                         |
| --------------------------------- | -------------------------------------------------- |
| Trame principale contrôlée        | Pas de risque de scénario cassé                    |
| Monde secondaire dynamique        | Chaque partie est unique                           |
| Sentiment de cohérence historique | Les environnements sont "le produit" des histoires |
| Rejouabilité + immersion          | Pas juste visuel, mais logique et narratif         |
