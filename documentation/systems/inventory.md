---
description: Learn how to add items to your game mode.
---

# Adding Items

 [Keywords and Inventory Syntax](#keywords-and-inventory-syntax)
- [Adding Items](#adding-items)
- [Keywords and Inventory Syntax](#keywords-and-inventory-syntax)
- [Difference Between Slot and Index](#difference-between-slot-and-index)
- [Using Inventory Functions](#using-inventory-functions)
- [Deep Cloning Objects](#deep-cloning-objects)
- [Add / Create Items](#add--create-items)
  - [Giving Players Items](#giving-players-items)
  - [Removing Players Items](#removing-players-items)
  - [Working with Player Inventories](#working-with-player-inventories)
  - [Item Effects](#item-effects)
    - [Item Example](#item-example)
  - [Item Factory](#item-factory)

# Keywords and Inventory Syntax

The inventory is setup as a single array. The `slot` determines how the item is displayed in the inventory interface and the `index` is where the item is in the array.

So accessing individual items for a player is something like...

```typescript
player.data.inventory[0]
```

Here's what they may look like from a visual perspective.

```typescript
[
    {
        name: 'Burger',
        description: 'A delicious burger...',
        quantity: 1,
        slot: 1
    }
    {
        name: 'Taco',
        description: 'A classic Mexican street taco.',
        quantity: 0,
        slot: 5
    }
]
```

_In the above example if we used `player.data.inventory[0]` we sould get the burger item_

# Difference Between Slot and Index

Slot is where the item is placed when the item is displayed to the user.

Index is where the item is placed inside of the array.

If a function returns an index for an inventory item then it means you can get the item like...

```typescript
player.data.inventory[index]
```

If the function returns a slot for an inventory item. Then it means you need to get it like this...

```typescript
const item = player.data.inventory.find(x => x.slot === someSlotNumber);
```

# Using Inventory Functions

The inventory does not always save after each update. If you use any inventory functions you should be throwing a save and a sync immediately after performing any functions.

```typescript
playerFuncs.save.field(player, 'inventory', player.data.inventory);
playerFuncs.sync.inventory(player)
```

# Deep Cloning Objects

Because these objects can be rather complicated there is a simple function that does a deep clone of an object and ensuring that you're not modifying the original data. You should always deep clone an object before adding it to a player inventory to prevent data from referencing other inventories and such.

```typescript
const item = deepCloneObject(originalItem) as Item;
// Then add the item somewhere...
```

# Add / Create Items

Items come in a variety of flavors but their general creation follows a specific template.

```typescript
const refItem: Item = {
    name: `Micro SMG`,
    uuid: `some_hash_thing`,
    description: `Debug: Should be able to go to toolbar. Cannot go to equipment. Is a weapon.`,
    icon: 'gun',
    slot: 4,
    quantity: 1,
    behavior: ITEM_TYPE.CAN_DROP | ITEM_TYPE.CAN_TRADE | ITEM_TYPE.IS_TOOLBAR | ITEM_TYPE.IS_WEAPON,
    data: {
        hash: 0x13532244 // Used as the weapon hash for giving the player a weapon
    }
};
```

Now when you create templates for items and want to use a reference item like the one above. You must perform a deep copy of that item reference.

```typescript
const newItem: Item = deepCloneObject<Item>(refItem);
```

After making the deepl clone of your object you can modify it.

```typescript
newItem.name = `Super Cool Item`;
newItem.icon = 'crate';
```

## Giving Players Items

More often than not the one location you will be putting new items in the player's inventory. Athena comes with a handful of utility functions to help you add and remove items from a player's inventory.

Here's the basic gist of it.

```typescript
const slotInfo = playerFuncs.inventory.getFreeInventorySlot(player);
playerFuncs.inventory.inventoryAdd(player, newItem, slotInfo.slot);

// Don't forget to save the inventory after adding it.
playerFuncs.save.field(player, 'inventory', player.data.inventory);
playerFuncs.sync.inventory(player)
```

## Removing Players Items

If you need to remove a player's item you can run the following functions to check if it is removed.

```typescript
const slotInfo: { slot: number; tab: number } | null = playerFuncs.inventory.isInInventory({ name: 'Micro SMG' });
if (!slotInfo) {
    playerFuncs.emit.message(player, `Item was not found!`);
    return;
}

const item: Item = playerFuncs.inventory.getInventoryItem(player, slotInfo.slot);
if (!item) {
    playerFuncs.emit.message(player, `Item was not found!`);
    return;
}

const didRemoveItem: boolean = playerFuncs.inventory.inventoryRemove(player, slotInfo.slot);
if (!didRemoveItem) {
    playerFuncs.emit.message(player, `Did not find item to remove!`);
    return;
}

alt.log(`The item was removed!`);

playerFuncs.save.field(player, 'inventory', player.data.inventory);
playerFuncs.sync.inventory(player)
```

## Working with Player Inventories

Depending on what you want to do with the player inventory there are a ton of ways to work with it. However, more often than not the most common use case for working with an inventory is finding an item and removing it. Which is what we'll be covering here.

```typescript
function findPlayerBurgerItem(player: alt.Player) {
    const itemInfo = playerFuncs.inventory.isInInventory(player, { name: 'Burger' });
    if (!itemInfo) {
        // Item does not exist.
        return;
    }

    // Get the found item, remove it, save inventory, and sync inventory.
    const item = player.data.inventory[itemInfo.index];
    if (!playerFuncs.inventory.inventoryRemove(player, itemInfo.slot)) {
        // Did not remove item successfully
        return;
    }

    playerFuncs.save.field(player, 'inventory', player.data.inventory);
    playerFuncs.sync.inventory(player)
}
```

## Item Effects

If you wish to use item effects when you consume an item it's quite simple.

You will need to add a `event` to the `data` section of your item.

When the item is consumed it will reduce the quantity by `1` and then call that event over `alt.emit`.

It can then be recieved with `alt.on`.

### Item Example

```typescript
const teleporterItem: Item = {
    name: `Teleporter`,
    uuid: `teleporter`,
    description: `Debug: Should be able to call an event with this`,
    icon: 'teleporter',
    slot: 5,
    quantity: 1,
    behavior: ITEM_TYPE.CAN_DROP | ITEM_TYPE.CAN_TRADE | ITEM_TYPE.CONSUMABLE,
    data: {
        event: 'effect:Teleport'
    }
};

alt.on('effect:Teleport', (player: alt.Player, item: Item) => {
    playerFuncs.emit.message(player, `You consumed ${item.name}`);
});
```

## Item Factory

The item registry is a relatively new concept but it allows you to create item `templates` that can be fetched from the Database so you're not storing them in your code as much. Your mileage may vary on this system as I personally do not use it very much.

Below is an example of how to create, fetch, and quantify an item before giving it to a player.

```typescript
async function createSomeItem(player: alt.Player) {
    const teleporterItem: Item = {
        name: `Teleporter`,
        dbName: `cool-teleporter`,
        description: `Debug: Should be able to call an event with this`,
        icon: 'teleporter',
        slot: 5,
        quantity: 1,
        behavior: ITEM_TYPE.CAN_DROP | ITEM_TYPE.CAN_TRADE | ITEM_TYPE.CONSUMABLE,
        data: {
            event: 'effect:Teleport'
        }
    };

    await ItemFactory.add(teleporterItem);
}

async function giveSomeItem(player: alt.Player) {
    const newItem = await ItemFactory.get('cool-teleporter');
    if (!newItem) {
        // Item does not exist
        return;
    }

    newItem.quantity = 1;

    const slotInfo = playerFuncs.inventory.getFreeInventorySlot(player);
    if (!slotInfo) {
        // No Room
        return;
    }

    if (!playerFuncs.inventory.inventoryAdd(player, newItem, slotInfo.slot)) {
        // Could not add item
        return;
    }

    // Don't forget to save the inventory after adding it.
    playerFuncs.save.field(player, 'inventory', player.data.inventory);
    playerFuncs.sync.inventory(player)
}
```