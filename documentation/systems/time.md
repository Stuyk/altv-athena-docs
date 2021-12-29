---
description: Learn how time works in Athena
---

# Time

Time in the Athena Framework has two different options.

* Server Time
* Minutes Per Minute

## Server Time (Default)

Server time is the default setting that uses the local timezone of the server to set the time in the server. Which means that an in real life day is an in-game day.

This can be enabled / disabled in the main athena configuration under `USE_SERVER_TIME`.

## Minutes Per Minute

This type of time lets you apply how many minutes should the world time should increase per minute. Example being that if a minute has passed you can specify for in-game minutes to increase by 5.

This can be enabled by turning off `USER_SERVER_TIME` and setting `MINUTES_PER_MINUTE` to the amount of minutes... per minute.

### Why was this added?

When you have an international audience for your server it's best to give both day, and night to all timezones. Minutes Per Minute allows this to happen.