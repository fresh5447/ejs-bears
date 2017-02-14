#### EJS Bears

__learning Node, Mongo, Mongoose, Express, and EJS__

### Description
We are going to build an application which uses EJS to render different pages. The pages will be displaying 'bears'.
For example:

UI Routes:
/ => Home route, renders index.ejs
/view => This will render and EJS page that displays all bears.ddsfasdfsadfdfdf
/post => This will render a form, capable of creating a new bear.

#### Introducing MongoDB

Mongodb is a non-relational database. It is really nice for javascript developers because it stores data in formats that we are used to working with. A single piece of data is known as a document. In our application here is what a document will look like:

```js
  var someBear = {
    name: "Winnie the pooh",
    species: "Honey Bear",
    color: "Golden Brown",
  }
```
The above is a single document, a bunch of these documents, or bears, is known as a collection. A collection is just an array full of objects.

`var allBears = [someBear, anotherBear, moreBear];`


When the EJS page to show all bears, is rendered, it will be displaying actual data from our bears collection.

In order to interactive with our database we will design a __RESTful__ API

The types of interactions we have with our database are described by __HTTP__ verbs.

#### GET
This verb is used for retriving data.

#### POST
This verb is used to `create` a new piece of data.

#### PUT
This verb is used to edit.

#### DELETE
An API that implements all of these methods is known as a ### C.R.U.D. API. Because you have the ability to Create, Read, Update, and Delete.

----
#### Mongoose
We will be implementing routes using express `app.get` to apply our HTTP verbs that interact with our database. Mongoose is a tool layerd on top of Mongo, that makes these routes much easier to implement. It is known as an ORM (Object Relational Mapper).

A route that goest to our database, retrieves all bears, and sends these bears back in JSON would look like so:

```js

  app.get("/bears", function(req, res){
    Bear.find(function(err, bear){
      if(err){
       return "error getting all bears from database"
      } else {
      res.json(bear)
    }
  });

```
----


### Implementation

#### Step 0: Project Setup

We will begin by creating a basic server configured with express, ejs, and body parser.

`touch server.js`

`npm init` -> hit enter to accept defaults

We do not want to keep track of our node modules in GitHub, so we tell git to ignore all of these files.

`echo "node_modules/" >> .gitignore`

`npm install --save express body-parser ejs`

Make sure you look at `package.json` to see if your dependencies were updated.

Configure your server to create a basic express server, tell it to use the view engine ejs, and apply the body-parser middleware to your application.

```js
var express = require('express');
var app = express();
var bodyParser = require('body-parser');

app.use(bodyParser.json());
app.use(bodyParser.urlencoded({ extended: true }));
app.set('view engine', 'ejs');

var server = app.listen(3000, function(){
  console.log('Server 🔥🔥🔥ed up on PORT 3000');
});

```

Ensure that your is functional before committing your code:
`nodemon server.js`

----
#### Step One: EJS Pages
In this step we will make the appropriate EJS files, and make routes to server these files.

Remembering that EJS pages must live in the views folder, create pages for index, view, and post.

`mkdir views`

`touch views/index.ejs views/view.ejs views/post.ejs`

Update each EJS page to have a basic HTML implementation. In `view.ejs` add some HTML for an unorderd list of bears. This is where our bears will eventually go. In `post.ejs` add a basic HTML form with input fields for bear name, species, and color.

Next we will define our routes that are responsible for serving each one of our `EJS` pages.

```js
// server.js

app.get('/', function(req, res) {
  res.render('index');
});

app.get('/view', function(req, res) {
  res.render('view');
});

app.get('/post', function(req, res) {
  res.render('post');
});

```

Make sure you test your endpoints before committing your code.
