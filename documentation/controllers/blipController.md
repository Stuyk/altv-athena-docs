---
description: Create in-world blips for a single player or everyone.
---

# ServerBlipController

Creates in-world blip that is displayed in-game on the minimap.

![](https://i.imgur.com/mDyR1r1.png)

Blip and Color List(s): 

- [alt:V Blip List](https://wiki.altv.mp/wiki/GTA:Blips)
- [FiveM Blip List](https://docs.fivem.net/docs/game-references/blips/)
- [RageMP Blip List](https://wiki.rage.mp/index.php?title=Blips)

# Example - World

```typescript
const uid = ServerBlipController.append({
    sprite: 616,
    color: 5,
    pos: { x: 0, y: 0, z: 0 },
    scale: 1,
    shortRange: true,
    text: 'Simple Delivery',
});
```

# Example - Single User

_Keep in mind you should have a player reference to use this_

```ts
const uid = ServerBlipController.addToPlayer(player, {
    sprite: 616,
    color: 5,
    pos: { x: 0, y: 0, z: 0 },
    scale: 1,
    shortRange: true,
    text: 'Simple Delivery',
});


alt.setTimeout(() => {
    if (!player || !player.valid) {
        return;
    }

    ServerBlipController.removeFromPlayer(player, uid);
}, 5000);
```