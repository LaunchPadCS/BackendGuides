## MongoDB Basics

MongoDB is one of the most popular noSQL databases available right now. It's a great choice for getting started with databases, and it's relatively easy to set up. We'll go over the basics first, and then explain how to use mongoDB from inside a node program.

### Setting up MongoDB
You don't need to install mongoDB to learn these basics, but if you want to you can download the free community edition of MongoDB from [here](https://www.mongodb.com/download-center).  From there, you can follow the setup instructions [here](https://docs.mongodb.com/manual/administration/install-community/). If you're following the windows guide, you can skip the section about configuring a windows service.


###Structuring MongoDB data
MongoDB data is organized into `collections` and `documents`.  A collection is just a group of documents bunched together. Usually a collection will represent a specific type of object in your system (for example you might have a collection for users or posts). Documents hold the actual data for the objects.

Here's what a document for a blog post might look like. It contains information about the post, as well as a special `_id` value to identify it.


```json
{
   _id: ObjectId(123456789)
   title: 'My Post about MongoDB',
   content: 'MongoDB is a type of database',
   likes: 25,
   shares: 50
}
```

You can also `embed` documents in each other. If we wanted our blog post document to contain a list of comments, it might look like this:

```json
{
   _id: ObjectId(123456789)
   title: 'My Post about MongoDB',
   content: 'MongoDB is a type of database',
   likes: 25,
   shares: 50,
   posts: [
	 {
	   comment: "Wow MongoDB is pretty neat!",
	   poster: "Sarah"
	 },
	 {
	   comment: "I think mySQL is cooler",
	   poster: "Bob"
	 }
   ]
}
```


### The MongoDB Shell
Most of the time you won't need to use the mongoDB shell to interact with your data. Instead, your program will use some helper library to work directly with the data. However, using the mongoDB shell can be useful for debugging. The shell is a program you can run in the command line which lets you work with mongoDB data.

If you had a collection of posts and wanted to read it's data, you would run a command like this from the mongo shell:

```bash
db.MyPostsCollection.find()
```

If you want to find a specific entry in the database, you can add filters as a paramater in the `find()` call.  If you wanted to find all the posts that had 50 likes and 50 shares, you could run a command like this:

```bash
db.MyPostsCollection.find({ likes: 50, shares: 50 })
```

And finally, if you wanted to insert data, you use the `insert` command:

```bash
db.MyPostsCollection.insert({
  title: 'My Test Post',
   content: 'This post is a test!',
   likes: 0,
   shares: 0,
})
```
