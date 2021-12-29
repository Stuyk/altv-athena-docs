---
description: >-
  Temporarily or infinitely attach an object to a client.
---

# playerFuncs.emit.objectAttach

Allows users to have objects attached to their players. They can be temporarily added or added for the entire play session.

_Accessible on Server Side_

# Example

```ts
const attachable: IAttachable = {
    model: 'prop_tool_fireaxe',
    bone: 57005,
    pos: {
        x: 0.1,
        y: -0.1,
        z: -0.02,
    },
    rot: {
        x: 80,
        y: 0,
        z: 170,
    },
};

playerFuncs.emit.objectAttach(player, attachable, 5000);
```

![](https://i.imgur.com/TucLJqC.png)