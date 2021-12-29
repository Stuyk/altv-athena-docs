---
description: Playing ped natives in a specific order.
---

# playerFuncs.emit.taskTimeline

Task timelines can be incredibly useful but they are also very limited in functionality. They basically allow you to override a player's inputs and make them do something specific with natives on client-side.

Understanding how they work though is a bit tricky.

## What Makes a 'Task'

Tasks are just natives with slightly obscure parameters.

Let's take the `native.taskGoToCoordsAnyMeans` as an example.

**Normal Native**

```typescript
taskGoToCoordAnyMeans(ped: number | alt.Player, x: number, y: number, z: number, speed: number, p5: any, p6: boolean, walkingStyle: number, p8: number);
```

**Task Object**

Notice how we do not specify `ped` in the parameters. 

That is inheritely added when we call the task.

Our arguments we are passing just remove the `ped` entry and we have very similar arguments.

```typescript
{
    nativeName: 'taskGoToCoordAnyMeans',
    params: [openSpot.pos.x, openSpot.pos.y, openSpot.pos.z, 1, null, false, 786603, 0],
    timeToWaitInMs: 5000,
}
```


## Simple Walking to and From Task

Let's say that when you start a job you want them to walk from Point A to Point B automatically. This can be achieved through a task timeline.

```typescript
const tasks: Array<Task> = [
    {
        nativeName: 'taskGoToCoordAnyMeans',
        params: [openSpot.pos.x, openSpot.pos.y, openSpot.pos.z, 1, null, false, 786603, 0],
        timeToWaitInMs: 5000,
    },
];

playerFuncs.emit.taskTimeline(player, tasks);
```

_openSpot is a pre-defined parameter_

## Preview of the Above Example

![](https://thumbs.gfycat.com/JubilantDearHousefly-size_restricted.gif)

_In the above example I never touched my keyboard to perform the walking_