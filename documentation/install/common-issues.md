---
description: Most Common Installation Issues
---

# Most Common Installation Issues

Not everything will be listed here; but here are some of the most common installation issues when installing Athena.

- [Most Common Installation Issues](#most-common-installation-issues)
  - [Bad Database Connection](#bad-database-connection)
  - [./altv-server: Permission denied](#altv-server-permission-denied)
  - [Failed to connect to HTTP Server](#failed-to-connect-to-http-server)

## Bad Database Connection

```
Uncaught exception: Error: connect ECONNREFUSED 0.0.0.0:27017
```

This means that the MongoDB service is not currently running and your server does not have a connection that can reach the Database. This can be resolved by starting the MongoDB service.

* [Linux MongoDB Instructions](./linux.md#MongoDB)

* [Windows MongoDB Instructions](./windows.md#ensure-mongodb-running-as-a-service)

If all else fails, configure `AthenaConfig.json` with a connection string from MongoDB Atlas (Google It).

## ./altv-server: Permission denied

This means that your linux terminal does not have execution rights to run the `altv-server` binary. This can be resolved by running a `chmod` command against the server binary.

**Run in Linux Terminal**

```
chmod +x ./altv-server
```

## Failed to connect to HTTP Server

This can be any number of things.

If you are trying to connect locally instead of doing `127.0.0.1:7788` for the direct connection, do `0.0.0.0:7788`.

If you are trying to connect externally then you did not port forward.
