---
description: Administrative stuff for Athena Framework
---

# Administrative Modes

Athena Framework does have some generic administrative modes but they're mostly restricted to the console at the moment. However, you can give certain accounts access to commands through the permission system.

## How to be an Admin?

If you want to give yourself admin permissions. You need to get your discord id out of discord.

![](https://i.imgur.com/6PgYFQE.png)

Then right-click on yourself in any server, channel, etc. and get your identifier.

![](https://i.imgur.com/VKWfEXb.png)

Start your server and make sure you already have an account and have logged into that account.

In your console type `/setadmin your_discord_id_here 4`

![](https://i.imgur.com/EtNxYqz.png)

## How do Permissions Work?

Let's talk about how permissions work and why you really need to understand this concept when you're writing commands. Permissions use a bitwise function to determine who can access what commands.

This means that only certain accounts should be able to access certain commands depending on the permissions you pass to a command.

### Unrestricted Command

```typescript
function doSomething(player: alt.Player) {
    console.log('Someone did something');
}

ChatController.addCommand('dosomething', '/dosomething - It does something?', PERMISSIONS.NONE, doSomething);
```

### Moderators Only Command

```typescript
function doSomething(player: alt.Player) {
    console.log('Moderator did something');
}

ChatController.addCommand('dosomething', '/dosomething - It does something?', PERMISSIONS.MODERATOR, doSomething);
```

### Admins Only Command

```typescript
function doSomething(player: alt.Player) {
    console.log('Admin did something');
}

ChatController.addCommand('dosomething', '/dosomething - It does something?', PERMISSIONS.ADMIN, doSomething);
```

### Admins and Moderators

```typescript
function doSomething(player: alt.Player) {
    console.log('Admin or Mod did something');
}

ChatController.addCommand('dosomething', '/dosomething - It does something?', PERMISSIONS.ADMIN | PERMISSIONS.MODERATOR, doSomething);
```

## How to Set Permission Level

Permissions by default are currently set to the following:

```typescript
export enum PERMISSIONS {
    NONE = 0,
    VIP = 1,
    MODERATOR = 2,
    ADMIN = 4
}
```

(This config can be found in `/core/shared/flags/permissionFlags.ts`)

To give someone access to all admin commands you can write into your `server terminal` the following command:

`/setadmin <discord_id> <permission_level>`

This requires the player to be online and in-game.

_The discord\_id is their actual identifier from Discord Developer mode_

## Adding Additional Permission Levels

Permissions are bitwise meaning that they `MUST` be a certain number in order for them to work. This means that if you do not use the right number it could `ruin` your server because you didn't read this right.

This is why I'm giving you an example to follow. Please ensure you follow this pattern.

```typescript
export enum PERMISSIONS {
    NONE = 0,
    VIP = 1,
    MODERATOR = 2, // 1 + 1 = this
    ADMIN_LEVEL_1 = 4, // 2 + 2 = this
    ADMIN_LEVEL_2 = 8, // 4 + 4 = this
    ADMIN_LEVEL_3 = 16, // 8 + 8 = this
    ADMIN_LEVEL_4 = 32, // 16 + 16 = this
    ADMIN_LEVEL_5 = 64, // 32 + 32 = this
    GOD_LEVEL_1 = 128, // 64 + 64 = this
    GOD_LEVEL_2 = 256, // 128 + 128 = this
    GOD_LEVEL_3 = 512, // 256 + 256 = this
    SWEAT_LORD = 1024 // 512 + 512 = this
    // What do you think goes here?
}
```

_Notice how each value increases by itself each time_

The answer to the above question is `2048`. Thanks for reading.
