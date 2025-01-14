mongodb is a nosql database management system that can manage a large amount of data. 
NOSQL : not structured query language.
Related data is stored as a single document.
data is stored in field value pairs





to get started on MongoDB run :
``mongosh`` on terminal
To show database use: ``show dbs``
To create database use: ``use school``
To create collection: ``db.createCollection("students")`` : add collection to current database
To drop a database use: ``db.dropDatabase()``


## To insert documents in MongoDB database:
```
use schools
db.createCollection("students")
db.students.insertOne({name:"SpongeBob", age: 30, gpa:3.2})


```


to check the data you've fed /inserted in a collection use:
db.student.find()


## to insert multiple documents/data use:
```
db.student.insert([
	{name: "Earth", age:1600, gpa:4.0}, {name: "Jupiter", age: 4900, gpa:4.1}, {name:"Mars", age:2900, gpa:3.9}, {name: "Andromeda", age:7000, gpa:4.9}
])
```


## datatypes in MongoDB
- String  : "Larry Jackal" , "Lary 123"
- integer : whole numbers , Example: 23, 32
- double : decimal, Examples: 4.3, 4.2
- boolean : true/false
- dateObjects :  example : registerDate :  new Date()
- null : 
- Arrays : Example: courses : ["Biology", "Chemistry", "Calculus"]
- dictionary : Example : {street: "123big", city: "Tokyo"}


## sorting data:
``db.students.find().sort({name:1})``
``db.students.find().sort({gpa:1})``
``db.students.find().limit(3)`` : returns 2 documents


## find() method
The find() method syntax:
``db.collectionName.find({query},{projection})``

**Query Examples:** 
``db.student.find({name:"Spongebob"})``
``db.student.find({gpa:4.0})``
``db.student.find({gpa:4.9, name: "Andromeda"})``


**Projection Examples:**
The projection is used for selecting specific fields that are to displayed
Example:
To select the collection
``show collections``
``show tables``
``db.students.find({}, {name:true, _id:false})``
## updating documents in MongoDB
Updating one document
Syntax:  ``db.collectionName.update({filter}, {update})

```
db.planets.update({name: "Earth"}, {$set:{aroundSun: 365}})

db.planets.update({name: "Jupiter"}, {$unset:{aroundSun: false}})

db.planets.update({name: "Jupiter"}, {$unset:{aroundSun:""}})
```

updating many documents:
```
db.planets.updateMany({fullTime: false}, {$set:{onlineclass: true} })
```

## deleting documents/data
``db.dataCollectonName.deleteOne({name: "Spongebob"})``
``db.dataCollectonName.deleteMany({registerData:{$exist:false}})``
## Operators
```

less than : $lt
greater than : $gt
greater than and equal : $gte
less than and equal : $lte
not equal : $ne
in : $in["Sponsebob", "Sandy"]
not in : $in["Spongebob", "Sandy"]
```


```
db.students.find({age:{$gt:30}})
db.students.find({name:{$in:["Elon Musk", "Trump Huston"]}})
db.students.find({name:{$nin:["Elon Musk", "Trump Huston"]}})
```

## Logical Operators
$and : logical operator and return if both conditions are met
``db.students.find({$and: [{fullTime:true}, {age:{gt:20}}]})``

$or : return data/document at-least one condition evaluates to true
``db.students.find({$or:[{age:{$gt:20}}, {year:{$gt:2000}}]})``

$nor : return if both conditions evaluate to false
``db.students.find({$nor:[{success:true}, {age:{$gt:80}}]})``
``db.students.find({age:{$not:{$gte:30}}})`` 
the benefit of using the $not operator it also checks for null values.
