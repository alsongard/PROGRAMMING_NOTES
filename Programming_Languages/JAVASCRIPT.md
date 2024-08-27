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

