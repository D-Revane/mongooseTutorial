# **Mongoose ODM**  

Mongoose is a "schema" based node.js library for mongoDB. It includes built-in type casting,validation, query building, and much more without the daunting task of programming it all from scratch.  


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

Inside of your models directory create your schema file  

    $ touch schema.js  

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

