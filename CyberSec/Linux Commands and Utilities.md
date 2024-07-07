## shuf
Definition: shuf command is used to randomize given input data.
Syntax of the command is :
``shuf [options] [data]``
Examples and descriptions :
* Input from terminal direct
```
shuf -e 1 2 3 4 5 6 7 8 9 10
<!---the following command results in a shuffled view of the numbers--------> 
```

 * Limiting number of output 
To limit the number of outputs use the -n option followed by a number 
```
test.txt {
1
2
3
4
5
6
7
8
9
10
}
shuf -n 5 test.txt
<!----display 5 lines of numbers which are shuffled----->
```

* To display more than the number of lines a text/file, use the -r and -n option
```
shuf -r -n 25 test.txt
```
display 25 lines