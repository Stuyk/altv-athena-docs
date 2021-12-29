---
description: Learn to Create Plugins
---

# Learn to Create Plugins

Plugins in the Athena Framework are made in a specific way. Meaning, that following this general structure will help you create robust plugins without touching the core of the framework.

It is important that when a plugin is created that is does not adjust the core of the Athena Framework. This ensures that compatability is future-proof and additional updates to the plugin can be made without over complicating it.

## Structure

All plugins should be placed inside the `core` resource.

Rules for Files and Folder(s)

- Plugins should use `kebab-case` for folder names.
  - ie. `door-plugin`
- File names should be `camelCase`.
  - ie. `mainDoorController.ts`
- Plugins should use their respective folders for imports
  - Server: `src/core/plugins`
  - Client: `src/core/client-plugins`
  - Shared: `src/core/shared-plugins`
  - WebView: `src-webviews/src/pages`
- Entry file for a Plugin should be `index.ts`
  - This only applies to server-side.
  - This should also be in the `src` folder of your plugin.

It is up to you as the plugin creator to provide `GOOD` instruction(s) on installation and removal of the plugin.

## Example Plugin Structure

Here is an example of the `atm` folder structure and files.

```
src/core/
|
├───client-plugins/
│   └───core-atm/
|       └─── view.ts
├───plugins/
│   └───core-atm/
│       ├───src/
|       |   └─── view.ts
|       └─── index.ts
└───shared-plugins/
    └───core-atm/
        ├─── events.ts
        └─── locales.ts
```

## Register a Plugin Server-Side

Inside of `src/core/plugins/imports.ts` is where you should import the `index` file for your plugin.

In your `index` file you should register your plugin.

```ts
import * as alt from 'alt-server';
import { PluginSystem } from '../../server/systems/plugins';

const PLUGIN_NAME = 'Example Plugin';

PluginSystem.registerPlugin(PLUGIN_NAME, () => {
    // Initialize other things for your plugin here...
    alt.log(`~lg~${PLUGIN_NAME} was Loaded`);
});
```

## Register a Plugin Client-Side

Inside of `src/core/client-plugins/imports.ts` you simply need to add your `index` file for client-side. Make sure not to mix server-side and client-side.

## Register a Shared Plugin

Plugins that use the shared folder can be used on both client-side and server-side. However, the content inside of these files has to be accessible on both client and server.

This means that you cannot use `alt.Player`, `alt.Vehicle`, etc. They're mostly good for creating event names, enums, etc. that will be used on both server-side and client-side.

## Learn from Example

Last but not least you should always look at the existing plugins to get a general idea of how they work and how they're being implemented.