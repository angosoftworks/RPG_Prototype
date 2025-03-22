---
icon: gamepad-modern
---

# Dynamic Micro-Interaction System

### **1. Concept Overview**

**Titre :** Dynamic Micro-Interaction & Social Response System\
**Pitch :**\
Créer un système léger mais systémique permettant aux PNJ d’interagir dynamiquement avec le joueur via des **micro-interactions contextuelles** (ex : siffler un couple, bousculer quelqu’un, saluer un passant) tout en répercutant ces actions sur le comportement social du PNJ, ses relations, et l’état du quartier à court et long terme.

***

### **2. Objectives**

* **Créer un monde socialement réactif**, où chaque petite action du joueur peut déclencher une réaction unique.
* **Éviter la fadeur / répétitivité des PNJ** en imbriquant personnalité, relations, historique et environnement dans les réactions.
* **Favoriser la rejouabilité infinie** par des interactions non-scriptées, nourries par des variables systémiques.
* **Faire évoluer le monde en fonction des micro-actions**, influençant potentiellement la réputation du joueur, les relations PNJ, ou déclenchant des événements à plus grande échelle.

***

### **3. Core Components**

#### **A. PNJ Data Structure**

| Variable               | Description                                                       |
| ---------------------- | ----------------------------------------------------------------- |
| Traits de personnalité | Gentil ↔ Méchant, Courageux ↔ Peureux, Sociable ↔ Solitaire, etc. |
| Relationnel            | Liste des alliés, rivaux, famille (inter-PNJ network)             |
| Historique personnel   | Mémoire d’événements passés (bagarre, humiliation, aide)          |
| Besoins dynamiques     | Sécurité, richesse, vengeance, appartenance, etc.                 |
| Réputation locale      | Niveau d’opinion envers le joueur                                 |

***

#### **B. Déclencheurs d’interactions**

| Contexte                                          | Exemple d’interaction générée                |
| ------------------------------------------------- | -------------------------------------------- |
| Proximité d’un couple                             | Joueur siffle → Réaction du mec/fille        |
| Bousculade accidentelle                           | PNJ peut ignorer, insulter, confronter       |
| Saluer un PNJ seul                                | Peut saluer en retour, ignorer, ou provoquer |
| Passer dans une ruelle sombre d’un quartier chaud | PNJ peut essayer de détrousser ou fuir       |

Les interactions sont **déclenchées dynamiquement** selon :

* Proximité du joueur.
* Type et traits des PNJ présents.
* État général du quartier (dangerosité, stabilité, etc.).

***

#### **C. Réactions PNJ modulées par leurs couches comportementales**

| Facteur    | Impact sur la réaction                                |
| ---------- | ----------------------------------------------------- |
| Traits     | Peureux → Évite, Courageux → Confronte                |
| Relations  | Si en présence d'allié/famille → Se sent renforcé     |
| Historique | Si déjà humilié par joueur → Peut attaquer direct     |
| Besoins    | Si en besoin d’appartenance → Cherche à impressionner |
| Quartier   | Quartier instable → Comportement plus impulsif        |

***

#### **D. Réponses possibles du Joueur (Arborescence)**

À chaque interaction, le joueur peut choisir entre :

1. **Désamorcer (s’excuser, apaiser)**
2. **Ignorer (indifférence, peut agacer davantage)**
3. **Provoquer (escalade, bagarre, humiliation, intimidation)**

***

#### **E. Conséquences Systémiques**

Chaque interaction modifie des variables :

| Action du joueur                      | Conséquence immédiate / long terme                   |
| ------------------------------------- | ---------------------------------------------------- |
| Humilier un PNJ devant témoin         | Réputation locale négative, possibilité de vengeance |
| Aider un PNJ dans une zone dangereuse | Relations positives, missions futures possibles      |
| Provoquer bagarre avec témoin         | Intervention policière, tension accrue quartier      |
| Tuer un proche d’un autre PNJ         | Possible vendetta, influence sur relations           |

***

### **4. Example Flow: Siffler un Couple**

**Contexte :**

* Le joueur siffle en passant à côté d’un couple.

**PNJ Data :**

* **Homme** : Peureux (30), Loyal (80), Sociable (60)
* **Femme** : Dominante, Courageuse (70)

**Déroulement :**

1. La femme interpelle : "Tu vas pas laisser passer ça ?"
2. L’homme hésite → calcule les influences :
   * Il est peureux → tendance à éviter confrontation.
   * Loyal → motivé à agir sous pression de sa compagne.
   * Quartier = stable → peu de support de PNJ alentour.

**Réactions possibles du joueur :**

* S’excuser → la femme peut exprimer mépris, homme soulagé.
* Ignorer → tension augmente, l’homme peut craquer.
* Provoquer → il se lance maladroitement dans une confrontation.

**Conséquences :**

* Si le joueur l’humilie → réputation locale baisse, homme peut revenir plus tard accompagné.
* Si bagarre → intervention police, voisins réagissent.
* Si le joueur le laisse partir → peut débloquer une mission plus tard (le mec voulant laver son honneur).

***

### **5. Scalabilité & Rejouabilité**

* Les **templates d’interactions** sont modulaires (provocation, aide, moquerie, vol, etc.).
* Chaque nouvelle interaction possible est **déployée dans toutes les zones**, et varie naturellement grâce aux couches comportementales.
* Le joueur **ne voit jamais deux fois exactement la même situation**, car les PNJ évoluent :
  * Différentes relations.
  * Historique différent.
  * Quartier différent.
  * Choix du joueur antérieurs impactant la réaction.

***

### **6. Bonus Features**

* **Propagation sociale :** Un PNJ témoignant d’une humiliation ou d’un geste héroïque peut en parler → impact sur réputation dans le quartier.
* **Chain Reactions :** Un simple sifflement peut enclencher une vendetta, influencer d’autres factions/PNJ.
* **Integration avec macro-systèmes :** Interactions locales participent à faire évoluer dangerosité, stabilité du quartier.

***

### **7. Deliverables Prioritaires**

| Système                        | Statut requis pour MVP                                   |
| ------------------------------ | -------------------------------------------------------- |
| PNJ Traits & Relations         | Implémentation basique (3-5 traits, 2-3 relations types) |
| Déclencheur d’interaction      | Système proximity + trigger contextuel                   |
| Arborescence de réponse joueur | 3 options minimales (désamorcer, ignorer, provoquer)     |
| Conséquences directes          | Simple réputation locale + réaction PNJ immédiate        |
| Historique PNJ                 | Enregistrement des humiliations, aides, vengeances       |
| Quartier impact                | Influence mineure sur dangerosité pour test              |
