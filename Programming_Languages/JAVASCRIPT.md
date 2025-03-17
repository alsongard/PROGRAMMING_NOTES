### TABLE OF CONTENTS

## conversion of char/strings to uppercase and lowercase
JavaScript strings are immutable there are 2 types of methods that can be used to convert strings to uppercase
#### Method 1 
```
toUpperCase()
let mystring = "hello world";
mystring = mystring.toUppercase();
console.log(mystring);
```
#### Method 2
Convert only the first letter one is required to use multiple methods for these
```
let myName = "gard alson safari";
new_name = myName.char(0).toUpperCase() + myName.slice(1);
console.log(new_name);
```

## type conversion using Number() and String() method
*Explicit Type Conversion*
***To convert a string to a number***
```
let myString = "23";
let sum = 10 + Number(myString);
console.log(sum);
```
***To convert a number to a string
```
let myAge = 32
console.log(typeof(String(myAge)));
```

***Type Coercion***
To convert an array to a string use the toString() method
```
myArray = [1,2];
console.log(myArray + "1"); //result 1, 21

```
Because the array is converted to a string using ``toString()`` and then concatenated to the string "1".


# Event listeners



## IIFE
Immediately invoked function expression 

## Changing css style  
To change the style of an element use the following syntax:
1. Using style :
``elementVariableName.style.property = "value";``

Example:
```
let myImage = document.querySelector(".myImage");
myImage.style.opacity = "0.7";
```

2. ``Classlist`` methods:
**using the add() methods:** 
```
<style>
.myParagraph{
	padding:10px;
	background:liear-gradient(to right, red,blue);
}
</style>
<body>
<p id="myPara">Hello there.. welcome to javascript</p>
<button onclick="changeStyle()">Click me to change style of paragraph above</button>
<script>
	let myParagraph = document.getElementById("myPara");
	function changeStyle(){
		myParagraph.classlist.add("myParagraph");
	}
<script>
</body>
```

**remove classList methods**
```
<script>
	let myParagraph = document.querySelector(".myPara");
	myParagraph.classList.remove("myStyle");
</script>
```

**toggle method**
How to change the style of the element using  toggle method:
```
<script>
	let new_paragraph = document.querySelector(".new_paragraph");
	new_paragraph.classList.toggle("myParaStyle");
</script>
```

**tenary operations**
Syntax :
```
let isGoingOut = true;
let answer = isGoingOUt === true ? "Yes" : "No";
console.log(answer);
```



## setTimeOut() function

the setTimeOut() takes in 2 arguments that is: a function and a time value in milliseconds.

Example:

```
function myGreeting()
{
	console.log("Hello there my Name is : Earth");
}
	setTimeOut(myGreeting, 5000);

```

**Math.random()**
the ``Math.random()`` is used to generate pseudo-random floating point numbers between `0` (inclusive) and `1` (exclusive). It does not take any arguments. However, you can manipulate its output to fit different ranges. *(by pseudo-random we mean that the values aren't entirely random, they are actually determined by a mathematical algorithm)*

```
console.log(Math.Random()); generates a floating value between 0.000.. to 0.999
```

To generate a random integer between 0 and 9:
```
function getRandomInt(max)
{
	return Math.floor(Math.random() * max)
}
```


### **spread operator**
the spread operator is used to copy elements from one array to another. 
``` 
const arr1 = [1, 2, 3];
const arr2 = [4, 5, 6];

const combinedArr = [...arr1, ...arr2];
```

### **arrow function**
arrow functions are anonymous, however they can be assigned an identifier.
```
const printGreeting = ()=>{
	console.log("hello there");
}

// to call the function do the following:
printGreeting();
```
one calls the function by calling the variableName assigned to the arrow function..

An Arrow function can have one or multiple arguments.
if it's a single argument, one can omit the parenthesis.
```
const printMessage = org =>{
	console.log(`${org} is awesome!`);
}
printMessage("freecodecamp");
```

arrow function can also return a value. An example is provided below:
```
const addTwoNumbers = (num1, num2) =>{
	return num1 + num2;
}
console.log(addTwoNumbers(3,4));
```

if the body of the arrow function is performing a simple expression, one can omit the curly braces and the ``return`` keyword
```
const addTwoNumbers = (num1, num2) => num1 + num2;
console.log(addTwoNumbers(3,4));
```

however if the body has multiple line of code, one is required to have both the curly braces and the return keyword.

### **map()**
he `map()` method is used to iterate through an array and return a new array. It's helpful when you want to create a new array based on the values of an existing array. 
For example:
```
> squares_array = combinedArray.map((number)=>number ** 2)
[
   1,  4,  9, 16,  25,
  36, 49, 64, 81, 100
]
```

### **join()**
The `join()` method is used to concatenate all the elements of an array into a single string.
```
> const exampleArr = ["This", "is", "a", "sentence"];
> const sentence = exampleArr.join(" "); 
> sentence
'This is a sentence'
```