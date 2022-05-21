---
description: Learn where to place mods for your server.
---

# Adding Mods

## Using Mods with alt:V

alt:V has [general modding instructions on how to stream files, mlos, ymaps, etc](https://docs.altv.mp/gta/articles/tutorials/index.html).

After following those general instructions read further below on where to put your mods.

## Where to Load Mods?

```
📁 altv-athena/
    L 📁 resources/
        L 📁 mods/
            |- 📁 a-mod/
            |    |- stream.cfg
            |    |- resource.cfg
            |    L 📁 stream/
            |- 📁 some-mod/
            |    |- stream.cfg
            |    |- resource.cfg
            |    L 📁 stream/
            L 📁 whatever-mod/
                |- stream.cfg
                |- resource.cfg
                L 📁 stream/
```

## Add to server.cfg

**! WAIT DO NOT EDIT `server.cfg` !**

Navigate to one of the following files:

*  `config/prod.json`
*  `config/devtest.json`
*  `config/dev.json`

Add the name of your resource and the folder path to the `resources` section.

Example:

* `mods/teslacar`
* `mods/hospital`
* `mods/fastcar`

## Load Order

In your configuration(s) you should always be loading mods `FIRST`. Which means you should append mods before normal athena resources such as `core` and `webview`.

Ensure you edit configurations in the `configs` folder.

Example:

```ts
resources: ["mods/a-mod", "mods/some-mod", "mods/whatever-mod", "webviews", "core"],
```

_It is highly recommended that if you are actively developing that you leave major MLOs off as it increases load time._

## Where to Place Mods

Mods are a bit tricky with alt:V but the alt:V Discord should always be your \#1 place to ask for modding support and ask general questions.

**ALL MODS SHOULD BE PLACED INSIDE `./resources/mods`. ANYTHING OUTSIDE THIS FOLDER GETS DELETED**

This is necessary to ensure a clean build is created for each deployment.

### Example

**Folder Path**

`./resources/mods/hospital`

**Resource Name**

`mods/hospital`

## Vehicle Mods

If you are adding vehicle mods you will need to append their vehicle data to `src/core/shared/information/vehicles.ts` and add their seat count, type, class, etc.

If you do not add these your vehicle **will not** function.

Make sure you look at other example vehicles because `seat count` may not be what it seems.
