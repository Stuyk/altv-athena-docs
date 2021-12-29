---
description: Learn where to place mods for your server.
---

# Using Mods with alt:V

You should follow the [generic mod instructions here](https://docs.altv.mp/gta/articles/tutorials/index.html). However, you will need to read further about where to place them and the load order as it's slightly different with the Athena Framework.

# Load Order

In your configuration(s) you should always be loading mods `FIRST`. Which means you should append mods before normal athena resources such as `core` and `webview`.

Ensure you edit configurations in the `configs` folder.

Example:

```
resources: ["my-building-mod", "my-car-mod", "webview","core"],
```

_It is highly recommended that if you are actively developing that you leave major MLOs off as it increases load time._

# Where to Place Mods

Mods are a bit tricky with alt:V but the alt:V Discord should always be your \#1 place to ask for modding support and ask general questions. In those regards Athena copies all files from the `./src` directory into the `./resources` directory.

**DO NOT PLACE ANYTHING IN THE `./resources` FOLDER**

Anything inside of `./resources` will always be deleted when you compile or start this game mode.

Anything inside of the `./src` folder that is not a `.ts` file will be copied over to `resources` after compilation.

This is necessary to ensure a clean build is created for each deployment.

## Example

**File Path:**

`./src/hospital`

**Resource Name**

`hospital`

# Vehicle Mods

If you are adding vehicle mods you will need to append their vehicle data to `src/core/shared/information/vehicles.ts` and add their seat count, type, class, etc.

If you do not add these your vehicle **will not** function.

Make sure you look at other example vehicles because `seat count` may not be what it seems.
