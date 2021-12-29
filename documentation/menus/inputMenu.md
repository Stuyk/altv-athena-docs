---
description: >-
  Create an input menu that will return results by key value pairings.
---

# playerFuncs.emit.inputMenu

Create an input menu that will return results by key value pairings.

_Accessible on Server Side_

# Example

```typescript
function createMenu(player: alt.Player) {
    const menu: InputMenu = {
        title: 'Input Test',
        options: [
            {
                id: 'some-name',
                desc: 'Write something...',
                placeholder: 'Property Name',
                type: InputOptionType.TEXT,
                error: 'Must specify property name.',
            },
            {
                id: 'some-number',
                desc: 'Some kind of number...',
                placeholder: '5000...',
                type: InputOptionType.NUMBER,
                error: 'Must specify property value.',
            },
        ],
        serverEvent: 'cmd:Input:Test',
        generalOptions: {
            submitText: 'Wow Nice Submit',
            cancelText: 'Bad Submit',
            description: 'idk there is some text here now lul',
            skipChecks: false,
        },
    };

    playerFuncs.emit.inputMenu(player, menu);
}

alt.onClient('cmd:Input:Test', (player: alt.Player, results: InputResult[] | null) => {
    if (!results) {
        console.log(`They cancelled the test input.`);
        return;
    }

    console.log(`Results from test input:`);
    console.log(results);
});
```

![](https://i.imgur.com/dwXzSi9.png)