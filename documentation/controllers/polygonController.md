---
description: Create a ColShape with multiple corners. Great for turfs.
---

# ServerPolygonController

Create a ColShape with multiple corners that can be triggered when a player enters / exits the area.

## Notes on Limitations

This polygon system isn't meant to cover large areas. It can cover small city blocks, stores, etc.

Polygon ColShapes like this are generally considered expensive and should be used sparingly.

# Example

```ts
function generatePolygon() {
    const positions = [
        { x: -1498.1483154296875, y: -677.0752563476562, z: 28.048023223876953 },
        { x: -1491.2274169921875, y: -671.2970581054688, z: 28.943195343017578 },
        { x: -1498.2650146484375, y: -664.248291015625, z: 29.025087356567383 },
        { x: -1463.30908203125, y: -638.9778442382812, z: 29.582916259765625 },
        { x: -1452.80712890625, y: -652.8944091796875, z: 29.582338333129883 },
        { x: -1478.6595458984375, y: -672.8909301757812, z: 29.041839599609375 },
        { x: -1481.732421875, y: -672.94677734375, z: 28.943140029907227 },
        { x: -1493.603271484375, y: -681.1644897460938, z: 27.73985481262207 },
        { x: -1493.603271484375, y: -681.1644897460938, z: 27.73985481262207 },
    ];

    playerFuncs.safe.setPosition(player, positions[0].x, positions[0].y, positions[0].z);

    const streamPolygon: IStreamPolygon = {
        pos: positions[0],
        vertices: positions,
        debug: true,
    };

    const uid = sha256Random(JSON.stringify(streamPolygon));
    streamPolygon.uid = uid;
    streamPolygon.enterEventCall = testEnter;
    streamPolygon.leaveEventCall = testLeave;

    // Setup Temporary Events
    alt.onClient(`${streamPolygon.uid}-test-enter`, testEnter);
    alt.onClient(`${streamPolygon.uid}-test-leave`, testLeave);

    // Setup the Temporary - All Player Polygon
    ServerPolygonController.append(streamPolygon);

    console.log(`Created: ${streamPolygon.uid}`);

    playerFuncs.emit.message(player, `Streamed polygon will be removed in 60 seconds.`);
    alt.setTimeout(() => {
        ServerPolygonController.remove(uid);

        // Remove Temporary Events
        alt.offClient(`${streamPolygon.uid}-test-enter`, testEnter);
        alt.offClient(`${streamPolygon.uid}-test-leave`, testLeave);
    }, 60000);
}

function testEnter<T>(player: T, stream: IStreamPolygon) {
    if (!(player instanceof alt.Player)) {
        return;
    }

    playerFuncs.emit.message(player, `You have entered: ${stream.uid}`);
}

function testLeave<T>(player: T, stream: IStreamPolygon) {
    if (!(player instanceof alt.Player)) {
        return;
    }

    playerFuncs.emit.message(player, `You have left: ${stream.uid}`);
}
```

![](https://i.imgur.com/tMIbeN4.png)