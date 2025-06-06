## Loading data from json file
use the json module
```
import json
with open("file_location", "r") as file:
		data_dict = json.load(file)
```
## Dictionaries
a built in data structure that stores values using key:value pairs. The keys are immutable, must be unique and the values are mutable(can be changed).
```
my_dict = { "alpha" : 1, "John": 99, "Jane": 101}
print(my_dict)
```
 
 ***appending data to dictionary***
 ```
 my_dict["sape"] = 101
 print(my_dict)
```

***del data from dictionary***
delete data from a dictionary by using the **del** keyword followed by the key_name
```
del my_dict["sape"]
print(my_dic)
```

***accessing key values only***
Given dictionary
```
user_data = {
			"name":]"johnte", "caroline", "bigggie", "elisha", "mayabi"],
			"age":[25, 23, 27, 23, 43]
			"country":["kenya", "russia", "chile", "chad", "japan"]
			}

```

To access only the key values use the keys() function
method 1: returns a key object value containing all the keys of the list
```
key_values = key in user_data.keys()
for key_item in key_values:
	print(key_item)
```
method 2 : returns a list using list comprehension
```
keys = [key for key_value in user_data.keys()]
```
the method above provides a list of the key values which can be used for searching for similar word or occurrences using the difflib module.

## difflib module
the difflib module can be used to look up if a string has a similar occurrence to a word in a list using the ``get_close_matches()`` method
```
import difflib as dff
fruits = ["apple",  "lemon", "orange", "waterlemon", "banana", "ovacado"]
fav_fruit = input("Enter your favourite fruit : ")
closest_match = dff.get_close_match(fav_fruit, fruits, n=3, cutoff=0.6)
for item in closest_match:
	print(item) # display closest items similar to fav_fruit in fruits list
```
options for the ``get_close_match()`` are :
``fav_fruit`` : the word to be used for searching for similarity 
``fruits`` : the list to be used for searching 
``n = 3``  : number of items to be returned which have similarity (optional = default = 3)
``cutoff = 0.6`` : percentage for the values with similarities to be returned in the list

## List Methods
A list is an ordered data structure used to hold several elements of different or same data types. 
```
my_list = [1, 2, 3, 4, 5]
```

>>***methods***

.append() = used to add an item to the end of a list
.sort() : arrange elements. Use with the key to provide more functionality
.reverse() : reverse the elements in the list
.index(x) : return the index value of the element x given
.index(x, start, end) : the index method can also take up start and  end arguments which specify the range for which the list is to be searched.

## Queues
To use queues use the module collections
```
from collections import deque
my_list = [1,2,3,4,5,6,7,8]
my_queue = deque(my_list)
my_queue.popleft()
my_queue.append(12)
```

## PEMDAS
Power
exponential
Multiplication to Division
Addition and Subtraction
Example :
```
((1 + 3) * (9 - 2) / 2) ** 2
```

## Math.ceil()
The ``math.ceil()`` function rounds of a floating or a decimal number to a whole number or integer
```
import math
test_value = 2.17
print(math.ceil(test_value))
```

## Data type
To confirm the data type of a variable use ``type()``
***Integers***
```
number = 10
print(f"Value of variable number is {number} and data type is {type(number)})
```
***Floats***
floats are numbers with a decimal point and can also be represented as a fraction.
```
myfloat = 22/7
print(myfloat)
print(type(myfloat))
```
***boolean***
These is either ``True or False``  value. Can be used for comparisons.
Examples :
```
z_one = True
print(z_one)
print(type(z_one))
```
One can also use the ``not`` value which reverses the value of the boolean.
```
z_two = False
pritn(z_two)
z_two = not z_two # value is reversed
print(z_two)
```
Boolean Values are used for comparisons
```
answer = (5 > 3)
print(answer) #True
```
Boolean Operation
```
# multiplying boolean values
print(False * 100) # 0
print(True * 100) # 100
```
***Strings***
Strings is a data type that contains multiple or single characters, numbers or alphanumeric characters. Normally placed inside double quotations.
Strings are immutable as compared to lists whose values can be changed.
```
mystring = "abc"
print(mystring)
print(type(mystring))
```
**string methods**
### Conversion of characters to uppercase, lowercase, capitalize
to convert into uppercase:
```
def upperCase(mystring):
	if type(mystring) == str:
	mystring = mystring.upper()
```
to convert to lowercase:
```
def lowerCase(mystring):
	if type(mystring) == str:
	mystring = mystring.lower()
```
to capitalize each word in a string
```
def capitalize(mystring):
	if type(mystring) == str:
		mystring = mystring.title()
```

## Round() method
The round() method is used to round-off numbers to the given decimal places
It takes 2 arguments :
``round (argument1, number_of_decimal_places)``
if no argument is given it returns a whole number
```
my_decimal = 22/7
print(type(my_decimal))
print(round(my_decimal, 3))
```

## type conversion
Converting different data types to other data types.
```
myNumbers = 3.
print(myNumbers)
print(type(myNumbers))
#conversion
myNumber = int(myNumber) #Always reassign the value
print(myNumber)
print(type(myNumber))
```
The same goes for  float()  inbuilt function
```
myNumber = 10
print(float(myNumber)) # return float(decimal) number
```
## FUNCTIONS
Python functions. To call a python function, use name followed by parenthesis in which an argument can be given.
```
print(spam_count)
```
the print is an inbuilt function and is called above

