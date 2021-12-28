---
description: >-
    Learn how to add custom sounds.
---

# Sounds

It is highly recommended that you keep your sounds compressed and keep the quality below `128`. We use the open source format known as `.ogg` for this game mode so it's recommended that you download [Audacity](https://www.audacityteam.org/download/) if you plan on doing a lot of audio editing.

Folder Placement

```
src-webviews/public/assets/sounds/yourFile.ogg
```

## Editing Sounds with Audacity

If you have never used Audacity before. It's actually quite simple to use.

Simply highlight the areas with your cursor that you want to remove and press `del` to remove the sections.

![](https://i.imgur.com/QGPE4Cb.png)

Then you are ready to export. Go to file `file -> export-> ogg`

![](https://i.imgur.com/WV6CQRC.png)

I usually change the quality to about `5` when I export. The quality won't matter that much for most of these small sounds.

# Playing Sounds

Sounds can be played in a 2D environment or a 3D environment. Depends on what you want to emit to a player.

Sounds should not last forever, and they should be used temporarily.

## 2D Environment

Simply use the playerFuncs to call the name of your file. Remove `.ogg` from the audioName.

```ts
// Last parameter is volume. 0 - 1
playerFuncs.emit.sound2D(player, 'unlock', 0.75);
```

## 3D Environment

Simply use the playerFuncs to call the name of your file. Remove `.ogg` from the audioName.

You must pass either a player, or vehicle as the target location of the audio.

```ts
// Last parameter is volume. 0 - 1
playerFuncs.emit.sound2D(player, 'unlock', player.vehicle);
```