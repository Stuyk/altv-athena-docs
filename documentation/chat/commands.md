---
description: >-
    Create a command that players can call through chat.
---

# addCommand

Create a command that players can call through chat.

```
Athena.controllers.chat.addCommand
```

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

# Example 1

Usage - One command

```typescript
Athena.controllers.chat.addCommand('mycommand', '/mycommand - does stuff', PERMISSIONS.NONE, handleCommand);

function handleCommand(player: alt.Player) {
    Athena.player.emit.message(`Hello from server-side`);
}
```

# Example 2

Usage - One command with one handler function.

```typescript
class CommandHolder {
    @command('test', '/test [arg1] [arg2] - Prints some args', PERMISSIONS.NONE)
    static doSomething(player: alt.Player, arg1: string, arg2: string) {
        console.log(arg1, arg2);
    }
}
```

# Example 3

Usage - Multiple commands with one handler function.

```typescript
class CommandHolder {
    @command(['test', 'testagain'], '/test [arg1] [arg2] - Prints some args', PERMISSIONS.NONE)
    static doSomething(player: alt.Player, arg1: string, arg2: string) {
        console.log(arg1, arg2);
    }
}
```