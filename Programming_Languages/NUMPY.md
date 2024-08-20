## Description

## Numpy arrays
initializing an np array.
```
import numpy as np
a = np.array([1,2,3,4])
print(a)
```
* Creating 2 dimensional arrays
```
my_array = 
```


### random sub module
random is a submodule within the numpy library that provides several functions used for  generating random numbers and sampling from various distributions(list).

**Key functions and Use Cases:**
1. Generating random numbers:
+ ``np.random.rand(d0, d1, ... , dn)``
Generates only positive numbers.
create an array of random floats in the interval of (0.0, 1.0) 1.0 exclusive
Example:
Int the example below generates random floating numbers each time it's run ranging form 0.0 (inclusive) and exclusive(1.0)
```
np.random.rand() # random values =0.7836079835715285
```
+ ``np.random.rand(2,3)``
*np.random.rand(rows,column)
Generate an array of 2 rows and 3 columns with values ranging form 0.0 to exclusive(1.0)

+ ``np.random.randn(d0, d1, ..., dn)``
Generates both positive and negative numbers.
Return a sample from the standard normal distribution

+ ``np.random.randint(low, high, size, dtype=int)``
Generates a random integer 
Example:
``np.random.randint(10)``
