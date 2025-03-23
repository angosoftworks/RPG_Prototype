---
layout:
  title:
    visible: true
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# BP\_SpawnZone

### Paramètres de classe

```json
{
  "Blueprint": {
    "Name": "BP_SpawnZone",
    "ParentClass": "Actor",
    "AdvancedOptions": {
      "Deprecated": false,
      "GenerateConstClass": false,
      "GenerateAbstractClass": false,
      "ShouldCookPropertyGuides": "Inherit"
    },
    "BlueprintOptions": {
      "RunConstructionScriptOnDrag": true,
      "RunConstructionScriptInSequence": false,
      "DisplayName": "",
      "Description": "",
      "Namespace": "",
      "Category": "",
      "HideCategories": []
    },
    "Interfaces": {
      "ImplementedInterfaces": [
        "BPI_SpawnZone"
      ],
      "InheritedInterfaces": []
    },
    "Imports": {
      "DefaultNamespaces": [],
      "ImportedNamespaces": []
    },
    "Variables": [],
    "Functions": [],
    "Events": []
  }
}

```

### Valeurs par défaut de classe

```json
{
  "BlueprintClass": "BP_SpawnZone",
  "Defaults": {
    "MaxActorsInZone": 0,
    "IsZoneEnabled": true,
    "CooldownOver": true
  },
  "TickSettings": {
    "StartWithTickEnabled": true,
    "TickInterval": 0.0,
    "AllowTickBeforeBeginPlay": false,
    "TickEvenWhenPaused": false,
    "AllowTickOnDedicatedServer": true,
    "TickGroup": "PrePhysics"
  },
  "Replication": {
    "OnlyRelevantToOwner": false,
    "AlwaysRelevant": false,
    "ReplicateMovement": false,
    "NetLoadOnClient": true,
    "NetUseOwnerRelevancy": false,
    "Replicates": false,
    "NetDormancy": "Awake",
    "NetCullDistanceSquared": 225000000.0,
    "NetUpdateFrequency": 100.0,
    "MinNetUpdateFrequency": 2.0,
    "NetPriority": 1.0,
    "PhysicsReplicationMode": "Default",
    "CallPreReplication": true,
    "CallPreReplicationForReplay": false,
    "ReplayRewindable": false
  },
  "Rendering": {
    "ActorHiddenInGame": false,
    "EditorBillboardScale": 1.0
  },
  "Collision": {
    "GenerateOverlapEventsDuringStreaming": false,
    "UpdateOverlapsMethodDuringStreaming": "UseConfigDefault",
    "RelevantForLevelBounds": true
  },
  "Actor": {
    "CanBeDamaged": true,
    "InitialLifeSpan": 0.0,
    "SpawnCollisionHandling": "AlwaysSpawnIgnoreCollisions",
    "FindCameraComponentWhenViewTarget": true
  },
  "HLOD": {
    "IncludeActorInHLOD": true
  },
  "Physics": {
    "AsyncPhysicsTickEnabled": false
  },
  "WorldPartition": {
    "IsSpatiallyLoaded": true
  },
  "DataLayers": {
    "ExternalDataLayerAsset": null
  }
}

```

### Graphiques

#### EventGraph

```json
{
  "Blueprint": "BP_SpawnZone",
  "EventGraph": [
    {
      "Event": "ReceiveBeginPlay",
      "ParentClass": "Actor",
      "OverrideFunction": true,
      "Enabled": false,
      "Comment": "Ce nœud est désactivé et ne sera pas appelé. Faites glisser les broches pour générer des fonctionnalités.",
      "Pins": [
        {
          "Name": "OutputDelegate",
          "Type": "delegate",
          "Direction": "output"
        },
        {
          "Name": "then",
          "Type": "exec",
          "Direction": "output"
        }
      ]
    },
    {
      "Event": "ReceiveActorBeginOverlap",
      "ParentClass": "Actor",
      "OverrideFunction": true,
      "Enabled": false,
      "PositionY": 208,
      "Comment": "Ce nœud est désactivé et ne sera pas appelé. Faites glisser les broches pour générer des fonctionnalités.",
      "Pins": [
        {
          "Name": "OutputDelegate",
          "Type": "delegate",
          "Direction": "output"
        },
        {
          "Name": "then",
          "Type": "exec",
          "Direction": "output"
        },
        {
          "Name": "OtherActor",
          "Type": "object",
          "SubType": "Actor",
          "Direction": "output",
          "Tooltip": "Other Actor - Acteur Référence d'objet"
        }
      ]
    },
    {
      "Event": "ReceiveTick",
      "ParentClass": "Actor",
      "OverrideFunction": true,
      "Enabled": false,
      "PositionY": 416,
      "Comment": "Ce nœud est désactivé et ne sera pas appelé. Faites glisser les broches pour générer des fonctionnalités.",
      "Pins": [
        {
          "Name": "OutputDelegate",
          "Type": "delegate",
          "Direction": "output"
        },
        {
          "Name": "then",
          "Type": "exec",
          "Direction": "output"
        },
        {
          "Name": "DeltaSeconds",
          "Type": "float",
          "Direction": "output",
          "Default": "0.0",
          "Tooltip": "Delta Seconds - Float (simple précision)"
        }
      ]
    }
  ]
}

```

