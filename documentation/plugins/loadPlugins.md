---
description: Learn to Load Plugins
---

# Learn to Load Plugins

Inside of the main `AthenaConfig.json` there is a section for loading plugins.

It currently works in two ways.

* []
  * An empty array for plugins means it will **LOAD ALL PLUGINS**
* ['core-character-creator', 'folder1', 'folder2', 'folder3']
  * An array with exact folder names as strings.
  * This will load **ONLY** the plugins specified. 

All plugins should be placed inside the `src/core/plugins` folder.

### Structure

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
  │   │   index.ts
  |   │
  │   └───src  
  │       │   file1.ts
  │       │   file2.ts
  │       │   file3.ts
  |
  ├───server
  │   │   index.ts
  │   │
  │   └───src
  │       │   file1.ts
  │       │   file2.ts
  │       │   file3.ts
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