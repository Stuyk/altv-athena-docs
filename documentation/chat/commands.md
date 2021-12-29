---
description: >-
    Create a command that players can call through chat.
---

# ChatController.addCommand

Create a command that players can call through chat.

_Accessible on Server Side_

## Note on Permissions

Permissions are a hard-coded bitwise enum. What does that mean?

If you want a command to be accessible to admins only then you do the following:

```typescript
PERMISSIONS.ADMIN
```

If you want a command to be accessible to admins and moderators then you do the following:

```typescript
PERMISSIONS.MODERATOR | PERMISSIONS.ADMIN
```

_The | operator basically stands for OR_

# Example

```typescript
ChatController.addCommand('mycommand', '/mycommand - does stuff', PERMISSIONS.NONE, handleCommand);

function handleCommand(player: alt.Player) {
    player.emit.message(`Hello from server-side`);
}
```