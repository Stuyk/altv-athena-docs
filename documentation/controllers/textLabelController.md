---
description: Create in-world text that is displayed at a 3D location.
---

# TextLabelController

Creates in-world text that is displayed in-game at a 3D location.

# Example - World

```typescript
const uid = ServerTextLabelController.append({
    data: 'Hello from In-World!',
    pos: { x: 1245.790771484375, y: -3165.754150390625, z: 5.60198450088501 },
});
```

# Example - Single User

_Keep in mind you should have a player reference to use this_

```ts
const uid = ServerTextLabelController.addToPlayer({
    data: 'Simple Delivery',
    pos: { x: 1245.790771484375, y: -3165.754150390625, z: 5.60198450088501 },
});


alt.setTimeout(() => {
    if (!player || !player.valid) {
        return;
    }

    ServerTextLabelController.removeFromPlayer(player, uid);
}, 5000);
```