---
description: >-
  Create an in-world static pedestrian.
---

# PedController

Create an in-world static pedestrian. They do not move, they cannot move, and they will not move.

All players can see 'variations' of the pedestrian.

# Example - World

```typescript
const ped: IPed = {
    uid: `ped-${Math.floor(Math.random() * 500000)}`,
    model: 'u_f_m_casinocash_01',
    pos: {
        x: player.pos.x,
        y: player.pos.y,
        z: player.pos.z - 1,
    },
};

PedController.append(ped);
```

# Example - Single User

```ts
const ped: IPed = {
    uid: `ped-${Math.floor(Math.random() * 500000)}`,
    model: 'u_f_m_casinocash_01',
    pos: {
        x: player.pos.x,
        y: player.pos.y,
        z: player.pos.z - 1,
    },
};

PedController.addToPlayer(ped);
```