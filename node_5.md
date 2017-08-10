## Making an Express Webserver

Now that we've gotten most of the boring groundwork out of the way, it's time to make an actual webserver! We're going to be using the popular [Express](https://www.npmjs.com/package/express) framework to make things easier, but like everything in node, there's hundreds of other options if you're not a fan of Express.

###What is Express?
Express is one of the first big frameworks to be created for node. It's very minimalist compared to other frameworks that exist. In other words, it handles the nasty networking stuff, but it expects you to write most of the logic yourself. The advantage of express is that it's easy to set up and gives you a lot of freedom. While we *could* write a server without a framework, it would become very complicated and messy.

Like any other npm module, you can install it easily with these commands:

```bash
npm init
npm install express --save
```

There's a few important functions in express, but they follow the same basic idea. You use these functions to set up your server `routes`, and then once they're ready, express will handle the rest. For our purposes, a route is basically just a url on your server.

Here's some of the most common functions you'll use in express:

* `get(url,callback)` runs the callback function when the user makes a GET request to the specified url
* `post(url,callback)` runs the callback function when the user makes a POST request to the specified url
* `listen(port,callback)` starts our server on the specified port, and then runs the callback function once it's ready

### An Example
That might be a little hard to understand right away, so take a look a this example:

```js
//Load express module into a variable
var express = require('express');
//Use the express() function to create a server, save that in the app varaible
var app = express();

//Set up our one route
app.get('/',function(request,response) {
  //Send "Hello World" back to the user
  response.send("Hello World!");
});

//Tell express to turn on the server
var server = app.listen(8080,function() {
 console.log("Server is listening on port 8080!");
});
```

There's a lot going on here, so let's break it down. The `get()` function we called is telling express to run our callback function whenever the user visits the `/` url. The `/` represents the "root" of the website's url. So if a user visits `yourWebsite.com`, they're visiting the root. If they were to visit `yourWebsite.com/viewCats` they would be visiting `/viewCats`.

In our example, when a user visits the `/` url we want express to run the function we provided. Express will automatically set the `request` and `response` parameters in this function, so we can use those if we need to. In this example we use `response.send()` to send data back to the user.

>Note that you can only call response.send() once. After it's been sent, the connection is closed and no more information can be passed. If you call it a second time in the same handler function, an error will be thrown.

Finally, we use `listen()` to express we're ready to start up the server. This function takes a port number as it's argument. If you're not familiar with ports, the basic idea is that they're like lanes on the internet highway to your computer. Only one program can use each port at a time. We ask it to run on port 8080 in this example, but you can use any port that isn't already being used on your laptop.

Finally, we pass a callback function to our `listen()` method. Once express has started up the server, it will run this callback. In our example we just print a message to the console.

### Running an Express App
Now that everything is set up, you could run your express server with `node myServer.js`. Don't forget to install express with `npm install` if you didn't earlier. If you visit [http://localhost:8080](http://localhost:8080) in your browser while the server is running, you'll see the "Hello World" message printed.

 The server will keep running until you stop it, so you  can kill the program with `ctrl+c` inside the terminal.
