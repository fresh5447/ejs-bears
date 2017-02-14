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
```
 var allBears = [someBear, anotherBear, moreBear];
```

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
app.get('/bears', function(req, res){
  Bear.find(function(err, bear){
    if(err){
     return "error getting all bears from database"
    } else {
    res.json(bear)
  }
});
```






### tools

### commit our changes over time.
