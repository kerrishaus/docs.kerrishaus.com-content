# Save Format

This page details the current save format for the game only. Previous save formats are not recorded here.  

The format consumed by the game is JavaScript spec JSON, but this page also provides ObjGen format JSON for easy modification.

JSON format.
```
{
  "version": 1,
  "shop": {
    "type": 1,
    "money": 0,
    "maxCustomers": 0,
    "timeUntilNextCustomer": 0,
    "timeSinceLastCustomer": 0,
    "minTimeUntilNextCustomer": 0,
    "maxTimeUntilNextCustomer": 0,
    "lifeSales": 0,
    "lifeCustomers": 0,
    "lifeReputation": 0,
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
        "rotation": {
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
    "rotation": {
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
    "rotation": {
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

  money n = 0

  maxCustomers n = 0
  timeUntilNextCustomer n = 0
  timeSinceLastCustomer n = 0
  minTimeUntilNextCustomer n = 0
  maxTimeUntilNextCustomer n = 0

  lifeSales n = 0
  lifeCustomers n = 0
  lifeReputation n = 0

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
    rotation
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
  rotation
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
  rotation
    x n = 0
    y n = 0
    z n = 0
  carriedItems[]
    itemType = tomato
```
