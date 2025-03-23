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

# BP\_SpawnManager

### Paramètres de classe

```json
{
  "Blueprint": "BP_SpawnManager",
  "ParentClass": "AActor",
  "RunConstructionScriptOnDrag": true,
  "RunConstructionScriptInSequencer": false,
  "Namespace": null,
  "Category": null,
  "Interfaces": [],
  "HideCategories": [],
  "AdvancedOptions": {
    "Deprecated": false,
    "GenerateConstClass": false,
    "GenerateAbstractClass": false,
    "ShouldCookPropertyGuides": "Inherit"
  },
  "Imports": []
}

```

### Valeurs par défaut de classe

```json
{
  "Blueprint": "BP_SpawnManager",
  "ParentClass": "AActor",
  "DefaultParameters": {
    "MaxSpawnedActors": 0,
    "SpawnInterval": 0.0,
    "ActorToSpawn": "None",
    "UsePooling": false
  },
  "Tick": {
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
    "ReplicatedMovement": {
      "LocationQuantizationLevel": "RoundWholeNumber",
      "VelocityQuantizationLevel": "RoundWholeNumber",
      "RotationQuantizationLevel": "ByteComponents"
    }
  },
  "Rendering": {
    "ActorHiddenInGame": false,
    "EditorBillboardScale": 1.0,
    "RelevantForLevelBounds": true
  },
  "Collision": {
    "GenerateOverlapEventsDuringLevelStreaming": false,
    "UpdateOverlapsMethodDuringLevelStreaming": "UseConfigDefault",
    "DefaultUpdateOverlapsMethodDuringLevelStreaming": "OnlyUpdateMovable"
  },
  "Actor": {
    "CanBeDamaged": true,
    "InitialLifeSpan": 0.0,
    "SpawnCollisionHandlingMethod": "AlwaysSpawnIgnoreCollisions",
    "FindCameraComponentWhenViewTarget": true,
    "IgnoresOriginShifting": false,
    "CanBeInCluster": false,
    "PivotOffset": [0.0, 0.0, 0.0]
  },
  "Input": {
    "BlockInput": false,
    "AutoReceiveInput": "Disabled",
    "InputPriority": 0
  },
  "HLOD": {
    "IncludeActorInHLOD": true,
    "HLODLayer": "None"
  },
  "Physics": {
    "AsyncPhysicsTickEnabled": false
  },
  "Events": [
    "OnTakeAnyDamage", "OnTakePointDamage", "OnTakeRadialDamage",
    "OnActorBeginOverlap", "OnActorEndOverlap", "OnBeginCursorOver",
    "OnEndCursorOver", "OnClicked", "OnReleased", "OnInputTouchBegin",
    "OnInputTouchEnd", "OnInputTouchEnter", "OnInputTouchLeave",
    "OnActorHit", "OnDestroyed", "OnEndPlay"
  ],
  "LevelInstance": {
    "IsMainWorldOnly": false
  },
  "Preparation": {
    "IsEditorOnlyActor": false,
    "GenerateOptimizedBlueprint": false
  },
  "WorldPartition": {
    "RuntimeGrid": "None",
    "IsSpatiallyLoaded": true
  },
  "DataLayers": {
    "DataLayers": [],
    "DataLayerAssets": [],
    "ExternalDataLayerAsset": "None"
  }
}
```

### Composants

#### DefaultSceneRoot

```json
{
  "Component": {
    "Name": "DefaultSceneRoot",
    "Type": "SceneComponent",
    "Category": "Composants",
    "EditableWhenInherited": true,
    "Mobility": "Mobile",
    "Scale": [1.0, 1.0, 1.0],
    "Visibility": {
      "Visible": true,
      "HiddenInGame": false
    },
    "Tick": {
      "StartWithTickEnabled": true,
      "TickInterval": 0.0,
      "TickGroup": "DuringPhysics",
      "TickOnDedicatedServer": true,
      "TickEvenWhenPaused": false
    },
    "LOD": {
      "DetailMode": "Low"
    },
    "Physics": {
      "ShouldUpdatePhysicsVolume": false
    },
    "Navigation": {
      "CanAffectNavigation": false
    },
    "Replication": {
      "ReplicateUsingRegisteredSubobjectList": false
    },
    "Activation": {
      "AutoActivate": false
    },
    "Events": [
      "PhysicsVolumeChanged",
      "OnComponentActivated",
      "OnComponentDeactivated"
    ],
    "AdvancedProperties": {
      "ExposeToCinematic": false,
      "Access": "Private",
      "CPF": {
        "BlueprintVisible": true,
        "ZeroConstructor": true,
        "InstancedReference": true,
        "NonTransactional": true,
        "NoDestructor": true,
        "HasGetValueTypeHash": true
      }
    }
  }
}
```

### Graphiques

#### EventGraph

