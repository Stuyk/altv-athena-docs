---
description: Controllers are server-side classes that control in-world elements.
---

# What is a Controller?

A Controller in Athena's case is a system that controls in-world streamed elements, or general behavior when a player is around a certain point in-game. Controllers can be text labels creators, marker creators, object creators, etc.

```ts
Athena.controllers.x
```

## What are they used for?

Showing different things to the player depending on their position in the world. Controllers are incredibly useful for creating custom functionality when your player base is moving around the map.

## What is a uid?

A `uid` stands for a unique identifier. This is used to potentially remove a blip, marker, etc. When removing a created element from a player you will always need a `uid` to remove it. This goes for all `world` based controllers as well.

See the other controllers to see how a `uid` is used.