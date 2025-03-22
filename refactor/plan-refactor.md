# Plan refactor

#### **1. Découpage du BP\_Manager**

* **BP\_SpawnManager** → Uniquement responsable du spawn/despawn.
* **BP\_DataManager** → Charge et fournit les DataTables/Structs.
* **BP\_RelationManager** → Gère les relations PNJ/Player.
* Le BP\_Manager principal orchestre uniquement les sous-managers.

***

#### **2. Intégration d’un Pooling System**

* Créer un **BP\_ActorPool** :
  * Réutilisation des PNJs existants.
  * Réduction du coût CPU/GPU.

***

#### **3. Modularisation des Spawn Zones**

* Créer des **BP\_SpawnZone Actors indépendants** :
  * Variables exposées : SpawnType, Radius, MaxActors.
  * Debug visuel via `DrawDebug` dans ConstructionScript.

***

#### **4. Optimisation Editor/Debug**

* Ajouter des **Editor Utilities Widgets** pour contrôle des spawn zones & PNJs.
* Possibilité de toggle les zones, voir leurs états en temps réel.

***

#### **5. Future-Proof : Async & Streaming Support**

* Déporter les charges lourdes du BeginPlay :
  * Utiliser des **Async Loading** pour Data.
  * Adapter au World Partition (spawn zones streamables).