```json
{
  "Blueprint": "BP_SpawnManager",
  "Aliases": {
    "Actor": "/Script/Engine.Actor"
  },
  "Events": [
    {
      "Name": "ReceiveBeginPlay",
      "ParentClass": "Actor",
      "Overrides": true,
      "Enabled": false,
      "Comment": "Ce nœud est désactivé et ne sera pas appelé.",
      "Pins": [
        { "Name": "OutputDelegate", "Direction": "Output", "Type": "delegate" },
        { "Name": "then", "Direction": "Output", "Type": "exec" }
      ]
    },
    {
      "Name": "ReceiveActorBeginOverlap",
      "ParentClass": "Actor",
      "Overrides": true,
      "Enabled": false,
      "Comment": "Ce nœud est désactivé et ne sera pas appelé.",
      "Pins": [
        { "Name": "OutputDelegate", "Direction": "Output", "Type": "delegate" },
        { "Name": "then", "Direction": "Output", "Type": "exec" },
        { "Name": "OtherActor", "Direction": "Output", "Type": "object", "Class": "Actor" }
      ]
    },
    {
      "Name": "ReceiveTick",
      "ParentClass": "Actor",
      "Overrides": true,
      "Enabled": false,
      "Comment": "Ce nœud est désactivé et ne sera pas appelé.",
      "Pins": [
        { "Name": "OutputDelegate", "Direction": "Output", "Type": "delegate" },
        { "Name": "then", "Direction": "Output", "Type": "exec" },
        { "Name": "DeltaSeconds", "Direction": "Output", "Type": "float", "Default": "0.0" }
      ]
    }
  ]
}

```

### Fonctions

#### Construction Script

```json
{
  "Function": {
    "Name": "UserConstructionScript",
    "ParentClass": "Actor",
    "Type": "FunctionEntry",
    "AccessSpecifier": "Default",
    "IsPure": false,
    "Pins": [
      {
        "Name": "then",
        "Direction": "Output",
        "Type": "exec"
      }
    ]
  }
}
```

#### InitializeSpawnZone

```json
{
  "Function": {
    "Name": "InitializeSpawnZones",
    "Access": "Public",
    "Pure": false,
    "Category": "Par défaut",
    "Description": "",
    "CompactNodeTitle": "",
    "EditorCallable": false,
    "ThreadSafe": false,
    "Deprecated": false,
    "Inputs": [],
    "Outputs": []
  },
  "Nodes": [
    {
      "Type": "FunctionEntry",
      "Name": "InitializeSpawnZones",
      "OutputExec": "GetAllActorsOfClass"
    },
    {
      "Type": "CallFunction",
      "Function": "GameplayStatics::GetAllActorsOfClass",
      "Inputs": {
        "ActorClass": "BP_SpawnZone_C"
      },
      "Outputs": {
        "OutActors": "Array of BP_SpawnZone_C"
      },
      "InputExec": "FunctionEntry",
      "OutputExec": "Set SpawnZones"
    },
    {
      "Type": "SetVariable",
      "Variable": "SpawnZones",
      "VariableType": "Array of BP_SpawnZone_C",
      "InputExec": "GetAllActorsOfClass",
      "Value": "OutActors Output",
      "OutputExec": null
    }
  ],
  "Connections": [
    {
      "From": "FunctionEntry",
      "To": "GetAllActorsOfClass"
    },
    {
      "From": "GetAllActorsOfClass",
      "To": "Set SpawnZones"
    }
  ]
}
```

#### StartSpawnLoop

```json
{
    "FunctionName": "StartSpawnLoop",
    "Access": "Public",
    "Pure": false,
    "Category": "Par défaut",
    "Description": null,
    "Keywords": null,
    "CompactNodeTitle": null,
    "EditorCallable": false,
    "Inputs": [],
    "Outputs": [],
    "Logic": [
        {
            "Step": 1,
            "Action": "Get Variable",
            "VariableName": "SpawnZones",
            "Type": "Array of BP_SpawnZone_C"
        },
        {
            "Step": 2,
            "Action": "Call Function",
            "Function": "KismetArrayLibrary.Array_Length",
            "Target": "SpawnZones",
            "ReturnType": "int"
        },
        {
            "Step": 3,
            "Action": "Compare",
            "Operation": "Greater_IntInt",
            "A": "Array_Length result",
            "B": 0
        },
        {
            "Step": 4,
            "Action": "Branch",
            "Condition": "A > 0",
            "True": {
                "CallFunction": "KismetSystemLibrary.K2_SetTimer",
                "Parameters": {
                    "Object": "Self",
                    "FunctionName": "SpawnActor",
                    "Time": "SpawnInterval",
                    "bLooping": true,
                    "bMaxOncePerFrame": false,
                    "InitialStartDelay": 0.0,
                    "InitialStartDelayVariance": 0.0
                },
                "Return": "TimerHandle"
            },
            "False": {
                "CallFunction": "KismetSystemLibrary.PrintString",
                "Parameters": {
                    "InString": "No Spawn Zones! Check Initialize",
                    "PrintToScreen": true,
                    "PrintToLog": true,
                    "TextColor": "(R=0,G=0.66,B=1,A=1)",
                    "Duration": 2.0,
                    "Key": "None"
                },
                "DevOnly": true
            }
        }
    ]
}
```

