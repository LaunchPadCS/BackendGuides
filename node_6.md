## More on Express Routing

In the last section you saw how to build a simple "Hello World" express server. That's a good start, but real applications need to support multiple different `routes` to handle different types of situations. In this section we'll go over how routes work and why they're useful.

###What is Routing?
In very simple web applications, every url on a website just points to a single file. For example, `mySite.com/home.html` points to the `home.html` file, and `mySite.com/img/cat.jpg` would point to the `cat.jpg` file inside the `img` folder.

In more complex websites, a URL doesn't always point to a specific file. Instead, we use a `router` to read the url and decide what code needs to run. We define multiple different `routes`, where each route is a rule about how to handle a certain URL pattern. You might have a route that says "run this function for any url that looks like `mySite.com/users/<some_user_id>`. In other words, a route links a set of URL's to a function that handles requests made to those URL's.

### Routing in Express
Routing can be complicated if you're writing it from scratch, but express makes it easy to set up. We can just use the `app.get()` and `app.post` functions to configure GET and POST routes respectively.

For example, this code would configure 3 different routes for a webserver:
```js
//Set up our one route (myWebsite.com)
app.get('/',function(request,response) {
  response.send("Welcome to this website!");
});

//Set up another route (myWebsite.com/sayHello)
app.get('/sayHello',function(request,response) {
  response.send("Hello World!");
});

//Set up a third route (myWebsite.com/sayGoodbye)
app.get('/sayGoodbye',function(request,response) {
  //Send "Goodbye World" back to the user
  response.send("Goodbye World!");
});
```

### Routing With Parameters
Routes in express can also handle `parameters` that work a little bit like wildcards. You can define one by using a colon `:`  before the name of the parameter you want to define. When a request is made to this route, the `req.params` variable will automatically contain the value passed in.

```js
//Respond to requests sent to myWebsite.com
app.get('/', function(req,res){
        res.send("Hello World!");
});

//Respond to requests sent to myWebsite.com/test/<anything_here>
app.get('/test/:name', function(req,res){
        res.send("Hello, " + req.params.name + "!");
});
```

So in this example, if we sent a request to `myWebsite.com/test/Steve`, we would see "Hello Steve!" sent back. 
