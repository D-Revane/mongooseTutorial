# **Mongoose ODM**  

Mongoose is a "schema" based node.js library for mongoDB. It includes built-in type casting,validation, query building, and much more without the daunting task of programming it all from scratch.  

This tutorial assumes that you already have a basic understanding of node.js, mongoDB, and how to build your application using them  


First, create a directory for your application and navigate to it  

	$ mkdir <application_directory>  
	$ cd <application_directory>  

Since this is a node.js application we must first run "npm init" to establish a package.json file  

	$ npm init  

Now install the mongoose ODM, as well as any other dependacies that your application may require. For the sake of this tutorial I will only go over the mongoose part of the application.  

	$ npm install mongoose  

## **Schemas**  

All of Mongooses functionality is built around customizable data structures called "schemas". Your schemas will dictate the way data is stored and referenced within your database.  

Create a "models" directory inside your application to store your schema files  

    $ mkdir models  

Inside of your models directory create your schema file. You can name this file whatever suites you best  

    $ touch <schema_file>.js  

Since we are using mongoose, we must assign each of our files that require mongoose funtionality a const value that referres to the mongoose library  

  ```javascript  
  const mongoose = require('mongoose');  
  ```  
  
Here is an example of a complete schema.js file  

![alt text](http://198.27.107.201/web-108/assignments/mongooseTutorial/images/schema.png "Schema File")  

Notice at the end of the file we export the schema model to access it from other files  

  ```javascript  
  module.exports = mongoose.model('todos', Todo)  
  ```  

## **Server/Index file**  

Create your server/index file in the root directory of your application. This file is usually named either server.js or index.js based on prefference  

    $ touch server.js  

Remember to assign the mongoose const value.  

Now we will establish our applications connection to our mongoDB database using mongoose connect  

  ```javascript  
   mongoose.connect('mongodb://localhost/Todo', {useNewUrlParser: true})  
  .catch(e => {  
  console.error("connection issue" , e.message)  
  })  
  ```  
Here is an example of the server.js file  

![alt text](http://198.27.107.201/web-108/assignments/mongooseTutorial/images/server.png "Server File")  


## **Routes**  

Create a routes directory within your application  

    $ mkdir routes  

In this directory create a file to direct the routes within your application. Again, you may name the file whatever suites you best  

    $ touch <routes_file>.js  

In this file is where we will direct our information requests. 
The requests shown in this example are  

- app.get()  // reads information from database  
- app.post()  // adds new entry to the database  
- app.put()  // updates existing entry in database  
- app.delete()  // deletes an entry from the database  

Here is an example of a routes file  

![alt text](http://198.27.107.201/web-108/assignments/mongooseTutorial/images/routes.png "Routes File")  

Notice that we have created a const value that referres to a controllers file   

  ```javascript  
  const todoCtrl = require('../controllers/todo-ctrl')  
  ```  

## **Controllers**  

Your controllers file will contain all of the functions that execute the information requests from the routes page  


Create a controllers directory within your application  

    $ mkdir controllers  

In this directory create your controller file

    $ touch <controller_file>.js  

Here is an example of a controller file. To fit the screenshot this file only includes one of the required functions  

![alt text](http://198.27.107.201/web-108/assignments/mongooseTutorial/images/controller.png "Controller File")  

Notice that the first line in the file creates a const value that referres to the schema model file created before  

  ```javascript  
  const Todo = require('../models/todo-model')  
  ```  


That is the basics of a CRUD application using the Mongoose ODM  

Please refer to the Mongoose documentation for a better understanding of how to work with mongoose, as this tutorial is just part of a school project and I just figuring this out myself