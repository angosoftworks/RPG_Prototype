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

# Struct\_PNJData

```json
{
  "Struct": "Struct_PNJData",
  "Access": "Public",
  "Variables": [
    {
      "Name": "Name",
      "Type": "FString",
      "Editable": true,
      "SaveGame": false,
      "MultiLineText": false
    },
    {
      "Name": "Profession",
      "Type": "FString",
      "Editable": true,
      "SaveGame": false,
      "MultiLineText": false
    },
    {
      "Name": "Clan",
      "Type": "FString",
      "Editable": true,
      "SaveGame": false,
      "MultiLineText": false
    },
    {
      "Name": "Traits",
      "Type": "Struct_PNJTraits",
      "Editable": true,
      "SaveGame": true,
      "MultiLineText": false,
      "Defaults": {
        "Ambition": 0,
        "Loyauté": 0,
        "Sociabilité": 0
      }
    },
    {
      "Name": "Relations",
      "Type": "TMap<FString, int32>",
      "Editable": true,
      "SaveGame": true,
      "MultiLineText": false,
      "Defaults": {}
    }
  ]
}
```
