---
description: Player identification system explained
---

# Identification System

Players have various ways to be identified but it is up to you as the server owner to decide how you want your player's identified.

The current strategy is based on a `temporary alt:v id` or `server_id` for short.

This means that a player joins, gets asigned an incremental id (1, 2, 3, 4...) and after they leave that number is freed up for any other player to take that same identifying number.

`server_id` -> A temporary player identifier assigned by the alt:V system.
`character_id` -> A persistent incremental character identifier in the database. Unique to the character.
`account_id` -> A persistent incremental account identifier in the database. Unique to an account who may own multiple characters.

![](https://i.imgur.com/MgEnthy.png)

## Obtaining the identifier

When working with the ID system you can get any player by the ID that they see by using the following API.

```typescript
const id = 5;
const player = Athena.systems.identifier.getPlayer(id);
```

This should always be used when a player is feeding you a command with an id.

