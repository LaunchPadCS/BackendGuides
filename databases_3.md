## Mongoose

Applications don't work with MongoDB using the shell we discussed in the last section. Instead, they use one of many helper libraries to work with the data. Mongoose is one popular mongoDB library for node, and we'll be explaining the basics in this section.

### Mongoose Basics
Mongoose is an npm module that makes it easy to work with mongoDB inside nodeJS. Installing it is as easy as using any other npm module; you can just run `npm install mongoose`.

When using mongoose, we define a `schema` for each collection we want to create. The schema is like a blueprint that lets mongoose know what information we want to save. You specify the type and name of each field you want to include. Then we convert the schema into a `model`, which is an object that lets us easily work with the collection.

Here's how you could define a schema for a collection that would keep track of some cats:

```js
//Load mongoose
var mongoose = require('mongoose');

//Create a cat schema for the cat collection
//In this case we'll track the age and name for each cat in the collection
var catSchema = new mongoose.Schema({
	age: Number,
	name: String,
});

//Convert our schema into a model that we can work with
var CatModel = mongoose.model('Cat', catSchema);
```

### Reading & Writing data

Once you have a model set up, you can easily read or write data. We just call `save()` on our model, and then pass in a callback function.

```js
var fluffy = new CatModel({ name: 'fluffy', age: 2 });
fluffy.save(function (err, fluffy) {
  //The 'err' var will be set if something went wrong
  if (err) {
	  console.log(err);
  } else {
      //Fluffy is now saved into the database!
  }
});
```

Reading data is also easy once you have a model. You can just call the `find()` method and pass in a callback function.

```js
CatModel.find({},function(err,cats) {
   if(err) {
       console.log(err); //Something went wrong!
   } else {
       //The 'cats' variable contains a list of all the cats
       for(var i=0; i < cats.length; i++) {
	      //Print a message for each cat in the database
	      console.log("Found a cat: " + cats[i].name)
	   }
   }
});
```

You can use the first argument to filter the results, just like you can with the mongoDB shell. If you wanted to find only cats who were 5 years old, you could add that to the first parameter:

```js
CatModel.find({age: 5},function(err,cats) {
   if(err) {
       console.log(err); //Something went wrong!
   } else {
       //The 'cats' variable contains a list of all the cats who are age 5
       for(var i=0; i < cats.length; i++) {
	      //Print a message for each cat in the database
	      console.log("Found a cat: " + cats[i].name)
	   }
   }
});
```

### Validation
One powerful feature of mongoose is `validation`. This lets us define some requirements in our schema. Then, if we try to insert invalid data, it will be rejected.

Mongoose makes it easy to set up validation. You just specify the details in the schema declaration:


```js
var mongoose = require('mongoose');
var catSchema = new mongoose.Schema({
	age: {
		type: Number,
		required: [true, "Missing Age!"],
		min: [0, "Age can’t be negative!"],
	},
});
```

For validation to work, you just include a list of requirements along with the error to throw if that requirement isn't met. For example, if we tried to save a cat without an age, we would see the "Missing Age!" error.


### Recommended Reading

* [The Official Mongoose Guide](http://mongoosejs.com/)
