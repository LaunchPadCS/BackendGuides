## Databases

Collecting, storing, and organization large amounts of data can become a challenge as applications start to get bigger. To help solve this problem, most web applications  use a Database Management System (DBMS) to organize their data. There's a lot of different database systems to choose from, all with their own advantages and disadvantages.  

###Why use a database?
The different database systems available all have different pros and cons, but they all provide some of the same general benefits. Here's the main ones:

* Ensure that data is saved even between restarts of a server
* Make sure that data is not corrupted if the server crashes in the middle of an operation
* Organize data into sections so it can be looked up easily
* Allow you to easily back up and restore data in case of emergencies
* Optimize everything to make reading or writing data as fast as possible

### What are the different types of databases?

The two main types of databases are Relational and noSQL. Both are great options, but it's important to know when to use which.

`Relational Databases`, sometimes abbreviated RDBMS, are the more traditional type of database. In a relational database, the data is organized into `tables` with rows and columns like an excel spreadsheet. Each table has a set of columns which describe the data in the table, and each row represents an object. For example, you might have a User table with a column for email, username, and password. Then for each person to register in your app, you would create a row to represent that user. Relational databases all use a language called `SQL`  to interact with the data. Although there are some minor differences, once you know SQL you can use any RDBMS easily.

`NoSQL` databases are a much newer type of database. As the name implies, they don't use SQL to read and write data. NoSQL databases don't usually organize data into tables and rows; instead, each of them organize data differently. The main idea here is that noSQL databases don't normally not force you to define specific tables and columns.

### When to use Relational or NoSQL?
Lots of people will tell you that one option is clearly better than the other. In reality, both options have some benefits and disadvantages, so it's just important to pick whichever is best for your needs.

Relational database systems are best for situations where you have clearly-defined types of data that will not change. If the objects you're going to store have relationships with other objects (for example a user might be linked to posts they have created), then a Relational database may be the way to go.

On the other hand, noSQL databases are great for when you aren't sure about what data you'll want to store. They're much easier to set up, and because they don't require SQL they tend to be easier to work with.

For this section, we're going to be covering a popular noSQL database called `MongoDB`, because it's quick to set up and easy to learn.
