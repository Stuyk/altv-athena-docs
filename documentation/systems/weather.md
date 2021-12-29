---
description: Learn how weather works in Athena
---

# Weather

The weather system in Athena is a bit different than normal systems. However, I will do my best to explain how this system works and why it was made in this way.

Rather than having region specific weather, weather works in 'waves'. A 'wave' is a specific weather type based on certain coordinates in the game.

**Example Image with Region Index**

![](https://i.imgur.com/OjPYe2C.png)

## Weather Rotation

The default weather rotation in Athena is as follows:

```typescript
[
    'EXTRASUNNY',
    'EXTRASUNNY',
    'CLEAR',
    'CLOUDS',
    'OVERCAST',
    'RAIN',
    'THUNDER',
    'RAIN',
    'FOGGY',
    'OVERCAST',
    'CLEARING',
]
```

Which means that by default the starting weather for each region is as follows.

```typescript
0 -> 'EXTRASUNNY',
1 -> 'EXTRASUNNY',
2 -> 'CLEAR',
3 -> 'CLOUDS',
4 -> 'OVERCAST',
```

When the weather rotates it takes the last element in the array and moves it to the front. Which means the next weather in the cycle for index 0 is `CLEARING` based on the default weather.

## Customizing the Weather Rotation

You can technically insert any weather type into the weather rotation and the rotation can be as long as you want it to be. Here's an example of how to increase the rotation and have longer hours of each weather type.

It's a simple system but can easily be customized to create unique and predictable weather patterns based on your server needs.

```typescript
[
    'EXTRASUNNY',
    'EXTRASUNNY',
    'EXTRASUNNY',
    'EXTRASUNNY',
    'CLEAR',
    'CLEAR',
    'CLOUDS',
    'CLOUDS',
    'CLOUDS',
    'OVERCAST',
    'OVERCAST',
    'OVERCAST',
    'RAIN',
    'RAIN',
    'RAIN',
    'THUNDER',
    'THUNDER',
    'THUNDER',
    'RAIN',
    'RAIN',
    'RAIN',
    'FOGGY',
    'FOGGY',
    'FOGGY',
    'OVERCAST',
    'OVERCAST',
    'CLEARING',
    'CLEARING',
    'CLEARING',
    'CLEARING',
]
```