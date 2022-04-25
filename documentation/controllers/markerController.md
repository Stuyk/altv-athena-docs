---
description: Create in-world markers for a single player or everyone.
---

# ServerMarkerController

Creates an in-world hologram that can be walked through. See the image below.

![](https://i.imgur.com/VJhIOBn.png)

Marker List(s): 

- [alt:V Marker List](https://wiki.altv.mp/wiki/GTA:Markers)
- [FiveM Marker List](https://docs.fivem.net/docs/game-references/markers/)
- [RageMP Marker List](https://wiki.rage.mp/index.php?title=Markers)

# Example - World

```typescript
const uid = Athena.controllers.marker.append({
    pos: {x: 0, y: 0, z: 0},
    color: new alt.RGBA(255, 255, 255, 150),
    type: MARKER_TYPE.CYLINDER,
    scale: new alt.Vector3(1, 1, 1),
});
```

# Example - Single User

_Keep in mind you should have a player reference to use this_

```typescript
const uid = Athena.controllers.marker.addToPlayer(player, {
    pos: {x: 0, y: 0, z: 0},
    color: new alt.RGBA(255, 255, 255, 150),
    type: MARKER_TYPE.CYLINDER,
    scale: new alt.Vector3(1, 1, 1),
});


alt.setTimeout(() => {
    if (!player || !player.valid) {
        return;
    }

    Athena.controllers.marker.removeFromPlayer(player, uid);
}, 5000);
```