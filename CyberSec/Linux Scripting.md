## Introduction
To write a linux script one must start with the shebang line and followed by code/statements that will be executed. 
Remember to change the permissions of the file to execute the file.

To execute the file use ``./file-name``
```
#!/bin/bash
echo "Hello world"
```

**Echo**
To echo out a statement, we use the following:
```
echo "hello world"
```
to echo a variable:
Syntax: ``echo $variableName``
```
name="Techie World"
echo $name
```

**Variables**
when declaring variables in bash scripting, no spacing between the var, equals and the value assigned to them
```
name="techie world"
echo $name
```


**Concatenation**
To concatenate a variable in statement or a string, we use ``"${varName}"``
```
foo="Hello"
world="Game"
echo "${foo} ${world}"
```


**For Loops**
to use the for loop we do the following:
```
for n in a b c;
do
	echo $n
done
```
result:
```
a
b
c
```
 if the elements were with a comma it would result in the following:
 ```
 for n in a, b, c;
 do 
	 echo $n
done 
```


# BASH SCRIPTING FREECODECAMP

when working with variables do not leave some space
```
FIRST_NAME="Jupiter"
echo "Hello " $FIRST_NAME
```

To use variables we must put a dollar sign/symbol before the variableName

Incase your variable names has spaces in it, enter it in double quotes
```
data="Sun Feb 11:50:59"
echo $data
```

**Positional arguments**
arguments can be defines as input that is given to a command. Positional arguments start from 1 and are seperated by a space
Example:
```
#!/bin/bash
echo $1 $2 $3
```

run : ``./file_name Welcome back Mr.Alson``


**Input/Output redirection**
1. Input
single quotes
```
wc w < myFile.txt
```

Double quotes
```
cat << EOF
ENTER TEXT
EOF (TO END)
```

Tripple quotes
```
wc <<< "hello there"
```


1. Output
> (write to new file)
echo "hello Mars, I am comming" > mars.txt
>> (append to file)
echo "hello there" >> myfile.txt

| pipe (pass output of previous command to new command)
```
ls -lt | grep "*.txt"
```

**Test Operators**
```
[ var|string = var|string]
echo $?
```
this can also work on numbers
``[ 1 = 1 ]``


```
[ 1 -eq 1 ]
echo $? === 0(true)
```

**switch case statement**
used when you have multiple option and single input for comparison
```
case variableName in 
    java | kotlin)
        echo "action"
    ;;
    javascript)
        echo "aciton"
    ;;
    *)
        echo "to do this"

esac
```

**Working with arrays**
```
MY_FIRST_ARRAY=(10 20 30 40 50 60 70 80 100)

echo $MY_FIRST_ARRAY

# print out specific value based on index
echo ${MY_FIRST_ARRAY[0]} 

echo ${MY_FIRST_ARRAY[@]}
```

**For Loops**
```
my_first_array=(Jupiter Mars Earth Uranus Neptune)
for item in ${my_first_array};
do 
    echo $item
done
```

**Functions**
```
showToday()
{
    todayDate=$(date | cut -d " " -f1,2,3)
    echo "Today's date is " $todayDate
}
showToday
```

**NOTE**
``${1,,}`` :used for converting a string to lowercase

**command subsitution**
``user_file=$(cat "$1")``
if i were to pass ``user_file=cat $1`` only the cat command is assigned to user_file and for the ``"$1"`` this ensures that even file with spaces will be treated as a single input
