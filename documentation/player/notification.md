---
description: Send a GTA:V Notification to a Player
---

# playerFuncs.emit.notification

This is the way to send a simple notification built in to GTA:V to a player.


## Server Usage

Sending a notification can be done like this...

```typescript
playerFuncs.emit.notification(player, '~g~Hello There!');
```

## Colors and Formatting

These can be applied to notifications to slightly customize them.

```
~r~ = Red
~b~ = Blue
~g~ = Green
~y~ = Yellow
~p~ = Purple
~c~ = Grey
~m~ = Dark Grey
~u~ = Black
~o~ = Orange
~n~ = New line
~s~ = Reset Color
~h~ = Bold text
∑ = Rockstar Icon
÷ = Rockstar Icon
¦ = Rockstar Verified Icon

-- Untested with alt:V --
^1 = red
^2 = green
^3 = yellow
^4 = blue
^5 = CYAN
^6 = Pink
^7 = white
^8 = Dark green, red, and blue. Varies.
^9 = gray
^0= black
^c = Blandishbeige
```
