---
description: General ingame commands for administrators
---

General commands which can be executed by players with administrative power

## Admin Commands
- [setcash](#setcash)
- [addbank](#addbank)
- [addcash](#addcash)
- [setbank](#setbank)
- [addparking](#addparking)
- [removeparking](#removeparking)
- [clearparking](#clearparking)
- [printparking](#printparking)
- [setdimension](#setdimension)
- [setinterior](#setinterior)
- [clearinventory](#clearinventory)
- [cleartoolbar](#cleartoolbar)
- [clearequipment](#clearequipment)
- [getitem](#getitem)
- [noclip](#noclip)
- [sethealth](#sethealth)
- [setarmour](#setarmour)
- [freeze](#freeze)
- [unfreeze](#unfreeze)
- [kick](#kick)
- [ban](#ban)
- [unban](#unban)
- [makeAdmin](#makeadmin)
- [info](#info)
- [revive](#revive)
- [gethere](#gethere)
- [goto](#goto)
- [tpwp](#tpwp)
- [coords](#coords)
- [testerrorscreen](#testerrorscreen)
- [testworldhelptext](#testworldhelptext)
- [testspinner](#testspinner)
- [testshard](#testshard)
- [testcredits](#testcredits)
- [testinput](#testinput)
- [testobjectattach](#testobjectattach)
- [testobjectattachinfinite](#testobjectattachinfinite)
- [testjobmenu](#testjobmenu)
- [testped](#testped)
- [testactionmenu](#testactionmenu)
- [refillVehicle](#refillvehicle)
- [repairVehicle](#repairvehicle)
- [tempvehicle](#tempvehicle)
- [addvehicle](#addvehicle)
- [weapon](#weapon)
- [removeallweapons](#removeallweapons)
- [ac](#ac)
- [apm](#apm)
- [broadcast](#broadcast)
- [addhouse](#addhouse)
- [settime](#settime)
- [cleartime](#cleartime)
- [setfood](#setfood)
- [setwater](#setwater)
- [setweather](#setweather)
- [clearweather](#clearweather)
- [setfuel](#setfuel)
- [fcreate](#fcreate)
- [fjoin](#fjoin)


# setcash

**Usage**
```bash
/setcash [amount] [id]
```

**Example**
```bash
/setcash 0 10000
```

# addbank

**Usage**
```bash
/addbank [amount] [id]
```

**Example**
```bash
/addbank 10000 0
```

# addcash

**Usage**
```bash
/addcash [amount] [id]
```

**Example**
```bash
/addcash 10000 0
```

# setbank

**Usage**
```bash
/setbank [amount] [id]
```

**Example**
```bash
/setbank 10000 0
```

# addparking

**Usage**
```bash
/addparking - Add parking to a temporary list.
```

**Example**
```bash
/addparking
```

**Response**

![](https://i.imgur.com/V9FVSZ4.png)

# removeparking

**Usage**
```bash
/removeparking - Remove last element from parking list.
```

**Example**
```bash
/removeparking
```

**Response**

![](https://i.imgur.com/QrrXbEA.png)

# clearparking

**Usage**
```bash
/clearparking - Clear Temporary List
```

**Example**
```bash
/clearparking
```

**Response**

![](https://i.imgur.com/h6mOUSh.png)

# printparking

**Usage**
```bash
/printparking - Print Temporary List
```

**Example**
```bash
/printparking
```

**Response**

![](https://i.imgur.com/5DJG5GJ.png)

# setdimension

**Usage**
```bash
/setdimension [id] [dimension]
```

**Example**
```bash
/setdimension 0 2
```

**Response**

![](https://i.imgur.com/vejxkzh.png)

# setinterior

**Usage**
```bash
/setinterior [id] [interior]
```

**Example**
```bash
/setinterior 0 null
```

**Response**

![](https://i.imgur.com/Jn5u2Ry.png)

# clearinventory

**Usage**
```bash
/clearinventory - Clear your inventory
```

**Example**
```bash
/clearinventory
```

# cleartoolbar

**Usage**
```bash
/cleartoolbar - Clear your Toolbar
```

**Example**
```bash
/cleartoolbar
```

# clearequipment

**Usage**
```bash
/clearequipment - Clear your Equipment
```

**Example**
```bash
/clearequipment
```

# getitem

**Usage**
```bash
/getitem [item-name] - Get an item by name
```

**Example**
```bash
/getitem Burger
```

**Response**

![](https://i.imgur.com/LCA0ND8.png)

# noclip

**Usage**
```bash
/noclip - Toggle No Clip Mode
```

**Example**
```bash
/noclip
```

**Response**

![](https://i.imgur.com/6qkO2X8.png)

# sethealth

**Usage**
```bash
/sethealth [value] [id]
```

**Example**
```bash
/sethealth 150 0
```

**Response**

![](https://i.imgur.com/Gbtik7N.png)

# setarmour

**Usage**
```bash
/setarmour [value] [id]
```

**Example**
```bash
/setarmour 50 0
```

**Response**

![](https://i.imgur.com/QMTOS1r.png)

# freeze

**Usage**
```bash
/freeze [id] - Freeze the specified player by id
```

**Example**
```bash
/freeze 0
```

**Response**

![](https://i.imgur.com/nJzVjls.png)

# unfreeze

**Usage**
```bash
/unfreeze [id] - Unfreeze the player specified by id
```

**Example**
```bash
/unfreeze 0
```

**Response**

![](https://i.imgur.com/nhdKTXC.png)

# kick

**Usage**
```bash
/kick [id] [reason] - Kicks the player with a reason
```

**Example**
```bash
/kick 0 Something happend
```

**Response**

![](https://i.imgur.com/iYw1z2t.png)

# ban

**Usage**
```bash
/ban [id] [reason] - Bans a player
```

**Example**
```bash
/ban 0 Cheating
```

**Response**

![](https://i.imgur.com/m2QVeYf.png)

# unban

**Usage**
```bash
/unban [discord_id] - Unbans a player by discord id
```

**Example**
```bash
/unban 700753097974218812
```

# makeAdmin

**Usage**
```bash
/makeAdmin [id] [PermissionLevel] - Add permission to specified player
```

**Example**
```bash
/makeAdmin 0 4
```

# info

**Usage**
```bash
/info [id] - Get account info for the specified id
```

**Example**
```bash
/info 0
```

**Response**

![](https://i.imgur.com/tf1TCE6.png)

# revive

**Usage**
```bash
/revive [id] - Revive self or others
```

**Example**
```bash
/revive 0
```

# gethere

**Usage**
```bash
/gethere [id] - Teleports a player to your position
```

**Example**
```bash
/gethere 0
```

# goto

**Usage**
```bash
/goto [id] - Teleports you to the specified players
```

**Example**
```bash
/goto 0
```

# tpwp

**Usage**
```bash
/tpwp - Teleport to a waypoint. Create waypoint First
```

**Example**
```bash
/tpwp
```

# coords

**Usage**
```bash
/coords [x] [y] [z] - Teleport to some coordinates
```

**Example**
```bash
/coords 0 1 73
```

# testerrorscreen

**Usage**
```bash
/testerrorscreen - Shows a temporary error screen
```

**Example**
```bash
/testerrorscreen
```

**Response**

![](https://i.imgur.com/FuC6DSk.png)

# testworldhelptext

**Usage**
```bash
/testworldhelptext - Shows temporary world help text
```

**Example**
```bash
/testworldhelptext
```

**Response**

![](https://i.imgur.com/FLZ9sPw.png)

# testspinner

**Usage**
```bash
/testspinner - Shows a temporary spinner
```

**Example**
```bash
/testspinner
```

**Response**

![](https://i.imgur.com/s2Xfv9V.png)

# testshard

**Usage**
```bash
/testshard - Shows a temporary shard
```

**Example**
```bash
/testshard
```

**Response**
![](https://i.imgur.com/N5FahSK.png)

# testcredits

**Usage**
```bash
/testcredits - Shows a temporary credits display
```

**Example**
```bash
/testcredits
```

**Response**

![](https://i.imgur.com/JlSKPUO.png)

# testinput

**Usage**
```bash
/testinput - Opens an temporary inputmenu
```

**Example**
```bash
/testinput
```

**Response**

![](https://i.imgur.com/zGf2SxA.png)

# testobjectattach

**Usage**
```bash
/testobjectattach - Test object attachment
```

**Example**
```bash
/testobjectattach
```

**Response**

![](https://i.imgur.com/q6LlgUp.png)

# testobjectattachinfinite

**Usage**
```bash
/testobjectattachinfinite  - Test object attachment
```

**Example**
```bash
/testobjectattachinfinite
```

**Response**

![](https://i.imgur.com/q6LlgUp.png)

# testjobmenu

**Usage**
```bash
/testjobmenu - Shows a test job menu
```

**Example**
```bash
/testjobmenu
```

**Response**

![](https://i.imgur.com/QA0HxSv.png)

# testped 

**Usage**
```bash
/testped - A Test Ped. Does not delete itself.
```

**Example**
```bash
/testped
```

**Response**

![](https://i.imgur.com/2NjiI4h.png)

# testactionmenu

**Usage**
```bash
/testactionmenu - A test action menu
```

**Example**
```bash
/testactionmenu
```

**Response**

![](https://i.imgur.com/U51aSdL.png)

# refillVehicle

**Usage**
```bash
/refillVehicle - Refills fuel of an vehicle by administrative power
```

**Example**
```bash
/refillVehicle
```

**Response**

![](https://i.imgur.com/0s0HyvH.png)

# repairVehicle

**Usage**
```bash
/repairVehicle - Repairs an vehicle by administrative power
```

**Example**
```bash
/repairVehicle
```

**Response**

![](https://i.imgur.com/Jhx4Arw.png)

# tempvehicle

**Usage**
```bash
/tempvehicle - Spawn a temporary vehicle
```

**Example**
```bash
/tempvehicle sultanrs
```

# addvehicle

**Usage**
```bash
/addvehicle - Add a vehicle to your character (Database)
```

**Example**
```bash
/addvehicle italirsx
```

# weapon

**Usage**
```bash
/weapon [name] - Get a weapon by name
```

**Example**
```bash
/weapon pistol
```

**Response**

![](https://i.imgur.com/8wUPa9U.png)

# removeallweapons

**Usage**
```bash
/removeallweapons - Remove all weapons
```

**Example**
```bash
/removeallweapons
```

**Response**

![](https://i.imgur.com/ZWQ2KOh.png)

# ac

**Usage**
```bash
/ac [very_long_message] - Chat with other admins
```

**Example**
```bash
/ac Hello World!
```

**Response**

![](https://i.imgur.com/rSQnV21.png)

# apm

**Usage**
```bash
/apm [id] - Sends an administrative private message to the specified player
```

**Example**
```bash
/apm 0 Stop this!
```

**Response**

![](https://i.imgur.com/J6CwMaG.png)

# broadcast

**Usage**
```bash
/broadcast [very_long_message] - Broadcast to whole server
```

**Example**
```bash
/broadcast This is an emergency, throw your computers out of the window!
```

**Response**

![](https://i.imgur.com/BM10rqN.png)

# addhouse

**Usage**
```bash
/addhouse - Open Athenas House Creator
```

**Example**
```bash
/addhouse
```

**Response**

![](https://i.imgur.com/fYx7TSl.png)

# settime

**Usage**
```bash
/settime [hour] - Override time to this hour
```

**Example**
```bash
/settime 22
```

**Response**

![](https://i.imgur.com/1qbCDim.png)

# cleartime

**Usage**
```bash
/cleartime - Clear override for time
```

**Example**
```bash
/cleartime
```

**Response**

![](https://i.imgur.com/cIfAiWg.png)

# setfood

**Usage**
```bash
/setfood [amount] - Set current food level
```

**Example**
```bash
/setfood 100
```

**Response**

![](https://i.imgur.com/hKgNxPn.png)

# setwater

**Usage**
```bash
/setwater [amount] - Set current water level
```

**Example**
```bash
/setwater 100
```

**Response**

![](https://i.imgur.com/RKpkWuG.png)

# setweather

**Usage**
```bash
/setweather [weather_name] - Override all region weathers
```

**Example**
```bash
/setweather XMAS
```

**Response**

![](https://i.imgur.com/QTxxODq.png)

# clearweather

**Usage**
```bash
/clearweather - Turn off weather override
```

**Example**
```bash
/clearweather
```

**Response**

![](https://i.imgur.com/Y8FPNhY.png)

# setfuel

**Usage**
```bash
/setfuel [amount] - Set fuel of current vehicle
```

**Example**
```bash
/setfuel 20
```

# fcreate

**Usage**
```bash
/fcreate [name] - Creates a faction with given name
```

**Example**
```bash
/fcreate Funny Faction
```

# fjoin

**Usage**
```bash
/fjoin [uid] - Quits current Faction and joins another
```

**Example**
```bash
/fjoin 626ab6dff48aad859c90cadb
```