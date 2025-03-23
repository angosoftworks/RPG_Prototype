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

<figure><img src=".gitbook/assets/image.png" alt=""><figcaption><p>BP_SpawnZone - Paramètres de classe</p></figcaption></figure>

### Valeurs par défaut de classe

<figure><img src=".gitbook/assets/image (1).png" alt=""><figcaption><p>BP_SpawnZone - Valeurs par défaut de classe pt1</p></figcaption></figure>

<figure><img src=".gitbook/assets/image (2).png" alt=""><figcaption><p>BP_SpawnZone - Valeurs par défaut de classe pt2</p></figcaption></figure>

<figure><img src=".gitbook/assets/image (4).png" alt=""><figcaption><p>BP_SpawnZone - Valeurs par défaut de classe pt3</p></figcaption></figure>

<figure><img src=".gitbook/assets/image (5).png" alt=""><figcaption><p>BP_SpawnZone - Valeurs par défaut de classe pt4</p></figcaption></figure>

### Graphiques

#### EventGraph

```
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

```
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

```
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

```
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

#### DefaultSceneRoot

<div align="center"><figure><img src=".gitbook/assets/image (6).png" alt=""><figcaption><p>DefaultSceneRoot</p></figcaption></figure></div>

#### SpawnZones

<figure><img src=".gitbook/assets/image (1) (1).png" alt=""><figcaption><p>SpawnZones</p></figcaption></figure>

```
BPVar(VarName="SpawnZones",VarGuid=99BB1E3747AAB611B223A3B7E2262CCD,VarType=(PinCategory="object",PinSubCategory="",PinSubCategoryObject="/Script/Engine.BlueprintGeneratedClass'/Game/Blueprints/BP_SpawnZone.BP_SpawnZone_C'",PinSubCategoryMemberReference=(MemberParent=None,MemberName="",MemberGuid=00000000000000000000000000000000),PinValueType=(TerminalCategory="",TerminalSubCategory="",TerminalSubCategoryObject=None,bTerminalIsConst=False,bTerminalIsWeakPointer=False,bTerminalIsUObjectWrapper=False),ContainerType=Array,bIsReference=False,bIsConst=False,bIsWeakPointer=False,bIsUObjectWrapper=False,bSerializeAsSinglePrecisionFloat=False),FriendlyName="Spawn Zones",Category=NSLOCTEXT("KismetSchema", "Default", "Default"),PropertyFlags=2053,RepNotifyFunc="",ReplicationCondition=COND_None,MetaDataArray=((DataKey="ExposeOnSpawn",DataValue="true")),DefaultValue="")
```

#### MaxSpawnedActors

<figure><img src=".gitbook/assets/image (2) (1).png" alt=""><figcaption><p>MaxSpawnedActors</p></figcaption></figure>

```
BPVar(VarName="MaxSpawnedActors",VarGuid=E2377D9143074317B09A1F854859A5BE,VarType=(PinCategory="int",PinSubCategory="",PinSubCategoryObject=None,PinSubCategoryMemberReference=(MemberParent=None,MemberName="",MemberGuid=00000000000000000000000000000000),PinValueType=(TerminalCategory="",TerminalSubCategory="",TerminalSubCategoryObject=None,bTerminalIsConst=False,bTerminalIsWeakPointer=False,bTerminalIsUObjectWrapper=False),ContainerType=None,bIsReference=False,bIsConst=False,bIsWeakPointer=False,bIsUObjectWrapper=False,bSerializeAsSinglePrecisionFloat=False),FriendlyName="Max Spawned Actors",Category=NSLOCTEXT("KismetSchema", "Default", "Default"),PropertyFlags=5,RepNotifyFunc="",ReplicationCondition=COND_None,MetaDataArray=,DefaultValue="0")
```

#### SpawnedActors

<figure><img src=".gitbook/assets/image (3) (1).png" alt=""><figcaption><p>SpawnedActors</p></figcaption></figure>

```
BPVar(VarName="SpawnedActors",VarGuid=F49BAD44426F82AECBC9F4B02F29BF14,VarType=(PinCategory="object",PinSubCategory="",PinSubCategoryObject="/Script/CoreUObject.Class'/Script/Engine.Actor'",PinSubCategoryMemberReference=(MemberParent=None,MemberName="",MemberGuid=00000000000000000000000000000000),PinValueType=(TerminalCategory="",TerminalSubCategory="",TerminalSubCategoryObject=None,bTerminalIsConst=False,bTerminalIsWeakPointer=False,bTerminalIsUObjectWrapper=False),ContainerType=Array,bIsReference=False,bIsConst=False,bIsWeakPointer=False,bIsUObjectWrapper=False,bSerializeAsSinglePrecisionFloat=False),FriendlyName="Spawned Actors",Category=NSLOCTEXT("KismetSchema", "Default", "Default"),PropertyFlags=67589,RepNotifyFunc="",ReplicationCondition=COND_None,MetaDataArray=,DefaultValue="")
```

