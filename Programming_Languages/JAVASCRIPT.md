### TABLE OF CONTENTS
[Events](Event listeners)


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
Because the array is converted to a string using toString() and then concatenated to the string "1".


# Event listeners



## IIFE
Immediately invoked function expression 
