---
description: Send a message to a player.
---

# playerFuncs.emit.message

This is the way to send a message to the in-game chat through server-side functionality.

## Limitations

Messages are meant to not be above `128 characters`. Ensure you are limiting what you are sending in a single line.

## Server Usage

Sending a message can be done like this...

```typescript
playerFuncs.emit.message(player, 'Hello There!');
```

## Colors

If you find yourself in need of colors you can specify a hex color relatively easily. You can also use multiple colors in a single line of text.

```typescript
playerFuncs.emit.message(player, '{FF0000}Hello There!');
```

The above message would display in the color `red`.