## Variables
Store data at a specific memory location .
Assigning a value to a variable at the moment of its declaration is known as initialization.
*declaration*
``let greet;``
*initialization*
``greet = 'Hello World';``
assigning values to variables the left value is always assigned to the right value
**Example**
```
let firstCharacter = "Hello";
let secondCharacter = "World";
secondCharacter = firstCharacter;
console.log(secondCharacter); //Hello
```
## Primitive data types
***Strings***
These are data types in double or single quotations
``let character = "Gard Alson";``
***Numbers(integers)***
these are numbers
``let luckyNumber = 10;``
## Console
The console allows you to print javascript code. 
``console.log("hello!");``
Printing out an uninitialized variable(not assigned any value) results in ``undefined``
## Non-primitive data types
These are data structures that can be used to store complex data and more that 1 data type.
Example : arrays
## Arrays
To declare an array use :
``let myArray = [];``
***Indexing***
In arrays one can access items, elements using indexing. The first value is always at index 0
**Example**
```
let rows = ["Naomi", "Quincy", "Camperhan"];
console.log(rows[0]);
```
