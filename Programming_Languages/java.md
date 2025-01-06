# java notes

1. package name
a package name should be unique and written in domain name in reverse.
It should be placed in the first line of your program
It entails the description of your product

Example: packagename
``package com.gardalson.javascourse.lesson1``


2. import statement:
every program file will use reexisting code:
To do so we use:
``import com.packagename.fileName``
``import com.marcusbiel.lesson1.car.Bmw`` // imported a specific file
``import com.marcusbiel.lesson1.car.*`` //imported multiple files

- Static imports

3. class:
OOP structure.
a class can contain multiple methods | functions.


4. functions 
``dirve(speed){}``

Types of varialbes:
- Instance variables
- static variables
- local variables
- local variables
- parameter
- argument

5. access modifier
- public: classes defined with the public access modifier can be accessed anywhere in the program.
- private

In any method, you must specify a return value.  this can be void, int, string e.t.c


6. @Test
Indicattes annotation. 

7. constructor
used to create new objects if not exist. 

8. object creation, declaration and allocatoin in a single line.
``Car myPorsche = new Car(1, 320);``

9: ALL lines of code must end with a semi-colon(;).
Indicated the end of the code statement.



In java to execute any code, it must be withina class /*and a method*/
To print a text we  use: ``System.out.println("Hello World");``
All code statements must end with a semi-colon: low level programming
Example:
```
package tutorials;

public class Main(){
        public static void main(String[] args){
                System.out.println("Hello World Welcome to Java");
        } 
}
```

**Variables & Data Types**
```
class Main(){

        public static void main(){
                int value_first = 10;
                System.out.println(value_first);
        }
}
```

There are 5 types of primitive datatypes in Java:
- String
- char 
- int
- double


1. String(String)
```
String greet = "Welcome to Java FreeCodeCamp Tutorial";
System.out.println(greet);
```

2. Character(char)

```
char c = 'w';
System.out.println(c);
```

3. Integer(int)
```
int value_one = 30;
System.out.println(value_one);
```
4. Double(double)
```
double value_two = 20.30;
System.out.println(value_two);
```

**BASIC OPERATION**
PEDMAS : parenthesis, exponential, division and multiplication, addition and subtraction.
I any case when we have both multiplication and division or addition and subtraction the calculation is done from left to right.
``int result = 10 + 2 * 3 - 4/2;``
PEDMAS: parenthesis, exponential, division and multiplication, addition and subtraction
Steps:
3*2 = 6
4/2 = 2
10 + 6 = 16
16 -2 = 14

**Type casting**
```
int x = 100;
int y = 11;
double my_result =x / (double)y;
System.out.println(my_result);
```

To perform typecasting place the datatype in brackets next to the variable you wish to type cast


## taking input data 
To take in put data we use the scanner module.
```
import java.util.Scanner
public class Main{
	public static void main(String[] args){
		// setup scanner
		Scanner sc = new Scanner(System.in);
		// to use scanner
		String scanned = sc.next();
		System.out.println();
	}

}
```
One could say the ``Scanner``  is a datatype
``sc.next()`` : allows us to get the next string from the user. It returns string datatype assigning it to a integer or any other datatype will result s to an error.

To get integer input change ``sc.next()`` to ``sc.nextInt()``
To get boolean Data : ``sc.nextBoolean()`` : true, false
To get decimal data : ``sc.nextDouble()``

To convert the datatype;
```
Scanner sc = new Scanner(System.in);
String user_input = sc.next();

// to convert
int x = Integer.parseInt(user_input);
System.out.println(x);
```


## Conditions and Loops
Example :
```
int x = 10;
int y = 20;
boolearn compare = x < y;
System.out.println(compare);
```

Integers has the following operations:

| Operator | Meaning      |
| -------- | ------------ |
| <        | less than    |
| >        | greater than |
| ==       | equal        |
| !=       | not equal    |


String operations:  

| Operator | Meaning   |
| -------- | --------- |
| ==       | equal to  |
| !=       | not equal |

``&&`` : and 
``||`` : or
!() : not (reverse the value inside the bracker)
 
To compare strings we use the function ``stringVariable.equals("comparisonTerm")``;
```
Scanner sc = new Scanner(System.in);

String user_input = sc.next();

System.out.println(user_input.equals("Hello"));
```



## if else if  else condition
```
if (age > 10)
{
	System.out.println("Age is above 10 " + age);
}
```

if esle:


if else if else: 


##  Arrays


An odd way or odd ball of declaring arrays:
```
String[] newArray = new String[7];
newArray[0] = "Joey";
newArray[1] = "Rachel";
newArray[2] = "Janice";
newArray[3] = "Chandler";
newArray[4] = "Monica";
newArray[5] = "Ross";
newArray[6] = "Rachel";

```


Second way of initializing arrays:
```
int[] myNumbers = {1, 2, 3, 4, 5};
System.out.println(myNumbers[0]);
```
The syntax is :
``dataType[] variableName = {values, values};``
Different types of scanners


## for loops
