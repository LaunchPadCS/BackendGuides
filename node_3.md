## Node Callbacks & Async Operations

Because of the way Node works, there's a few quirks you'll need to get used to before moving any further. The main thing that can throw people off is callbacks and async operations. We'll explain how both of those work and how you can take advantage of them in your node programs.  

### Threading Basics
The first concept that's important to understand is what a `Thread` is. Basically, a CPU can only process one instruction at a time, line by line, in order. To speed things up, modern computers have multi-core CPU's that are able to process multiple "threads" of instructions at the same time. Many programming languages allow you to take advantage of this and run certain parts of code on additional processors.

 You don't need to worry about the specifics of threading for node, but if you're curious, here's the basic idea: Internally, Node executes all your code inside a single main thread, but all I/O operations are ultimately passed onto parallel worker threads. If that doesn't make any sense to you, don't worry about it. If you're interested in learning more about how JavaScript handles threads in general, [this](https://www.youtube.com/watch?v=8aGhZQkoFbQ) talk from Philip Roberts is an amazing explanation.

### Synchronous vs Asynchronous
If you're programmed before, you're probably use to `Synchronous` execution. Synchronous code executes in order, line by line, until the program ends. If one function takes a long time to execute, the program will wait until that function finishes before moving on. For example, you may have something like this:

```js
console.log("Hello World");
superSlowFunction(); //This function takes 10 seconds to finish
console.log("All Done!"); //This message prints 10 seconds later
```

On the other hand, you can have `Asynchronous` code. With an `Asynchronous` function, the program will move on before the function has finished. Instead, the function will finish in the background while the main program keeps going. Here's an example:

```js
console.log("Hello World");
slowAsyncFunction(); //This function takes 10 seconds to finish
console.log("All Done!"); //This message prints immediately
//...Waiting 10 seconds....
//After 10 seconds the async function finishes
```
 This type of code is great for when we have slow operations that need to run in the background, but we don't want to pause the whole program while they run. It would be pretty bad if your entire server stopped working for a few seconds because one user was doing something slow.  

### Callback Basics
The trick with Asynchronous programming is that most of the time need to say "run this in the background *and then do this other thing once that finishes*". In node, we use `callbacks` to handle this. Basically, a callback is a function that gets run after some async operation is finished.  

Let's take a look at an example. The `setTimeout()` function takes a callback as it's first argument and a time (in milliseconds) as it's second argument. After that number of milliseconds has passed, it will run the callback. This program will print "Hello World" first, then wait 1000 milliseconds, and *then* print "Hey I'm running".

```js
myCallback = function() {
	console.log("Hey Im running!");
}
setTimeout(myCallback,1000);
console.log("Hello World!");
```

 Basically, we're assigning a function to the `myCallback` variable and then passing that into the `setTimeout()` function. This method works, but it's a little sloppy and not the way code is usually written. Instead, we can skip the variable assignment and declare the function right inside the spot we need it. This code would do the exact same thing:

```js
setTimeout(function() {
	console.log("Hey Im running!");
},1000);
console.log("Hello World!");
```

This syntax may be a little more confusing, but it's a lot cleaner and easier to read once you get used to it. The same thing is happening though: We pass in a function into `setTimeout()`, and that function gets run automatically after 1000 milliseconds have passed. The important thing is that our code can move past the slow operation and keep going.

###Recommend Reading
[What the heck is the event loop anyways?](https://www.youtube.com/watch?v=8aGhZQkoFbQ)
