---
description: >-
    Create an infinitely scaling menu that can have multiple callbacks, options, etc.
---

# playerFuncs.emit.createCredits

Create an infinitely scaling menu that can have multiple callbacks, options, etc.

![](https://i.imgur.com/XKdwj0i.png)

## Benefits

-   Easily Customizable
-   Infinitely Scaleable
-   Used Server or Client Side
-   Can be Dynamically Created
-   1 - 9 Hotkeys
-   Arrow Key Usage
-   Enter Keypress
-   Backspace Keypress

_Accessible on Server Side_

# Example

```ts
function showActionMenu(player: alt.Player) {
// Create an action called facePalm that uses the Animation Interface.
    const facePalm: Action = {
        eventName: 'animation:Action:Server',
        isServer: true,
        data: {
            dict: 'anim@mp_player_intupperface_palm',
            name: 'idle_a',
            duration: 3000,
            flags: ANIMATION_FLAGS.UPPERBODY_ONLY,
        },
    };

    // Create an action called gangSign that uses the Animation Interface.
    const gangSign: Action = {
        eventName: 'animation:Action:Server',
        isServer: true,
        data: {
            dict: 'mp_player_int_uppergang_sign_a',
            name: 'mp_player_int_gang_sign_a',
            duration: 3000,
            flags: ANIMATION_FLAGS.UPPERBODY_ONLY,
        },
    };

    // Create the menu and send it to the player/
    playerFuncs.set.actionMenu(
        player,
        // The Menu
        {
            // Option 1 in the menu is a single event.
            'Option 1': {
                eventName: 'hello:From:Client',
                isServer: true,
            },
            // Animations in the menu contains 2 more events. You can also add another menu.
            Animations: {
                'Face Palm': facePalm,
                'Gang Sign': gangSign,
                // Creates a menu in the menu.
                'More Animations': {
                    'Face Palm 2': facePalm, // Just using the same one for testing purposes
                    'Gang Sign 2': gangSign,
                    // Creates a menu in the menu in the menu
                    'More More Animations': {
                        'Face Palm 3': facePalm, // Just using the same one for testing purposes
                        'Gang Sign 3': gangSign,
                        // etc...
                    },
                },
            },
        },
    );
}

alt.onClient('hello:From:Client', (player) => {
    playerFuncs.emit.message(player, `Got menu option from client.`);
});

alt.onClient('animation:Action:Server', (player, data: Animation) => {
    if (!data) {
        return;
    }

    playerFuncs.emit.animation(player, data.dict, data.name, data.flags, data.duration);
});
```