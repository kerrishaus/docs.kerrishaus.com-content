# Save Format

This page details the current save format for the game only. Previous save formats are not recorded here.  

The format consumed by the game is JavaScript spec JSON, but this page also provides ObjGen format JSON for easy modification.

JSON format.
```
{
  "version": 1,
  "shop": {
    "type": 1,
    "reputation": 0,
    "money": 0,
    "containers": [
      {
        "itemType": "tomato",
        "position": {
          "x": 0,
          "y": 0,
          "z": 0
        },
        "amount": 0
      }
    ],
    "customers": [
      {
        "reputation": 0,
        "position": {
          "x": 0,
          "y": 0,
          "z": 0
        },
        "carriedItems": [
          {
            "itemType": "tomato"
          }
        ],
        "actions": [
          {
            "name": {},
            "type": {},
            "amount": {},
            "container": {},
            "position": {
              "x": 0,
              "y": 0,
              "z": 0
            }
          }
        ]
      }
    ]
  },
  "player": {
    "position": {
      "x": 0,
      "y": 0,
      "z": 0
    },
    "carriedItems": [
      {
        "itemType": {},
        "position": {
          "x": 0,
          "y": 0,
          "z": 0
        }
      }
    ]
  },
  "employees": {
    "position": {
      "x": 0,
      "y": 0,
      "z": 0
    },
    "carriedItems": [
      {
        "itemType": "tomato"
      }
    ]
  }
}
```

ObjGen format
```
version n = 1

shop
  type n = 1
  reputation n = 0
  money n = 0
  containers[]
    itemType = tomato
    position
      x n = 0
      y n = 0
      z n = 0
    amount n = 0
  customers[]
    reputation n = 0
    position
      x n = 0
      y n = 0
      z n = 0
    carriedItems[]
      itemType = tomato
    actions[]
      name
      type
      amount
      container
      position
        x n = 0
        y n = 0
        z n = 0

player
  position
    x n = 0
    y n = 0
    z n = 0
  carriedItems[]
    itemType
    position
      x n = 0
      y n = 0
      z n = 0

employees
  position
    x n = 0
    y n = 0
    z n = 0
  carriedItems[]
    itemType = tomato
```
