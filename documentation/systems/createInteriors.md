---
description: Learn how to add an interior.
---

# Interior(s)

Interiors are bound to a dimension automatically. Which means that each interior has a unique dimension that belongs to it.

There is currently just a single command to add a house.

# Adding an Interior by Example

If you have a plugin or custom location where you want to add a bunch of houses to the Database. You can use the below example(s) to create two different interior types.

## Global Interior
```ts
await InteriorSystem.add({
    name: 'Diamond Resorts Casino',
    uid: 'diamond-resort-casino',
    outside: { x: 935.1909790039062, y: 46.17036819458008, z: 80.09584045410156 },
    inside: { x: 1089.8856201171875, y: 206.2451629638672, z: -49.5 },
    objects: [],
    system: INTERIOR_SYSTEM.NONE,
    isUnlocked: true,
});
```

## House Interior

```ts
await InteriorSystem.add({
    name: 'Some Cool House',
    uid: 'some-cool-house',
    outside: { x: -841.6432495117188, y: -24.96125030517578, z: 39.39847183227539 },
    inside: { x: -786.8663, y: 315.7642, z: 216.6385 },
    system:
        INTERIOR_SYSTEM.HAS_LOCK |
        INTERIOR_SYSTEM.HAS_OWNER |
        INTERIOR_SYSTEM.HAS_PRICE |
        INTERIOR_SYSTEM.HAS_STORAGE,
    ipl: 'apa_v_mp_h_01_a',
    price: 25000,
    isUnlocked: true,
});
```

_The above examples must use an async function to work_

# Adding a House by Command

It will prompt you for information about the house.

```ts
/addhouse
```

General input for testing...

```
Name: Some Property
Price: 25000
POS: {"x":-783.0387573242188,"y":317.3805236816406,"z":176.80389404296875}
IPL: apa_v_mp_h_01_a
```

You can find interiors by googling for IPL lists and such. Make sure to get door positions and what not as well.