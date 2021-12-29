---
description: Information about the Database and how to access it.
---

# Database

The database is MongoDB and for most SQL users out there they have absolutely zero idea that a non-query based database even exists.

Welcome to the easiest Database you will ever use in your entire life and the world of NoSQL.

## Why MongoDB?

Well, most people can't write SQL Queries and absolutely botch using them which results in things like SQL Injections. Not only that they often have to do way too much work to get a Database to even take a new value in their table.

NoSQL pretty much says hey if you want to add a new field, you can. We won't even bat an eye. Which means you can create new fields in your database without even having to touch the database or look at it.

What do I mean?

Let's take this object for example:

```ts
{   
    _id: 'jklfejklwjfkl;ejw;alfjlewafewa',
    name: 'stuyk'
}
```

I want to add a new field. I will now add it.

```ts
{
    _id: 'jklfejklwjfkl;ejw;alfjlewafewa',
    name: 'stuyk',
    username: 'stuyk1'
}
```

That's it. I've added the field and I can now save the modified `document` to the database. I didn't have to do anything special. This is why MongoDB will be the easiest Database you will ever work with.

Anyway, this section isn't about how to use it. Just showing you what you can do with a simple database entry.

## Accessing MongoDB

If you are one of those people who likes to see the data inside of your MongoDB database you will need MongoDB Compass.

Now depending on `how you installed mongodb` you may or may not need a username and password.

### Accessing it Locally

If you installed it locally and there is no user you can simply open MongoDB Compass and hit connect.

### Accessing it Externally

If you installed it externally such as on a Linux or Windows server that is not directly on your local machine you will need a `connection string` and you will also need to [SECURE AND OPEN YOUR MONGODB DATABASE](https://www.digitalocean.com/community/tutorials/how-to-secure-mongodb-on-ubuntu-20-04).

Yes you actually have to do that if you wish to access your database from outside of the server itself.

### Accessing MongoDB Atlas

If you chose to use MongoDB Atlas you can get the connection string from the Atlas website by clicking `Connect`.

![](https://i.imgur.com/wk8FaqA.png)