#### SpawnActor

```json
{
    "FunctionName": "SpawnActor",
    "EditorSettings": {
        "Category": "Par défaut",
        "AccessSpecifier": "Public",
        "Pure": false,
        "CallableInEditor": false,
        "Keywords": "",
        "Description": "",
        "CompactNodeTitle": "",
        "Advanced": {
            "Const": false,
            "Exec": false,
            "ThreadSafe": false,
            "UnsafeDuringConstruction": false,
            "Deprecated": false,
            "DeprecationMessage": ""
        },
        "Inputs": [],
        "Outputs": []
    },
    "Variables": [
        { "Name": "SpawnedActors", "Type": "Array<Actor>" },
        { "Name": "MaxSpawnedActors", "Type": "int" },
        { "Name": "SpawnZones", "Type": "Array<BP_SpawnZone_C>" },
        { "Name": "ActorToSpawn", "Type": "Class<Actor>" }
    ],
    "LogicFlow": [
        { "Step": "Array_Length", "Input": "SpawnedActors", "Output": "Length" },
        { "Step": "GreaterEqual", "Inputs": ["Length", "MaxSpawnedActors"], "Output": "Condition" },
        { "Step": "Branch", "Condition": "Condition", "Outputs": ["TruePath", "FalsePath"] },
        { "Step": "Array_Random", "Input": "SpawnZones", "Output": "RandomSpawnZone", "Path": "TruePath" },
        { "Step": "GetRandomPointInZone", "Target": "RandomSpawnZone", "Output": "Vector" },
        { "Step": "Conv_VectorToTransform", "Input": "Vector", "Output": "Transform" },
        { "Step": "SpawnActorFromClass", "Class": "ActorToSpawn", "Transform": "Transform", "Output": "SpawnedActor" },
        { "Step": "Array_Add", "Array": "SpawnedActors", "Item": "SpawnedActor" }
    ]
}
```

#### GetAvailableZone

```json
{
  "Function": "GetAvailableZone",
  "Access": "Public",
  "Category": "Par défaut",
  "Pure": false,
  "EditorCallable": false,
  "Inputs": [],
  "Outputs": [
    {
      "Name": "AvailableZone",
      "Type": "BP_SpawnZone_C"
    }
  ],
  "Logic": [
    {
      "Call": "GetAllActorsOfClass",
      "Params": {
        "ActorClass": "BP_SpawnZone_C"
      },
      "Result": "OutActors[]"
    },
    {
      "Loop": "ForEach OutActors[]",
      "Body": [
        {
          "Call": "IsZoneAvailable",
          "Target": "ArrayElement",
          "Result": "IsAvailable"
        },
        {
          "If": "IsAvailable == true",
          "Then": {
            "Return": "AvailableZone = ArrayElement"
          }
        }
      ]
    }
  ]
}
```

#### RecycleActor

```json
{
  "Function": "RecycleActor",
  "Access": "Public",
  "Category": "Default",
  "Pure": false,
  "CallInEditor": false,
  "Inputs": [
    {
      "Name": "ActorToRecycle",
      "Type": "Actor",
      "ByRef": false,
      "Const": false
    }
  ],
  "Outputs": [],
  "ExecutionFlow": [
    {
      "Node": "SetActorHiddenInGame",
      "Target": "ActorToRecycle",
      "Parameters": {
        "bNewHidden": true
      }
    },
    {
      "Node": "SetActorEnableCollision",
      "Target": "ActorToRecycle",
      "Parameters": {
        "bNewActorEnableCollision": false
      }
    },
    {
      "Node": "SetActorTickEnabled",
      "Target": "ActorToRecycle",
      "Parameters": {
        "bEnabled": false
      }
    },
    {
      "Node": "Array_Add",
      "Library": "KismetArrayLibrary",
      "Parameters": {
        "TargetArray": {
          "Name": "ActorPool",
          "Type": "Array of Actor",
          "Const": true,
          "ByRef": true
        },
        "NewItem": "ActorToRecycle"
      }
    }
  ]
}
```

### Variables

#### SpawnZones

```json
{
  "VariableName": "SpawnZones",
  "Type": "Array of BP_SpawnZone_C",
  "Access": "Public",
  "Category": "Default",
  "EditableInstanceOnly": true,
  "ExposeOnSpawn": true,
  "BlueprintVisible": true,
  "DisableEditOnTemplate": true,
  "Replication": "None",
  "DefaultValue": []
}
```