#### SpawnInterval

<figure><img src=".gitbook/assets/image (4) (1).png" alt=""><figcaption><p>SpawnInterval</p></figcaption></figure>

```
BPVar(VarName="SpawnInterval",VarGuid=6A910B7846BC5E1FB72427A4F4F53902,VarType=(PinCategory="real",PinSubCategory="double",PinSubCategoryObject=None,PinSubCategoryMemberReference=(MemberParent=None,MemberName="",MemberGuid=00000000000000000000000000000000),PinValueType=(TerminalCategory="",TerminalSubCategory="",TerminalSubCategoryObject=None,bTerminalIsConst=False,bTerminalIsWeakPointer=False,bTerminalIsUObjectWrapper=False),ContainerType=None,bIsReference=False,bIsConst=False,bIsWeakPointer=False,bIsUObjectWrapper=False,bSerializeAsSinglePrecisionFloat=False),FriendlyName="Spawn Interval",Category=NSLOCTEXT("KismetSchema", "Default", "Default"),PropertyFlags=5,RepNotifyFunc="",ReplicationCondition=COND_None,MetaDataArray=,DefaultValue="0.000000")
```

#### ActorToSpawn

<figure><img src=".gitbook/assets/image (5) (1).png" alt=""><figcaption><p>ActorToSpawn</p></figcaption></figure>

```
BPVar(VarName="ActorToSpawn",VarGuid=1181DFF84F0A322C19672598988B6F54,VarType=(PinCategory="class",PinSubCategory="",PinSubCategoryObject="/Script/CoreUObject.Class'/Script/Engine.Actor'",PinSubCategoryMemberReference=(MemberParent=None,MemberName="",MemberGuid=00000000000000000000000000000000),PinValueType=(TerminalCategory="",TerminalSubCategory="",TerminalSubCategoryObject=None,bTerminalIsConst=False,bTerminalIsWeakPointer=False,bTerminalIsUObjectWrapper=False),ContainerType=None,bIsReference=False,bIsConst=False,bIsWeakPointer=False,bIsUObjectWrapper=False,bSerializeAsSinglePrecisionFloat=False),FriendlyName="Actor to Spawn",Category=NSLOCTEXT("KismetSchema", "Default", "Default"),PropertyFlags=5,RepNotifyFunc="",ReplicationCondition=COND_None,MetaDataArray=,DefaultValue="None")
```

#### bUsePooling

<figure><img src=".gitbook/assets/image (6) (1).png" alt=""><figcaption><p>bUsePooling</p></figcaption></figure>

```
BPVar(VarName="bUsePooling",VarGuid=9084CD3B449C3222CDE389BA35CDEECB,VarType=(PinCategory="bool",PinSubCategory="",PinSubCategoryObject=None,PinSubCategoryMemberReference=(MemberParent=None,MemberName="",MemberGuid=00000000000000000000000000000000),PinValueType=(TerminalCategory="",TerminalSubCategory="",TerminalSubCategoryObject=None,bTerminalIsConst=False,bTerminalIsWeakPointer=False,bTerminalIsUObjectWrapper=False),ContainerType=None,bIsReference=False,bIsConst=False,bIsWeakPointer=False,bIsUObjectWrapper=False,bSerializeAsSinglePrecisionFloat=False),FriendlyName="Use Pooling",Category=NSLOCTEXT("KismetSchema", "Default", "Default"),PropertyFlags=5,RepNotifyFunc="",ReplicationCondition=COND_None,MetaDataArray=,DefaultValue="False")
```

#### ActorPool

<figure><img src=".gitbook/assets/image (7).png" alt=""><figcaption><p>ActorPool</p></figcaption></figure>

```
BPVar(VarName="ActorPool",VarGuid=EB5307D144D10BAC2C19248F485B3AC0,VarType=(PinCategory="object",PinSubCategory="",PinSubCategoryObject="/Script/CoreUObject.Class'/Script/Engine.Actor'",PinSubCategoryMemberReference=(MemberParent=None,MemberName="",MemberGuid=00000000000000000000000000000000),PinValueType=(TerminalCategory="",TerminalSubCategory="",TerminalSubCategoryObject=None,bTerminalIsConst=False,bTerminalIsWeakPointer=False,bTerminalIsUObjectWrapper=False),ContainerType=Array,bIsReference=False,bIsConst=False,bIsWeakPointer=False,bIsUObjectWrapper=False,bSerializeAsSinglePrecisionFloat=False),FriendlyName="Actor Pool",Category=NSLOCTEXT("KismetSchema", "Default", "Default"),PropertyFlags=67589,RepNotifyFunc="",ReplicationCondition=COND_None,MetaDataArray=,DefaultValue="")
```

####

####

####

####

####

####

####
