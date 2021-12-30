---
description: Learn how to add custom behavior to default inventory.
---

# Inventory Rules

Inventory Rules are these custom rules that let you deny a specific action from being performed when a player moves an item around in their inventory.

## Preface

You should not be using inventory rules as a way to listen to item movements, and where items are going. These rules are applied before any items are added, removed, etc. Which means that it is not a guarenteed way to see if an item made it to a specific slot and such.

These just let you stop certain things from happening such as maybe dropping a very unique key on the ground.

## The Rules

These are the events you can tap into to deny, or accept a specific action from happening.

```typescript
export enum INVENTORY_RULES {
    // Inventory <-> Toolbar
    FROM_TOOLBAR_TO_INVENTORY = 'from-toolbar-to-inventory',
    FROM_INVENTORY_TO_TOOLBAR = 'from-inventory-to-toolbar',
    // Inventory <-> Equipment
    FROM_EQUIPMENT_TO_INVENTORY = 'from-equipment-to-inventory',
    FROM_INVENTORY_TO_EQUIPMENT = 'from-inventory-to-equipment',
    // Inventory <-> Ground
    FROM_GROUND_TO_INVENTORY = 'from-ground-to-inventory',
    FROM_INVENTORY_TO_GROUND = 'from-inventory-to-ground',
    // Equipment <-> Toolbar
    FROM_EQUIPMENT_TO_TOOLBAR = 'from-equipment-to-toolbar',
    FROM_TOOLBAR_TO_EQUIPMENT = 'from-toolbar-to-equipment',
    // Equipment <-> Ground
    FROM_EQUIPMENT_TO_GROUND = 'from-equipment-to-ground',
    FROM_GROUND_TO_EQUIPMENT = 'from-ground-to-equipment',
    // Toolbar <-> Ground
    FROM_TOOLBAR_TO_GROUND = 'from-toolbar-to-ground',
    FROM_GROUND_TO_TOOLBAR = 'from-ground-to-toolbar',
}
```

## Customizing Rules

The general formula is to take any one of the events above that you want to apply a rule to and then simply add rules based around the item that is being moved.

In the example below we are going to prevent players from equipping an RPG in their toolbar.

What we'll do is check if the name includes RPG and if it does we'll just return `false` so the inventory system knows it should fail this action.

```typescript
function theRule(item: Item, selectSlot: number, endSlot: number, ruleName: string): boolean {
    if (item.name.includes('RPG')) {
        return false;
    }

    return true;
}


InventoryController.addRule(INVENTORY_RULES.FROM_INVENTORY_TO_TOOLBAR, theRule);
```

_It's that simple to deny an item from making it to a certain point._