## Programming in Node

Because node is just JavaScript, it's pretty easy to pick up. If you're not already familiar with it, we'll quickly go over the basics here.

### Hello World
The first thing you'll need to do is install node. You can grab it from their website [here](https://nodejs.org/en/).

For the most part, a node program works pretty much like any normal JavaScript program. If you're brand new to JavaScript you might want to take a look a this [this](https://launchpadcs.gitbooks.io/webdev-guides/content/js_01.html) page where we cover some of the basics.

Because node is a command line tool, any output will be directed into the terminal instead of the browser's debugging tools. Here's a sample program that would print some output into the terminal:

```js
//Say Hello
console.log("Hello World!");

//Define a function so we can say hello easily
function sayHello(name) {
	console.log("Hi, " + name);
}

//Say hi to some people
sayHello("Kayla");
sayHello("Sam");

var myName = "Bob";
sayHello(myName);
```
To run a node program, just use the `node` command from the terminal once you've installed it. For example, you could run a program by typing `node myFile.js`.

Just like JavaScript in the browser, node programs don't have an entry point or main method. Instead, execution just starts at the top of the file you specify in your terminal.


### JavaScript Modules
In 2015, the `ES6` standard of JavaScript was released. This specification allows you to use an `import` statement to load objects from one file into another, sort of like how importing works in Java or C. This is *not* supported in Node, since it was created before this standard existed.

Luckily, node has it's own custom module system that works in a similar way. Developers can `export` a value from one file and then import it into another with the `require()` function.

Let's say you have two files: `main.js` and `passwords.js`. You have some password variables in `passwords.js` that you want to use inside `main.js`. First, you set the `module.exports` variable inside `passwords.js` to whatever you want to share:

```js
//Inside the passwords.js file
var myPassword = "Password123";
module.exports = myPassword; //Let node know you want to share this variable with other files
```
Now, any other file can load the contents of the `module.exports` variable using the `require()` function. Here's an example:

```js
//Inside the main.js file
var secretPassword = require('passwords.js'); //Load the variable we exported
console.log("The password is: " + secretPassword);
```

This concept might be a little confusing at first, but it'll make more sense once you've used it. For now, just know that `require()` is how you can load in content from other files.

### A simple Server
You now know enough to make a very simple server in node! Here's an example of what that might look like:

```js
//Load the http module that comes with node
var http = require('http');

//Tell the server what to do when it gets a request
var server = http.createServer(function(request, response) {
	//Send "Hey There" to the browser
	response.write("Hey there");
	//Let the browser know we're done talking to it
	response.end();
});

//Turn on the server using port 8080
server.listen(8080);
```

If you were to run this code and visit `http://localhost:8080` in your browser, you would see "Hey there" printed on the screen.  The syntax used here is a little complicated, but we'll get to the specifics later. The main point is that using just 6 lines of code, you can create a server that does a lot of work for you automatically.


###Recommend Reading
[Anatomy of a node HTTP Transaction](https://nodejs.org/en/docs/guides/anatomy-of-an-http-transaction/)