### Fonctions

#### Construction Script

```json
{
  "Function": "UserConstructionScript",
  "ParentClass": "Actor",
  "Type": "FunctionEntry",
  "Access": "Public",
  "Pure": false,
  "CompactNodeTitle": null,
  "CallInEditor": false,
  "Inputs": [],
  "Outputs": [
    { "Type": "exec", "Name": "then" }
  ],
  "Notes": "Construction Script spécifique aux Actors, appelé lors de la construction de l'acteur."
}
```

#### GetRandomPointInZone

```json
{
  "Function": "GetRandomPointInZone",
  "Access": "Public",
  "Pure": false,
  "Category": "Par défaut",
  "Inputs": [],
  "Outputs": [
    {
      "Name": "Vector",
      "Type": "Vector"
    }
  ],
  "Logic": [
    "Get Variable: Box (BoxComponent)",
    "BoxComponent::GetScaledBoxExtent → Box Extent (Vector)",
    "SceneComponent::K2_GetComponentLocation → Box Location (Vector)",
    "BreakVector(Box Extent) → X, Y, Z",
    "Multiply X, Y, Z by -1 → Negative Extents",
    "RandomFloatInRange(X Min, X Max), Y, Z",
    "MakeVector(X, Y, Z)",
    "Add(MakeVector, Box Location)",
    "Return Vector"
  ]
}
```

#### StartSpawnLoop

```json
{
  "Function": {
    "Name": "IsZoneAvailable",
    "Type": "Pure",
    "AccessSpecifier": "Public",
    "Category": "Par défaut",
    "Output": {
      "Name": "IsAvailable",
      "Type": "bool",
      "DefaultValue": true
    },
    "Logic": [
      {
        "Get": "SpawnedActorsInZone",
        "Type": "Array<Actor>"
      },
      {
        "CallFunction": "Array_Length",
        "Input": "SpawnedActorsInZone",
        "Output": "NumSpawnedActors"
      },
      {
        "Get": "MaxActorsInZone",
        "Type": "int"
      },
      {
        "Operation": "Less",
        "Inputs": ["NumSpawnedActors", "MaxActorsInZone"],
        "Output": "IsUnderMax"
      },
      {
        "Get": "bIsZoneEnabled",
        "Type": "bool"
      },
      {
        "Get": "bCooldownOver",
        "Type": "bool"
      },
      {
        "Operation": "BooleanAND",
        "Inputs": ["IsUnderMax", "bIsZoneEnabled", "bCooldownOver"],
        "Output": "IsAvailable"
      }
    ]
  }
}
```

### Variables

#### Box

```json
{
  "Variable": {
    "Name": "Box",
    "Type": "UBoxComponent",
    "Category": "Default",
    "ExposeToCinematics": true,
    "Visibility": "VisibleAnywhere",
    "AdvancedProperties": [
      "BlueprintVisible",
      "ZeroConstructor",
      "InstancedReference",
      "NonTransactional",
      "NoDestructor",
      "HasGetValueTypeHash"
    ],
    "DefaultValue": "None",
    "EventsAvailable": [
      "OnComponentHit",
      "OnComponentBeginOverlap",
      "OnComponentEndOverlap",
      "OnComponentWake",
      "OnComponentSleep",
      "OnComponentPhysicsStateChanged",
      "OnBeginCursorOver",
      "OnEndCursorOver",
      "OnClicked",
      "OnReleased",
      "OnInputTouchBegin",
      "OnInputTouchEnd",
      "OnInputTouchEnter",
      "OnInputTouchLeave",
      "PhysicsVolumeChanged",
      "OnComponentActivated",
      "OnComponentDeactivated"
    ]
  }
}

```

