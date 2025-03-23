{
  "Blueprint": {
    "Name": "BP_SpawnZone",
    "ParentClass": "Actor",
    "Interfaces": ["BPI_SpawnZone"],
    "AdvancedOptions": {
      "Deprecated": false,
      "GenerateConstClass": false,
      "GenerateAbstractClass": false,
      "ShouldCookPropertyGuides": "Inherit"
    },
    "BlueprintOptions": {
      "RunConstructionScriptOnDrag": true,
      "RunConstructionScriptInSequence": false
    },
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
    "ActorSettings": {
      "CanBeDamaged": true,
      "InitialLifeSpan": 0.0,
      "SpawnCollisionHandling": "AlwaysSpawnIgnoreCollisions",
      "FindCameraComponentWhenViewTarget": true
    },
    "Physics": {
      "AsyncPhysicsTickEnabled": false
    },
    "WorldPartition": {
      "IsSpatiallyLoaded": true
    },
    "Components": [
      {
        "Name": "DefaultSceneRoot",
        "Type": "SceneComponent",
        "Category": "Par défaut",
        "EditableWhenInherited": true,
        "Mobility": "Mobile",
        "Scale": [1.0, 1.0, 1.0],
        "Tick": {
          "StartWithTickEnabled": true,
          "TickInterval": 0.0,
          "TickGroup": "During Physics",
          "AllowTickOnDedicatedServer": true,
          "TickEvenWhenPaused": false
        },
        "Rendering": { "DetailMode": "Low" },
        "Navigation": { "CanEverAffectNavigation": false },
        "AdvancedFlags": { "CPF_BlueprintVisible": true },
        "Events": [
          "PhysicsVolumeChanged",
          "OnComponentActivated",
          "OnComponentDeactivated"
        ]
      },
      {
        "Name": "Box",
        "Type": "BoxComponent",
        "Category": "Default",
        "EditableWhenInherited": true,
        "Transform": {
          "Translation": [0.0, 0.0, 0.0],
          "Rotation": [0.0, 0.0, 0.0],
          "Scale": [1.0, 1.0, 1.0],
          "Mobility": "Movable"
        },
        "Shape": {
          "BoxExtent": [32.0, 32.0, 32.0],
          "ShapeColor": [223, 149, 157, 255]
        },
        "Collision": {
          "Profile": "NoCollision",
          "ObjectType": "WorldStatic",
          "CollisionResponses": {
            "Visibility": "Ignore",
            "Camera": "Ignore",
            "WorldStatic": "Ignore",
            "WorldDynamic": "Ignore",
            "Pawn": "Ignore",
            "PhysicsBody": "Ignore",
            "Vehicle": "Ignore",
            "Destructible": "Ignore"
          },
          "GenerateOverlapEvents": false
        },
        "Physics": {
          "SimulatePhysics": false,
          "EnableGravity": true,
          "LinearDamping": 0.01,
          "AngularDamping": 0.0,
          "Constraints": {
            "LockPosition": ["X", "Y", "Z"],
            "LockRotation": ["X", "Y", "Z"]
          },
          "ApplyImpulseOnDamage": true,
          "ReplicatePhysics": true,
          "Mass": 65.15,
          "MassScale": 1.0,
          "SolverIterations": {
            "Position": 8,
            "Velocity": 2,
            "Projection": 1
          },
          "StartAwake": true
        },
        "Rendering": {
          "Visible": true,
          "HiddenInGame": true,
          "ReflectionCapture": true,
          "RayTracing": true,
          "ReceivesDecals": true
        },
        "Navigation": {
          "AffectNavigation": true,
          "DynamicObstacle": false
        },
        "Tick": { "Enabled": true, "Interval": 0.0, "DuringPhysics": true },
        "Events": [
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
    ],
    "Variables": [
      {
        "Name": "MaxActorsInZone",
        "Type": "int",
        "Category": "Default",
        "Access": "Private",
        "Tooltip": "Nombre max d’acteurs autorisés dans la zone",
        "DefaultValue": 0
      },
      {
        "Name": "SpawnedActorsInZone",
        "Type": "Array<Actor>",
        "Category": "Default",
        "Access": "Public",
        "Tooltip": "Liste des acteurs déjà spawn dans cette zone",
        "DefaultValue": []
      },
      {
        "Name": "bIsZoneEnabled",
        "Type": "bool",
        "Category": "Default",
        "Access": "Public",
        "DefaultValue": true
      },
      {
        "Name": "bCooldownOver",
        "Type": "bool",
        "Category": "Default",
        "Access": "Public",
        "DefaultValue": true
      }
    ],
    "Functions": [
      {
        "Name": "UserConstructionScript",
        "Type": "FunctionEntry",
        "Access": "Public",
        "Notes": "Construction Script spécifique aux Actors"
      },
      {
        "Name": "GetRandomPointInZone",
        "Access": "Public",
        "Outputs": [{ "Type": "Vector", "Name": "Vector" }],
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
      },
      {
        "Name": "IsZoneAvailable",
        "Access": "Public",
        "Type": "Pure",
        "Outputs": [{ "Name": "IsAvailable", "Type": "bool" }],
        "Logic": [
          "Get SpawnedActorsInZone → Array<Actor>",
          "CallFunction: Array_Length → NumSpawnedActors",
          "Compare NumSpawnedActors < MaxActorsInZone → IsUnderMax",
          "Get bIsZoneEnabled",
          "Get bCooldownOver",
          "BooleanAND(IsUnderMax, bIsZoneEnabled, bCooldownOver) → IsAvailable"
        ]
      }
    ],
    "EventGraph": [
      {
        "Event": "ReceiveBeginPlay",
        "Enabled": false,
        "Comment": "Ce nœud est désactivé et ne sera pas appelé."
      },
      {
        "Event": "ReceiveActorBeginOverlap",
        "Enabled": false,
        "Comment": "Ce nœud est désactivé et ne sera pas appelé."
      },
      {
        "Event": "ReceiveTick",
        "Enabled": false,
        "Comment": "Ce nœud est désactivé et ne sera pas appelé."
      }
    ]
  }
}
