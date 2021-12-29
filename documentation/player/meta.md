---
description: Meta lets you easily sync single-sided data for players.
---

# playerFuncs.emit.meta

There may be a use case where you just need a single player to know about a variable on client-side. Let's say their own bank balance for instance.

You want the player to know their balance but it's not important for other players to know about this data. That is what `meta` is for.

## Server Usage

Setting a meta can be done like this...

```typescript
playerFuncs.emit.meta(player, 'bank', 500);
```

## Client Usage

Depending on what you need; you may need to extend the meta interface.

```typescript
import * as alt from 'alt-client';
import * as metaRef from '../../client/extensions/Meta'

// Extends the player interface.
declare module 'alt-client' {
    export interface Meta extends Partial<metaRef.Meta> {
        someNewValue?: null | undefined | string;
    }
}
```

After you can access meta on a player directly

```typescript
const result = alt.Player.local.meta.someNewValue;
```

## Client Listening for Changes

If you want to listen for changes to specific keys there is an event for it. This can only be done on client-side.

```typescript
alt.on(SYSTEM_EVENTS.META_CHANGED, (key: string, value: any, oldValue: any) => {
    console.log(key);
    console.log(`${oldValue} -> ${value}`);
})
```