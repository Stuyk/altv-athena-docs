---
description: Create particles on-screen for a player or players.
---

# playerFuncs.emit.particle

Create a simple particle emit that displays for the current player or all players near the player. Particles are like fancy effects that can show up in-game like smoke, sparks, etc.

[Particle List by DurtyFree](https://github.com/DurtyFree/gta-v-data-dumps/blob/master/particleEffectsCompact.json)

[Particle List Vespura](https://vespura.com/fivem/particle-list/)

Example in-game

![](https://thumbs.gfycat.com/ElasticSinfulGosling-size_restricted.gif)


_Accessible on Server Side_

# Example

```typescript
// Last parameter if set to 'true' shows it for other players nearby.
playerFuncs.emit.particle(player, {
    pos: player.pos,
    dict: 'core',
    name: 'exp_water',
    duration: 5000,
    scale: 2,
    delay: 0
}, true);
```