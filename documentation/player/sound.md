---
description: Playing Sounds for a Player
---

# Summary

Sounds can be played in 3 different ways.

* 2D - Custom
* 3D - Custom
* GTA:V Interface Sounds - Not Custom

Is is suggested to take a look at [Custom Sounds](../misc/createCustomSounds.md) to understand how they are implemented and created.

However, interface sound list can be found here:

[https://altv.stuyk.com/docs/articles/tables/frontend-sounds.html](https://altv.stuyk.com/docs/articles/tables/frontend-sounds.html)

# playerFuncs.emit.sound2D

Sounds are played in both channels of their speakers.

```typescript
playerFuncs.emit.sound2D(player, 'item_error');
```

# playerFuncs.emit.sound3D

Sounds are played based on where the entity is.

The last parameter is either a `player` or a `vehicle`.

```typescript
 playerFuncs.emit.sound3D(player, 'item_equip', player);
```

# playerFuncs.emit.soundFrontend

Sounds are played in both channels of their speakers.

```typescript
playerFuncs.emit.soundFrontend(player, 'Hack_Failed', 'DLC_HEIST_BIOLAB_PREP_HACKING_SOUNDS');
```