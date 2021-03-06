---
description: Create in-world help text that is displayed in a 3D location.
---

# WorldNotificationController

Creates in-world help text that is displayed in-game at a 3D location.

## Note on Limitations

Can only render one of these at a time in-world. Try to use them sparingly.

# Example - World

```typescript
const uid = Athena.controllers.notification.append({
    text: 'Hello World!',
    type: WORLD_NOTIFICATION_TYPE.ARROW_BOTTOM,
    pos: { ...player.pos },
});
```

# Example - Single User

_Keep in mind you should have a player reference to use this_

```typescript
const uid = Athena.controllers.notification.addToPlayer(player, {
    text: 'Hello World!',
    type: WORLD_NOTIFICATION_TYPE.ARROW_BOTTOM,
    pos: { ...player.pos },
});

alt.setTimeout(() => {
    if (!player || !player.valid) {
        return;
    }

   Athena.controllers.notification.removeFromPlayer(player, uid);
}, 5000);
```