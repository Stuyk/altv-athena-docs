---
description: Currency related commands for individual players.
---

# Athena.player.currency

All currency related functionality for managing cash and bank values.

_Accessible on Server Side_

## Currency Types

Currency currently comes in two types. There is `bank` and `cash`.

Cash is a value that can be considered `on-hand` while `bank` is money stored in a 'safe' location. They're effectively the same but it's dependent on you to decide how to use them and the rules behind each currency type.

## Set Currency

This is pretty much just for administrative related things. Currency can bet set to an exact value.

```typescript
Athena.player.currency.set(player, CurrencyTypes.CASH, 50000)
```

```typescript
Athena.player.currency.set(player, CurrencyTypes.BANK, 50000)
```

## Adding Currency

**Cash**

```typescript
if (!Athena.player.currency.add(player, CurrencyTypes.CASH, 25)) {
    // Did not add the currency successfully
    return;
}

// added successfully
```

**Bank**

```typescript
if (!Athena.player.currency.add(player, CurrencyTypes.BANK, 25)) {
    // Did not add the currency successfully
    return;
}

// added successfully
```

## Removing Currency

**Cash**

```typescript
if (!Athena.player.currency.sub(player, CurrencyTypes.CASH, 25)) {
    // Did not remove the currency successfully
    return;
}

// removed successfully
```

**Bank**

```typescript
if (!Athena.player.currency.sub(player, CurrencyTypes.BANK, 25)) {
    // Did not remove the currency successfully
    return;
}

// removed successfully
```

## Remove All Currency Types

There is sometimes a situation where you wan to remove both cash on-hand and bank currency at the same time. That is what `subAllCurrencies` is for.

The function below will remove all currencies and start with `cash` first.

As a general example. Imagine the player has the following:

* 100 Cash
* 100 Bank

Together than is 200.

If the cost of an item is 150; you can use subAllCurrencies to subtract 100 from `cash` and 50 from `bank`. Leaving `50` remaining in the player's overall currency stats.

**Example**

```typescript
if (!Athena.player.currency.subAllCurrencies(player, 25)) {
    // Did not have enough to remove all.
    return;
}

// Removed cash first, and then whatever was left from bank.
```
