---
description: Create an in-world static pedestrian.
---

# ServerPedController

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

Athena.controllers.ped.append(ped);
```

# Example - Single User

_Keep in mind you should have a player reference to use this_

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

Athena.controllers.ped.addToPlayer(ped);
```

# Play Animations for a Ped

```typescript        
let anim1: Animation = {
    dict: 'random@arrests@busted',
    name: 'idle_a',
    flags: ANIMATION_FLAGS.REPEAT | ANIMATION_FLAGS.UPPERBODY_ONLY,
    duration: -1
}

let anim2: Animation = {
    dict: 'random@arrests',
    name: 'idle_2_hands_up',
    flags: ANIMATION_FLAGS.NORMAL | ANIMATION_FLAGS.STOP_LAST_FRAME,
    duration: -1
}

Athena.controllers.ped.playAnimation('test-ped-1', [anim1,anim2])
```