#### MaxSpawnedActors

```json
{
  "Variable": {
    "Name": "MaxSpawnedActors",
    "Type": "int",
    "DefaultValue": 0,
    "DisplayName": "Max Spawned Actors",
    "Category": "Default",
    "Access": "Public",
    "EditableInstance": true,
    "ExposeOnSpawn": false,
    "ExposeToCinematics": false,
    "BlueprintReadOnly": false,
    "Replication": "None",
    "Description": "",
    "AdvancedOptions": {
      "ConfigVar": false,
      "Transient": false,
      "SaveGame": false,
      "Obsolete": false
    },
    "PropertyFlags": {
      "Editable": true,
      "BlueprintVisible": true,
      "ZeroConstructor": true,
      "PlainOldData": true,
      "NoDestructor": true,
      "HasGetValueTypeHash": true
    }
  }
}
```

#### SpawnedActors

```json
{
  "VariableName": "SpawnedActors",
  "Type": "Array<AActor*>",
  "Access": "Public",
  "BlueprintVisible": true,
  "EditableInstance": false,
  "Category": "Default",
  "Replication": "None",
  "DefaultValue": [],
  "Flags": [
    "CPF_Edit",
    "CPF_BlueprintVisible",
    "CPF_DisableEditOnTemplate",
    "CPF_DisableEditOnInstance"
  ]
}
```

#### SpawnInterval

```json
{
  "Variable": "SpawnInterval",
  "Type": "Float",
  "Access": "Public",
  "EditableInstanceOnly": true,
  "BlueprintReadOnly": false,
  "ExposeOnSpawn": false,
  "ExposeToCinematic": false,
  "Category": "Default",
  "Replication": "None",
  "DefaultValue": 0.0,
  "AdvancedOptions": {
    "Config": false,
    "Transient": false,
    "SaveGame": false,
    "Deprecated": false
  },
  "PropertyFlags": [
    "Edit",
    "BlueprintVisible",
    "ZeroConstructor",
    "PlainOldData",
    "NoDestructor",
    "HasGetValueTypeHash"
  ]
}
```

#### ActorToSpawn

```json
{
  "Variable": "ActorToSpawn",
  "Type": "Class Reference (Actor)",
  "FriendlyName": "Actor to Spawn",
  "Category": "Default",
  "DefaultValue": "None",
  "Access": "Public",
  "EditableInstance": true,
  "Replication": "None",
  "CinematicExposed": false,
  "BlueprintReadOnly": false,
  "ExposeOnSpawn": false,
  "ConfigVariable": false,
  "Transient": false,
  "SaveGame": false,
  "AdvancedDisplay": false,
  "Obsolete": false,
  "Flags": [
    "Editable in Editor (CPF_Edit)",
    "Blueprint Visible (CPF_BlueprintVisible)",
    "Zero Constructor (CPF_ZeroConstructor)",
    "No Destructor (CPF_NoDestructor)",
    "Has GetValueTypeHash (CPF_HasGetValueTypeHash)"
  ]
}
```

#### bUsePooling

```json
{
  "Variable": {
    "Name": "bUsePooling",
    "Type": "bool",
    "FriendlyName": "Use Pooling",
    "Category": "Default",
    "Access": "Public",
    "InstanceEditable": true,
    "BlueprintReadOnly": false,
    "ExposeOnSpawn": false,
    "Private": false,
    "ExposeToCinematics": false,
    "Replication": "None",
    "ReplicationCondition": "None",
    "ConfigVariable": false,
    "Transient": false,
    "SaveGame": false,
    "AdvancedDisplay": false,
    "Obsolete": false,
    "Flags": [
      "CPF_Edit",
      "CPF_BlueprintVisible",
      "CPF_ZeroConstructor",
      "CPF_IsPlainOldData",
      "CPF_NoDestructor",
      "CPF_HasGetValueTypeHash"
    ],
    "DefaultValue": false
  }
}
```

#### ActorPool

```json
{
  "Variable": {
    "Name": "ActorPool",
    "Type": "Array of Actor",
    "Category": "Default",
    "Access": "Public",
    "Editable": true,
    "ExposedOnSpawn": false,
    "BlueprintReadOnly": false,
    "Replication": "None",
    "Description": "",
    "AdvancedFlags": {
      "ConfigVariable": false,
      "Transient": false,
      "SaveGame": false,
      "Deprecated": false,
      "DisplayAdvanced": false
    },
    "EditorFlags": {
      "CPF_Edit": true,
      "CPF_BlueprintVisible": true,
      "CPF_DisableEditOnTemplate": true,
      "CPF_DisableEditOnInstance": true
    },
    "DefaultValue": []
  }
}
```