#### DefaultSceneRoot

```json
{
  "Variable": {
    "Name": "DefaultSceneRoot",
    "Type": "SceneComponent*",
    "Access": "Private",
    "Category": "Default",
    "CinematicExposure": false,
    "DefaultValue": "None",
    "PropertyFlags": [
      "BlueprintVisible",
      "ZeroConstructor",
      "InstancedReference",
      "NonTransactional",
      "NoDestructor",
      "HasGetValueTypeHash"
    ],
    "Events": [
      "OnPhysicsVolumeChanged",
      "OnComponentActivated",
      "OnComponentDeactivated"
    ]
  }
}

```

#### MaxActorsInZone

```json
{
  "VariableName": "MaxActorsInZone",
  "Type": "int",
  "FriendlyName": "Max Actors in Zone",
  "Category": "Default",
  "Tooltip": "Nombre max d’acteurs autorisés dans la zone",
  "Access": "Private",
  "InstanceEditable": false,
  "BlueprintReadOnly": false,
  "ExposeOnSpawn": false,
  "ExposeToCinematic": false,
  "Replication": "None",
  "ReplicationCondition": "None",
  "DefaultValue": 0,
  "AdvancedOptions": {
    "Config": false,
    "Transient": false,
    "SaveGame": false,
    "Deprecated": false
  },
  "EditorFlags": {
    "CPF_Edit": true,
    "CPF_BlueprintVisible": true,
    "CPF_ZeroConstructor": true,
    "CPF_DisableEditOnInstance": true,
    "CPF_IsPlainOldData": true,
    "CPF_NoDestructor": true,
    "CPF_HasGetValueTypeHash": true
  }
}
```

#### SpawnedActorsInZone

```json
{
  "Variable": "SpawnedActorsInZone",
  "Type": "Array of Actor",
  "Access": "Public",
  "BlueprintExposure": {
    "EditableInEditor": true,
    "VisibleInBlueprint": true,
    "ExposeOnSpawn": false,
    "ReadOnly": false
  },
  "EditableOn": {
    "Template": false,
    "Instance": false
  },
  "Replication": "None",
  "Category": "Default",
  "Tooltip": "Liste des acteurs déjà spawn dans cette zone",
  "DefaultValue": "Empty Array",
  "AdvancedFlags": {
    "Transient": false,
    "SaveGame": false,
    "Deprecated": false
  }
}
```

#### bIsZoneEnabled

```json
{
  "Variable": "bIsZoneEnabled",
  "Type": "Bool",
  "FriendlyName": "Is Zone Enabled",
  "Category": "Default",
  "Access": "Public",
  "Editable": true,
  "ReadOnly": false,
  "ExposeOnSpawn": false,
  "ExposeToCinematic": false,
  "Replication": "None",
  "ReplicationCondition": "None",
  "AdvancedFlags": [
    "CPF_Edit",
    "CPF_BlueprintVisible",
    "CPF_ZeroConstructor",
    "CPF_DisableEditOnInstance",
    "CPF_IsPlainOldData",
    "CPF_NoDestructor",
    "CPF_HasGetValueTypeHash"
  ],
  "DefaultValue": true
}
```

#### bCooldownOver

```json
{
  "Variable": "bCooldownOver",
  "Type": "Bool",
  "FriendlyName": "Cooldown Over",
  "DefaultValue": true,
  "Category": "Default",
  "AccessSpecifier": "Public",
  "Replication": "None",
  "Description": "",
  "Editable": false,
  "BlueprintReadOnly": false,
  "ExposeOnSpawn": false,
  "ExposeToCinematics": false,
  "Advanced": {
    "Config": false,
    "Transient": false,
    "SaveGame": false,
    "Obsolete": false
  },
  "PropertyFlags": [
    "CPF_Edit",
    "CPF_BlueprintVisible",
    "CPF_ZeroConstructor",
    "CPF_DisableEditOnInstance",
    "CPF_IsPlainOldData",
    "CPF_NoDestructor",
    "CPF_HasGetValueTypeHash"
  ]
}
```
