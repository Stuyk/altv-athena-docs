---
description: Saving player data, new data, etc.
---

# Athena.player.save

There are a few things that are automatically saved to the database every `5 seconds` but there are certain things that are obviously not saved all the time.

**Saved Every 5 Seconds**

* position
* health
* armour
* hours
* water
* food

_Saved automatically_

**Conditional Saves**

* inventory
* equipment
* toolbar
* death state
* wanted
* faction
* appearance
* info
* cash
* bank

_Saved based on things that trigger them_

## Save Injections

Save injections are a simple way to define an object with multiple keys, and values to save. Save injections should be used sparingly.

Save injections work as a `callback` meaning that it runs a function before it sends back the data to save. With a save injection you are going to want to dynamically apply this data based on what is needed.

**Important**

You should only add a save injection `once`. It will automatically call the callback every 5 seconds to add to the saved data.

**Example**

```typescript
Athena.player.save.addSaveInjection((player: alt.Player) => {
    return { hello: 'world' };
});
```

_The above automatically saves the key `hello` and value `world` every 5 seconds_

## Conditional Saving

You do not need a key to exist in the `Character` interface to save data. However, it is best practice to extend the `Character` interface in your plugin to apply new values.

**Extending the Interface**

```typescript
import * as alt from 'alt-server';
import * as charRef from '../../../shared/interfaces/character';

// Extends the player interface.
declare module 'alt-server' {
    export interface Character extends Partial<charRef.Character> {
        someNewValue?: null | undefined | string;
    }
}
```

**The Conditional Save**

```typescript
Athena.player.save.field(player, 'someNewValue', player.data.someNewValue);
```

_Used for single key and value_

OR

```typescript
Athena.player.save.partial(player, { someNewValue: player.data.someNewValue });
```

_Used for multiple keys and values_