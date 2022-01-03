---
description: How to debug the game mode
---

# Debugging Athena

If you have implemented code but are not sure how to find an error then there's a few ways to approach it.

# Table of Contents

- [Debugging Athena](#debugging-athena)
- [Table of Contents](#table-of-contents)
  - [Debugging Code](#debugging-code)
    - [npx tsc](#npx-tsc)
    - [Open Console in-game](#open-console-in-game)
  - [Common Issues](#common-issues)
    - [Black Screen on Join](#black-screen-on-join)
  - [Can't find the Error?](#cant-find-the-error)


## Debugging Code

### npx tsc

This command you run your terminal will use the generic typescript compiler to help you find a `bug` in your code. If there's an issue it will tell you the exact file, and line number.

If it's at the end of a `bracket` then it's inside of the bracket that is causing the error.

To utilize this simply run in your terminal:

Enter the following in a terminal:

```
npx tsc
```

### Open Console in-game

Open your console in-game by press `F8` and see if anything is red. If there is red text than you may have encoutered an issue that is preventing you from fully joining / experiencing the server.

It's best to read the errors, check discord, etc. to figure out what the issue is.

Try to solve it yourself before asking around.

## Common Issues

### Black Screen on Join

This is likely due to the webserver taking on another port other than `3000`. What that means is you need to either restart your machine, or kill all `node process`, `altv-server` processes, and maybe even `restart vscode`.

If you are running `npm run dev` on a remote server and are trying to connect to it, it will not work. Development mode only works on the same machine.

## Can't find the Error?

* Does the same issue occur on a clean Athena server?
* Have you tried removing any files you've added to see if it boots?
* Have you tried removing any additional resources you added to Athena?

Otherwise, open a support ticket in the discord for help.