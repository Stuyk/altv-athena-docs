---
description: Learn to Create Plugins
---

# Learn to Create Plugins

**HEY LISTEN!**

**THIS DOCUMENT TARGETS PLUGINS FOR 3.0.8+**

**THIS DOCUMENT TARGETS PLUGINS FOR 3.0.8+**

**THIS DOCUMENT TARGETS PLUGINS FOR 3.0.8+**

**HEY LISTEN!**

Plugins in the Athena Framework are made in a specific way. Meaning, that following this general structure will help you create robust plugins without touching the core of the framework.

It is important that when a plugin is created that is does not adjust the core of the Athena Framework. This ensures that compatability is future-proof and additional updates to the plugin can be made without over complicating it.

### Structure

All plugins should be placed inside the `src/core/plugins` folder.

The folder structure is very specific.

It consists of several folders inside your main folder.

* server
  * This should all be server-side code
* client
  * This should all be client-side code
* shared
  * This should be shared between server, client, and webview
* webview
  * This is a WebView Page you want to inject

```
src/core/plugins/core-example
  ├───client
  │       index.ts
  │
  ├───server
  │   │   index.ts
  │   │
  │   └───src
  │           file1.ts
  │           file2.ts
  │           file3.ts
  │
  ├───shared
  │   │   file1.ts
  │   │   file2.ts
  │   │   file3.ts
  │
  └───webview
      │   Example.vue
      │   tsconfig.json
      │
      ├───components
      │       Component1.vue
      │       Component2.vue
      │       Component3.vue
```

### Naming

Rules for Files and Folder(s)
- Plugins should use `kebab-case` for folder names.
  - ie. `door-plugin`
- File names should be `camelCase`.
  - ie. `mainDoorController.ts`
- Plugins should use their respective folders for imports
  - Server: `src/core/plugins/example-plugin/server`
  - Client: `src/core/plugins/example-plugin/client`
  - Shared: `src/core/plugins/example-plugin/shared`
  - WebView: `src/core/plugins/example-plugin/webview`
- Entry file for a Plugin should be `index.ts`
  - This applies to both `client` and `server`.

It is up to you as the plugin creator to provide `GOOD` instruction(s) on installation and removal of the plugin.

## Registering a Server Plugin

In your plugin's `index` file you should register your plugin.

```typescript
import * as alt from 'alt-server';
import { PluginSystem } from '../../server/systems/plugins';

const PLUGIN_NAME = 'Example Plugin';

PluginSystem.registerPlugin(PLUGIN_NAME, () => {
    // Initialize other things for your plugin here...
    alt.log(`~lg~${PLUGIN_NAME} was Loaded`);
});
```


## Register a Plugin WebView

Inside of `src/core/plugins/athena/webview/imports.ts` 


## Importing Plugins

You can import plugins for `client` and `server` by navigating to their respective `imports.ts` files.

### Client

```
src/core/plugins/athena/client/imports.ts
```

Each of these files should have import references to other `index` files for other plugins. Simply add the `index` file for your plugin and it will be imported.

#### Example

```ts
import '../../example-plugin/client/index';
```

### Server

```
src/core/plugins/athena/server/imports.ts
```

Each of these files should have import references to other `index` files for other plugins. Simply add the `index` file for your plugin and it will be imported.

#### Example

```ts
import '../../example-plugin/server/index';
```

### WebView

```
src/core/plugins/athena/webview/imports.ts
```

Inside of the imports for webview you'll need to import the `vue` file. The `vue` file should then have a `shallowRef` of its import added to the object.

#### Example

```ts
import Example from '../../example-plugin/webview/Example.vue';

export const PLUGIN_IMPORTS = {
    Example: shallowRef(Example),
};
```

_If there are errors on import, do not worry it will still compile._


## Register a Shared Plugin

Plugins that use the shared folder can be used on both client-side and server-side. However, the content inside of these files has to be accessible on both client and server.

This means that you cannot use `alt.Player`, `alt.Vehicle`, etc. They're mostly good for creating event names, enums, etc. that will be used on both server-side and client-side.

## Learn from Example

Last but not least you should always look at the existing plugins to get a general idea of how they work and how they're being implemented.