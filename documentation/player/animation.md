---
description: Animations can be played from server-side.
---

# playerFuncs.emit.animation

In most cases you'll be wanting to play an animation from server-side as that's where a majority of our logic is going to be written. There's a player function to do this with ease.

## Animation Flags

Animation flags are a way to specify how an animation looks in-game. They're built around bitwise functionality so you combine a handful of them to get the desired effect you want.

```typescript
export enum ANIMATION_FLAGS {
    NORMAL = 0,
    REPEAT = 1,
    STOP_LAST_FRAME = 2,
    UPPERBODY_ONLY = 16,
    ENABLE_PLAYER_CONTROL = 32,
    CANCELABLE = 120
}
```

Example

```typescript
const foreverLastFrame = ANIMATION_FLAGS.STOP_LAST_FRAME | ANIMATION_FLAGS.UPPERBODY_ONLY;
```

## Usage

Playing an animation can be done like this...

**Input Values**

```typescript
// Plays an animation forever.
playerFuncs.emit.animation(player, 'dictionary', 'name', flags, -1);
```

**Example**

```typescript
// Plays for 12 seconds.
playerFuncs.emit.animation(
    player,
    'mp_car_bomb',
    'car_bomb_mechanic',
    ANIMATION_FLAGS.NORMAL | ANIMATION_FLAGS.REPEAT,
    12000,
);
```

## Stopping Animation

If you ever find yourself needing to stop an animation there's a simple function to clear it.

```typescript
playerFuncs.emit.clearAnimation(player);
```

## Scenarios

Scenarios are just really complex animations that are generally long.

[Scenario List](https://github.com/Santagain/gtav-scenarios)

```typescript
// Plays for 10 seconds.
playerFuncs.emit.scenario(player, `WORLD_HUMAN_AA_SMOKE`, 10000);
```