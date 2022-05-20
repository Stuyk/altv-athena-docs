---
description: Learn how to build a WheelMenu in the Athena Framework on both sides.
---

# Summary

Wheel Menu's are exactly how they sound. It's a wheel with a bunch of items you can select. Those items inside of the menu can have other items buried behind it.

* To create a nested WheelMenu just add more then 8 Options and scroll the page (handled automatically)

# Video Guide

- Currently not available


# Basic Example - Serverside

This example simply has an event where if an event is passed from server to server. It will
log the current data the WheelMenu Option holds into the server console.

```typescript
InteractionController.add({
    position: { x: 0, y: 1, z: 71 },
    description: 'Open Wheelmenu',
    callback: (player: alt.Player) => {
        const menu: Array<IWheelOption> = [
            {
                name: 'Test the menu!',
                icon: 'icon-house',
                color: 'red',
                data: [
                    {
                        description: 'Test the menu!',
                        icon: 'current icon is => icon-house',
                        color: 'current color is => red',
                    }
                ],
                doNotClose: false,
                emitServer: 'WheelMenu-TestEvent',
            },
        ];
        Athena.player.emit.wheelMenu(player, 'Hello World!', menu);
    },
});

alt.onClient('WheelMenu-TestEvent', (player: alt.Player, data: Array<any>) => {
    console.log('WheelMenu-TestEvent got fired! Hello World!');
    console.log(`Current Data of test-event => ${JSON.stringify(data)}`);
});
```

# Basic Example - Clientside
This example simply has an callback where data is passed into. It will log the current data the WheelMenu Option holds into the developer (F8) console.
```typescript
alt.on('keydown', (key) => {
    if(key === 71) {
        const menu: Array<IWheelOptionExt> = [
            {
                name: 'Test the menu!',
                icon: 'icon-house',
                color: 'red',
                data: [
                    {
                        description: 'Test the menu!',
                        icon: 'current icon is => icon-house',
                        color: 'current color is => red',
                    }
                ],
                doNotClose: false,
                callback: (data: Array<string>) => {
                    console.log(`Data of Clientsided WheelMenu => ${JSON.stringify(data)}`);
                }
            },
        ];
        WheelMenu.open('Clientsided', menu);
    }
});
```
# Valid Options

- Disclaimer: The IWheelOption will work on both sides, while the IWheelOptionExt will only work on the clientside.


```typescript
export interface IWheelOption {
    /**
     * The name of this option.
     *
     * @type {string}
     * @memberof IWheelOption
     */
    name: string;
    /**
     * A unique identifier for this option.
     *
     * If not specified one will automatically be created.
     *
     * @type {string}
     * @memberof IWheelOption
     */
    uid?: string;

    /**
     * A plain text color for the icon and text color.
     *
     * ie. `red`, `green`, `yellow`, etc.
     *
     * @type {string}
     * @memberof IWheelOption
     */
    color?: string;

    /**
     * An icon from the `icons` page in the pages.
     *
     * ie. `icon-home`
     *
     * @type {string}
     * @memberof IWheelOption
     */
    icon?: string;

    /**
     * Do not close the wheel menu after executing this option.
     *
     * @type {boolean}
     * @memberof IWheelOption
     */
    doNotClose?: boolean;

    /**
     * From the client, call a specific server event through alt.emitServer
     *
     * @type {string}
     * @memberof IWheelOption
     */
    emitServer?: string;

    /**
     * From the client, emit a client event through alt.emit
     *
     * @type {string}
     * @memberof IWheelOption
     */
    emitClient?: string;

    /**
     * Any data that you want to pass through a callback or an event.
     *
     * @type {Array<any>}
     * @memberof IWheelOptionExt
     */
    data?: Array<any>;
}

export interface IWheelOptionExt extends IWheelOption {
    /**
     * A callback that will only work on client-side.
     *
     * @memberof IWheelOptionExt
     */
    callback?: (...args: any[]) => void;
}
```