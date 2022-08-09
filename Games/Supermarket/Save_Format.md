# Save Format

This page details the current save format for the game only. Previous save formats are not recorded here.  

The format consumed by the game is JavaScript spec JSON, but this page also provides ObjGen format JSON for easy modification.

This is the initial game save, in JSON.
```
{
  "version": 1,
  "shop": {
    "type": 1,
    "money": 25,
    "maxCustomers": 20,
    "timeUntilNextCustomer": 14,
    "timeSinceLastCustomer": 0,
    "minTimeUntilNextCustomer": 7,
    "maxTimeUntilNextCustomer": 20,
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
    ],
    "employees": [
      {
        "position": {
          "x": 0,
          "y": 0,
          "z": 0.5
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
        "actions": []
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
      "z": 0.5
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
  }
}
```

ObjGen format
```
version n = 1

shop
  type n = 1

  money n = 25

  maxCustomers n = 20
  timeUntilNextCustomer n = 14
  timeSinceLastCustomer n = 0
  minTimeUntilNextCustomer n = 7
  maxTimeUntilNextCustomer n = 20

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
  employees[]
    position
      x n = 0
      y n = 0
      z n = 0.5
    rotation
      x n = 0
      y n = 0
      z n = 0
    carriedItems[]
      itemType = tomato
    actions[]

player
  position
    x n = 0
    y n = 0
    z n = 0
  rotation
    x n = 0
    y n = 0
    z n = 0.5
  carriedItems[]
    itemType
    position
      x n = 0
      y n = 0
      z n = 0
```
