---
description: Learn how to add interactions.
---

# What is an Interaction?

An interaction is an invisible position on the map where if a player walks over this spot they may press their interaction button to trigger something. This can be anything from a menu, text, etc.

Keep in mind that Interactions are **GLOBAL** which means all players can access them. However, you can write an `if` statement inside of the intraction trigger to prevent the code from going further.

All interactions are `server-side` so if you want it to trigger `client-side` you will need to emit an event to the client to trigger it. This will ensure that interaction(s) are synced through `server-side` first.

# Creation

This will create a ColShape where the player can press their interaction button to trigger something.

_Keep in mind that the paths of these files may vary._

```typescript
function doThisWhenInteractionIsPressed(player: alt.Player) {
    Athena.player.emit.message(player, 'Nice!');
}

function GenerateInteractions() {
    Athena.controllers.interaction.add({
        uid: 'interaction-do-something',
        type: 'interaction:DoSomething',
        position: { x: 402.397308, y: -1029.67, z: 29.34688 },
        description: 'Neato',
        callback: doThisWhenInteractionIsPressed
    });
}

GenerateInteractions();
```

# Removal

This will remove an interaction and its associated ColShape.

_Keep in mind that the paths of these files may vary._

```typescript
import * as alt from 'alt-server';

const UID = 'do-something';
const INT_TYPE = 'interaction:DoSomething';

function doThisWhenInteractionIsPressed(player: alt.Player) {
    Athena.player.emit.message(player, 'Removing Interaction!');
    Athena.controllers.interaction.remove(INT_TYPE, UID);
}

function GenerateInteractions() {
    Athena.controllers.interaction.add({
        uid: UID,
        type: INT_TYPE,
        position: { x: 402.397308, y: -1029.67, z: 29.34688 },
        description: 'Remove this interaction on press.',
        callback: doThisWhenInteractionIsPressed
    });
}

GenerateInteractions();
```