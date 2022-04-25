---
description: Create a simple progress bar.
---

# Athena.player.emit.createProgressBar

Progress bars are server-based and controlled server-side. They are not distributed to several players but can be shown to a single user. They're based on a set period of time between a starting point and an ending point.

![](https://thumbs.gfycat.com/HonorableInfiniteCorydorascatfish-size_restricted.gif)

_Accessible on Server Side_

## Creation

Creation very simple and will always return a `uid` if not specified.

```typescript
const uid = Athena.player.emit.createProgressBar(player, {
    color: new alt.RGBA(0, 255, 0, 255),
    distance: 5,
    position: player.pos,
    milliseconds: 5000,
    percentageEnabled: true,
});
```

## Clearing

If for some reason you need to clear the progress bar early you can use the uid to clear it.

```typescript
const uid = Athena.player.emit.createProgressBar(player, {
    color: new alt.RGBA(0, 255, 0, 255),
    distance: 5,
    position: player.pos,
    milliseconds: 5000,
    percentageEnabled: true,
});

Athena.player.emit.removeProgressBar(player, uid);
```

## Example

This progress bar lasts 5 seconds.

```typescript
const uid = Athena.player.emit.createProgressBar(player, {
    color: new alt.RGBA(0, 255, 0, 255),
    distance: 5,
    position: player.pos,
    milliseconds: 5000,
    percentageEnabled: true,
});
```