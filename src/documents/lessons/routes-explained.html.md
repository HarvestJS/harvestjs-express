---
title: Express Routes Explained
layout: lesson
pageOrder: 50
---

In the last lesson, I had you open `routes/index.js` and make changes there to affect the rendered output. But how did I know that was the file to change? In order to understand that, you'll need to understand HTTP requests, so let's touch on that briefly.

Express uses HTTP verbs for routes and supports `GET`, `POST`, `PUT` and `DELETE` out of the box for reading, creating, updating and removing assets. These routes are defined using `app.get`, `app.post`, `app.put` and `app.delete`.

`GET` and `POST` requests should be familiar to you if you've worked with form data on webpages in the past. The other two are also important for modifying information on the server via RESTful calls, as you'll learn later. By default, requests are `GET`.

<hr>

With that brief introduction out of the way, open `app.js` in your editor and check out the following code, which should be at or near line 32:

`app.get('/', routes.index);`

This is defining a `GET` route for /, the base of the application, which is the page you get when you load [http://localhost:3000](http://localhost:3000).

What about the `routes.index` part? That's coming from the included routes, which happens on or near line 7:

`routes = require('./routes')`.

Node's `require` command, when given a directory, will try to load `index.js` by default, which is what is happening here, and why it's loading `index.js` without us needing to explicitly tell it to.

<hr>

What about the next line, `app.get('/users', user.list);`? This is defining another route, `/users`, which you can access at [http://localhost:3000/users](http://localhost:3000/users).

Using what you just read above, can you figure out where the code for that route lives?

Hopefully you answered `routes/user.js`. Open that file and notice that this response is a little bit different, using `req.send` instead of `res.render`. If you loaded the above URL in your browser, you'll notice is doesn't have any HTML, it's just plain text. We'll touch more on that in the following lessons.

That's express routes in a nutshell. In the next lesson, we'll create our own route and use it to request some information from the server.