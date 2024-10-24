## Variables
Store data at a specific memory location .
Assigning a value to a variable at the moment of its declaration is known as initialization.
*declaration*
``let greet; //declare variable``
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
***const***
The const keyword is used declare variables whose values will not change. While using the const variable, one must initialize(not possible to declare only)
```
const firstName = "Helloo";
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
``let myArray = []; //empty array``
***Indexing***
In arrays one can access items, elements using indexing. The first value is always at index 0
**Example**
```
let rows = ["Naomi", "Quincy", "Camperhan"];
console.log(rows[0]);
```
Accessing the last value of an array we use the length of the array - 1
```
 console.log(rows.length - 1);
```
***mutation***
Arrays in javascript are mutable, meaning an array values can be changed
```
rows[2] = 10;
```

#### Array Methods
These are functions that are part of an object namely the array data type.
1. push()
The push() array method is used to add an element to an array at the end . For the push() method returns the number of items in the array
```
rows.push("freeCodeCamp);
```
1.  pop()
The pop() array method is used to remove the last element in an array. It returns the value removed.
```
let popped = rows.pop();
console.log(popped) // returns the last element removed
```
  1. unshift()
The unshift() array method is used to add a value at the beginning of the array and it's return value is the new length of the array. Takes a value as an argument.
```
const numbers = [1, 2, 3];
const unshifted = numbers.unshift(5)
console.log(unshifted); // 4 = new length
```
1. shift()
The shift() array method is used to remove the first element in an array. 
```
const numbers = [1, 2, 3];

console.log(numbers);

const shifted = numbers.shift();

console.log(`Value of shifted is ${shifted}`);
```
## Conditions

**IF()**
The  if condition is used to check if the  condition evaluates to true
Example:
```
if (condtion == true)
{
	//execute action
	console.log("Condition is true")
}
```

We have 2 types of values that can be given to the if condition.

| truthy        | falsey           |
| ------------- | ---------------- |
| true(boolean) | false(boolean)   |
| "string data" | null             |
|               | ""(empty string) |
|               | undefined        |
|               | Nan              |
|               |                  |
**ELSE IF**
The ``else if()`` statement is used when checking several conditions
**else** statement is used when both ``if`` and ``else if`` condition evaluate to false.
```
if ("") {
console.log("Condition is true");
} else if (5 < 10) {
console.log("5 is less than 10");
} else {
console.log("This is the else block");
}
```

**WHILE() CONDITION**
The while condition is used to check if the condition  evaluates to true:
Example if i  is less than ten execute;
```
let i = 10
while (i < 10)
{
	console.log(`Value : ${i}`);
	i++;
}
```
## Operators
1. Equality Operators
   ``==`` : used to check if given values are equal
   ``===`` : Strict equality operator that is used to check if the given values are equal and of the same data type. Most preferred equality operator to be used.
   