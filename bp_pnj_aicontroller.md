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

# BP\_PNJ\_AIController

```json
{
  "BlueprintName": "BP_PNJ_AIController",
  "ParentClass": "AIController",
  "Settings": {
    "RunConstructionScriptOnDrag": true,
    "RunConstructionScriptInSequencer": false,
    "ShouldCookPropertyGuides": "Inherit"
  },
  "ActorTick": {
    "StartWithTickEnabled": true,
    "TickInterval": 0.0,
    "AllowTickBeforeBeginPlay": false,
    "TickEvenWhenPaused": false,
    "AllowTickOnDedicatedServer": true,
    "TickGroup": "PrePhysics"
  },
  "AIOptions": {
    "StartAILogicOnPossess": false,
    "StopAILogicOnUnpossess": true,
    "SkipExtraLOSChecks": true,
    "AllowStrafe": false,
    "WantsPlayerState": true,
    "SetControlRotationFromPawnOrientation": true,
    "PerceptionComponent": "None",
    "DefaultNavigationFilterClass": "None"
  },
  "ComponentTick": {
    "StartWithTickEnabled": true,
    "TickInterval": 0.0,
    "TickEvenWhenPaused": false,
    "AllowTickOnDedicatedServer": false,
    "TickGroup": "DuringPhysics"
  },
  "Replication": {
    "OnlyRelevantToOwner": true,
    "Replicates": false,
    "NetDormancy": "Awake",
    "NetCullDistanceSquared": 225000000.0,
    "NetUpdateFrequency": 100.0,
    "MinNetUpdateFrequency": 2.0,
    "NetPriority": 1.0,
    "CallPreReplication": true,
    "CallPreReplicationForReplay": true,
    "LocationQuantization": "RoundWholeNumber",
    "VelocityQuantization": "RoundWholeNumber",
    "RotationQuantization": "ByteComponents"
  },
  "Activation": {
    "AutoActivate": true
  },
  "Variable": {
    "EditableWhenInherited": true
  },
  "Controller": {
    "AttachToPawn": false
  },
  "Actor": {
    "CanBeDamaged": false,
    "InitialLifeSpan": 0.0,
    "SpawnCollisionHandlingMethod": "AlwaysSpawnIgnoreCollisions",
    "FindCameraComponentWhenViewTarget": true
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
  "EventsAvailable": [
    "OnInstigatedAnyDamage",
    "OnPossessedPawnChanged",
    "OnActorBeginOverlap",
    "OnActorEndOverlap",
    "OnActorHit",
    "OnDestroyed",
    "OnEndPlay"
  ]
}
```
