---
description: Create in-world help text that is displayed in a 3D location.
---

# WorldNotificationController

Creates in-world help text that is displayed in-game at a 3D location.

## Note on Limitations

Can only render one of these at a time in-world. Try to use them sparingly.

# Example - World

```typescript
const uid = WorldNotificationController.append({
    text: 'Hello World!',
    type: WORLD_NOTIFICATION_TYPE.ARROW_BOTTOM,
    pos: { ...player.pos },
});
```

# Example - Single User

_Keep in mind you should have a player reference to use this_

```ts
const uid = WorldNotificationController.addToPlayer(player, {
    text: 'Hello World!',
    type: WORLD_NOTIFICATION_TYPE.ARROW_BOTTOM,
    pos: { ...player.pos },
});

alt.setTimeout(() => {
    if (!player || !player.valid) {
        return;
    }

    WorldNotificationController.removeFromPlayer(player, uid);
}, 5000);
```