## Operator overloading
depending on how an operator is used, results in a different meaning.
Example:
```
spam_count = 0
spam_count = 4
viking_song = spam_count * " spam "
print(viking_song)
```

## inbuilt functions
+ min - returns the least value
+ max - returns the max value
+ abs - returns the absolute value which is value of the number

```
print(min(10,7,9,11))
print(max(120,10,1))
```

## Backslash character
the backslash character is used as an escape character
`` \ ``

## Multiple assignment of data
Python enables us to assign multiple values to a variable
Example:
```
a = 10
b = 20
a, b = b, a
```

##  Methods and attributes
Methods and attributes are different. In python, objects are instances of classes since Python programming language is a OOP(object oriented programming language).
a method is a function that is attached to an object. 
Example :

upper() : convert all characters in a string to uppercase
```
name = "John Doe"
print(name.upper())
```

pluto_mass = 1.303 


## Setting up a python virtual environment
Setting up python virtual environment using venv module  is the most preferred.   Other tools to set up virtual environment in python are ``virtualvenv`` and ``conda``.

To setup python venv virtual environment use the following command:
``python3 -m venv venv`` execute the command in the folder of your project
To activate the venv environment, ensure you are in the folder in which you created your virtual environment
```
cd Python_Virtual_Environment
source venv/bin/activate
```
After this the prompt in your terminal will start with (venv)
Now you can install external dependencies for your project such as ``opencv``
``python3 -m pip install package_name``
``python3 -m pip install opencv``
To deactivate the virtual environment use ``deactivate`` command.

### **Switch case statements**
```
match varName:
	case "equalToMe":
		performAction || assignvalue
```


## saving machine learning model
To save your machine learning model we use joblib or pickle. the dump method is used  to create the model and the load method is used to load the model for use. 


in Python, the hashlib module is a standard module, which is preinstalled(it's installed when python is installed in a computer)

The hashlib module in python required data to be in byte format becuase hashing function s operate on byte and not string
in python string are in Unicode while hashing algorithms require data to be in raw byte format


```
print(data.encode())
```

To view the encoded data in Raw Bytes use:
```
encoded_data_list = list(encoded_data)
print(encoded_data_list)
```
the ``update()`` function is used to pass the encoded data to the hash function. Also since hashing works by processing data in chunks, the ``update()`` functions enables you to add data incrementally *(instead of hashing all the data at once)* 


the ``hexdigest()`` function is the output interface for providing the hash in hexadecimal format. One can also access the hash in binary format, though unreadable for humans, it can be usefull in low level applications. 
The hash is represented in hexadecimal format for the following reasons:
- readability
- compact represantation
- standard in cryptography

```
data_hash = sha256_hash_object.hexdigest()
```
to view in binary:
```
data_hash_binary_format = sha256_hash_object.digest()
```

hash_practical.py file:
```
import hashlib
data="Hello Porsche I wanna try You"
sha256_hash = hashlib.sha256()
print(data)
print(data.encode()) # this will print with b as first b'Hello Porsche I wanna try You'

data.encode()

# to view in Raw Bytes use the following
for byte in encoded_data:
	print(byte, end=" ")

print("\n")
encoded_data_list = list(encoded_data)
print(encoded_data_list)

# the udpate function only acts as an input interface to the hash 
# function(sha256 function)

sha256_hash.update(encoded_data)

# to view the output use the hexdigest()

data_hash = sha256_hash.hexdigest()
print(f"The hash for the data in hexadecimal : {data_hash}")

# to view the binary hash
data_hash_binary = sha256_hash.digest()
print(f"The hash for the data in binary \n {data_hash_binary}")
```


### **join() method**
the join method is used to join items in an iterable || concatenate elements of an iterable (like a list or tuple) into a single string, with a specified separator.
Syntax: `` seperator.join([iterable])``

```
myWords = ["Jupiter", "is", "the", "larget", "planet", "in", "the", "Solar", "System"]

mySentence = " ".join(myWords)
print(mySentence)
```


### **list methods:**


### **``zip()``**

the ``zip()`` function is used to  combine  multiple iterables, such as lists or arrays,  element by element in each of the iterables given, creating an iterator of tuples.
```
names=["Alice", "John", "Constantine"]
scores=[90,91,89]
print(list(zip(names,scores)))
```
If the length of the given iterables are different, it stops at the shortes one.

You can zip() that is combined more than 2 lists.
You can also use it in a for loop.

```
for name,score in zip(names,scored):
	print(f"{name} scored {score}")
```

**You can also unzip data**
```
>>> names=["Alice","John","Constantine"]
>>> scores=[90,89,91]
>>> address=["Washington", "New Castle", "London"]
>>> data = list(zip(names,scores,address))
>>> data
[('Alice', 90, 'Washington'), ('John', 89, 'New Castle'), ('Constantine', 91, 'London')]
>>> 
>>> newNames,newScores,newAddress = zip(*data)
>>> print(newNames)
('Alice', 'John', 'Constantine')
>>> print(newScores)
(90, 89, 91)
>>> print(newAddress)
('Washington', 'New Castle', 'London')
>>> 
```


### **Conditions**
if statement
```
if true: 
	execute # execute only if true
```

**if else condition**
```
if false:
	skip
else:
	execute
```

**if elif condition**
```
if true:
	execute
elif true:
	execute
else: 
	execute
```

### **lambda**
anonymous function
```
lambda parameter: operation
```
Example:
```
>>> add = lambda x, y : x + y
>>> add(10,12)
22
```


