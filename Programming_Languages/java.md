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
To use for loops follow the following Syntax:
```
for (int varialbe; condition; increment/decreemnt)
{
	Action/Execute;
}
```
example:
```
for(int i=0; i < 10; i++)
{
	System.out.println(i);
}
```

or:
```
int[] myArray = {1, 2, 3, 5, 7, 9, 11, 13, 17, 19, 23, 29};
count = 0;
for(int element:myArray)
{
	System.out.println("index  " + count + ":" +  element);
}
```

``break;`` : it is used to stop the iteration in a for or a while loop.



## sets
A set is a collection of unordered elements which are unique. 
a set only has unique numbers, it has no definite length such as how an array can have. ``String[] names = String[7]``.

```
Set<integer> t = new HashSet<Integer>();
```

Syntax: 
``keyWord(Set) <Datatype>(integer/string..) variableName= new Hashset <Datatype>();
``Set <String> users = new Hashset <String>();``

To add things to a set:
```

users.add("John");
users.add("Jim");
users.add("James");
users.add("Joeh");
users.add("Joeh");
users.remove("Joeh"); // used to remove an item in  a set
System.out.println(users);

boolean x = users.contains("James"); // checks for the element in the array return boolean
```

Set methods:

| Method                 | Operation                                   |
| ---------------------- | ------------------------------------------- |
| setName.remove(item)   | Remove an item from set                     |
| setName.contains(item) | check if item exist in set & return boolean |
| setName.isEmpty()      | checks if set is empty                      |
| setName.clear()        | clear set , remove everything               |
| setName.size()         | return the number of items in the set       |

``HashSet`` : standard set
``TreeSet`` : ordered unique elements in a tree data structure
``LinkedHashSet`` :  

## ArrayLists

 Syntax: 
 `` ArrayList<dataType> varialbeName = new ArrayList<dataType>();``
 
 .add(a) : add value(a) to ``arrayList``
 .get(a) : return value(a) at given index
 .set(a, b) : at the given index(a) set to value(b)

```
ArrayList<Integer> myNumbers = new ArrayList<Integer>();
t.add(1); // add integer to list
t.get(0); // get value at index 0
t.add

// set something at a given index
t.set(1, 5); //(index, value)
```

## Maps 
there are 3 types of maps:
tree map
hash map
linked hash map

map is a key value pair similar to dictionaries in python
Hash Maps
hash maps have no order. if key values are repeated and have new values, this replace the new value.
```
Map m = new HashMap();
m.put(11, 999);
m.put("tim", 200);
m.put("jeo", 300);

System.out.println(m);
```

Tree Maps
in a tree maps the key data types have to be the same. This keys are sorted when accessing them.
```
Map t = new TreeMap();
t.put(4, "Mars");
t.put(5, "Jupiter");
t.put(6, "Uranus");

System.out.println(t);
```

Linked Hash Maps
in linked hashmaps, the key pair value is stored in the order in which they are written.

```
Map l = new LinkedHashMap();

l.put("Manager", "Margaret");
l.put("CEO", "James Cameroon");
l.put("secretary", "Dona Tovalds");

System.out.println(l);

```


## Functions

*Note : the following function is in the file and in the main class *
```
public static void hello(string name)
{
	System.out.println("Hello " + name);
}

```

In main function call the function as show below:
```
public static void main(String[] args)
{
	hello("Earth");
}
```

## Classes
### Class Attributes
private :  attributes that have private attribute can only be accessed within that class they're defined with.
public: attributes/variables and methods that have the public access modifier are accessible to any of the child classes within and in other packages.
protected: attributes and methods are accessible in different classes in the same package but not accessible to other packages.
### **Access Modifier Comparison Table**

|Modifier|Same Class|Same Package|Subclass (Different Package)|Other Packages|
|---|---|---|---|---|
|**`public`**|✔|✔|✔|✔|
|**`protected`**|✔|✔|✔|✘|
|**`default`**|✔|✔|✘|✘|
|**`private`**|✔|✘|✘|✘|
this is used to reference attributes of a class.

To create a class create a new file

**Constructor**
Constructor should have the same name as that of the class an do not have a return type.
It is a special method used to initialize objects and is called when an instance of a class is created. 
Objects in a class can be used to access variables and methods.


Example:
```
public class Book()
{
	String title;
	String author;
	// create default constructor
	public Book()
	{
		System.out.println("Book Created");
	}
}
```

In your main.java file:
```
public class Main()
{
	public void Main()
	{
		Book bookObj = new Book();
	}
}
```
The moment you run this file you will get the "Book Created" string on console/terminal.

There are different types of constructors, namely:
- Default constructors
- Parameterized  constructors
- No-argument constructors (similar to default constructors)

Parameterized constructors:
student.java file:
```
class Student()
{
	private String studentName;
	private String studentCourse;
	private int studentAge;

	public Student(String studentNameInput, String studentCourseInput, int studentAgeInput)
	{
		this.studentName = studentNameInput;
		this.studentCourse = studentCourseInput;
		this.studentAge = studentAgeInput;
	}
	public void studentInfo()
	{
		System.out.print("The Student details are as follows: \n" + "Student Name : " + studentName + "\nStudent Age : " + studentAge + "\nStudent Course" + studentCourse);
	}
}
```
main.java file:
```
class Main()
{
	public class Main()
	{
	System.out.println("Enter student name : ");
	{
		Scanner sc = new Scanner(System.in);
		System.out.println("Enter student Name: ")
		String nameInput = sc.next();
		System.out.println("Enter student course : ");
		String courseInput = sc.next();
		System.out.println("Enter student Age : ");
		int ageInput = sc.nextInt();
		Student studObj = new Student(nameInput, courseInput, ageInput);
		studObj.StudentInfo();
	}
}
```

## inheritance
inheritance is an OOP feature that enables the access of variables and methods from a parent class to a child class.
```
public class Cat extends Dog{

	// the default constructor method should be equal to that of the Dog constructor methods
	private String food;
	public Cat(String name, int age, String food)
	{
		super(name, age);
		this.food = food;
	}
}
```
In your main file, you can access some of the methods/function in Dog class as show below:
```
Cat catObj = new Cat("picky", 2, "Fish");
catObj.speak();
```


## Static 
- static attributes/variables
- static methods

static methods cannot access non-static attributes or variables
static methods can access static variables and other static variables.

Static methods and variables belong to a class and not an instance. static methods can directly access and modify static variables  because they belong to the class.
```
/*
* static variables are shared accross all instances and retain their value
*/

public class StaticIntro2 {
	static int counter = 0;
	private int myLuckyNumber = 1;
	public StaticIntro2()
	{
		System.out.println("Static variable value is : " + counter);
		counter++;
	}

	public static void staticMethod()
	{
		System.out.println("Static variable: " + counter);
		counter++;
		System.out.println("Static variable after incrementing: " + counter);
	}

	public static void main(String[] args)
	{
		staticMethod();
		StaticIntro2 object1 = new StaticIntro2();
		// StaticIntro2 object2 = new StaticIntro2();
		System.out.println("Value of static var is : " + counter);
		System.out.println("Value of non-static variable is " + object1.myLuckyNumber);
	}
}
```

Though static methods cannot access non-static or instance variables, they can be accessed using Object referencing.
```

```