---
description: Learn how to load clothing mods.
---

# Clothing Mods

Clothing mods are probably the most annoying modding resouce to add to a server purely because of the complexity.

It is suggested to follow the following [the official clothing tutorial for setting up a clothing dlc pack](https://docs.altv.mp/gta/articles/tutorials/stream_clothes.html).


## Where to Load Clothes?

Below is an example of a single clothing mod with exactly 1 for the `mask` slot.

Every DLC Pack for clothing may be different but there are some general common functionalities.

All mods should be placed under `resources/mods`.

```
📁 altv-athena/
    L 📁 resources/
        L 📁 mods/
            |- 📁 clothing-mod-a/
            |    |- stream.cfg
            |    |- resource.cfg
            |    L 📁 stream/
            |        |- mp_f_freemode_01_mp_f_dlcpackname.meta
            |        |- mp_m_freemode_01_mp_m_dlcpackname.meta
            |        |
            |        |- 📁 ped_female.rpf/
            |        |   |- mp_f_freemode_01_mp_f_dlcpackname.ymt
            |        |   L 📁 mp_f_freemode_01_mp_f_dlcpackname/
            |        |       |- some_model_000_u.ydd
            |        |       L some_model_diff_000_a_uni.ytd
            |        |
            |        L 📁 ped_male.rpf/
            |            |- mp_m_freemode_01_mp_m_dlcpackname.ymt
            |            L 📁 mp_m_freemode_01_mp_m_dlcpackname/
            |                |- some_model_000_u.ydd
            |                L some_model_diff_000_a_un
            |
            L 📁 clothing-mod-c/
```

## Adding to Configs

After adding the modification to your `resources/mods` folder you need to add it to your configs.

Under the `configs` folder in the root directory of Athena you will have various `.json` files.

It is suggested to load all resource packs at the beginning of the `resources` array.

**VERY IMPORTANT NOTE**

The order of the resources does matter. Do not alphabetize. Do not change the order.

You should absolutely load clothing resources as they are added to your game mode.

ORDER MATTERS.

## Example Config

This is what you would add under `configs/dev.json` file to load a clothing resource.

The name should match the folder name in `resources/mods`.

```javascript
"resources": [
    "mods/clothing-mod-c",
    "mods/clothing-mod-a",
    "mods/clothing-mod-w",
    "webviews",
    "core"
],
```

## Configuring Clothing Counts

You should be aware of the clothing count you are adding for both male, and female. You are 100% responsible to know this information and it should be obtainable from the Clothing Tool provided in the tutorial at the beginning of this page.

Example of Clothing Counts

![](https://i.imgur.com/WJI178b.png)

As you can see in the above image we need to add the following:

```
1 -> Female Top / Shirt
1 -> Male Undershirt
```

Inside of Athena navigate to:

```
src/core/plugins/core-clothing/shared/config.ts
```

Look for a section called `DLC_CLOTHING`.

This section has a very specific format so pay attention.

We're going to add the clothing count based on the example above. `1 Female Top` and `1 Male Undershirt`.

```typescript
    DLC_CLOTHING: {
        [CLOTHING_IDS.MASKS]: [],
        [CLOTHING_IDS.TORSOS]: [],
        [CLOTHING_IDS.LEGS]: [],
        [CLOTHING_IDS.BAGS]: [],
        [CLOTHING_IDS.SHOES]: [],
        [CLOTHING_IDS.ACCESSORIES]: [],
        [CLOTHING_IDS.UNDERSHIRTS]: [
            // MOD NAME: 'clothing-mod-a' 
            {
                dlcName: 'dlcpackname',
                count: {
                    [ORIENTATION.FEMALE]: 0,
                    [ORIENTATION.MALE]: 1,
                },
            },
        ],
        [CLOTHING_IDS.BODY_ARMOUR]: [],
        [CLOTHING_IDS.TOP]: [
            // MOD NAME: 'clothing-mod-a' 
            {
                dlcName: 'dlcpackname',
                count: {
                    [ORIENTATION.FEMALE]: 1,
                    [ORIENTATION.MALE]: 0,
                },
            },
        ],
    }
```

## Finish

You are all done adding the clothing mod.

Visit a clothing store in-game to see if it worked.

Keep in mind that if you remove this mod in the future you will have to remove the clothing item from **all players**.

Which there is not an automated method to do this.

