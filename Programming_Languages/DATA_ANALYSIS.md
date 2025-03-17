## Filling in missing values using the ``fillna()`` method
When filling in values using the ``fillna()`` method, it returns a new series / Dataframe but does not modify the original list. To modify the original list use:
```
import pandas as pd
data_df = pd.read_csv("")
data_df["Gender"].fillna("Female", inPlace=True)

#or
#replacing the column
data_df["Gender"] = data_df["Gender"].fillna("Female")
```
### selecting rows with empty values
To select rows only with empty values:
```
filtered_data = data_df.isna().any(axis=1) #capture rows only
filtered_data_df = data_df[filtered_data]
print(filterd_data_df)
```

### check data type of a column
```
column_data_type = data_df["columnName"].dtype
print(column_data_type)
```


### **cleaning data**
``dropna``() method
the ``dropna()`` method is used to drop any rows by default that have a Nan. 
the ``dropna()`` method receives arguments and can drops a column or a row:

```
data_df = data_df.dropna(axis=0) # drops rows which is set by default
data_df = data_df.dropna(axis=1) # drops column with NaN
```

### **convert datatype of a column**
To convert datatype of a column use the following:
```
data_df["movie_rating"] = data_df["movie_rating"].astype(str)

```


### **resetting index values after filtering**

To reset index values after perform some filtering on your dataset use the ``reset_index()`` method.

```
high_perfoming_students = data_df[data_df["marks"] > 80].reset_index(drop=True)
```

### **Sorting Values for dataset**
To sort values for a dataset we use the  ``sort_values()`` method.  
```
high_performing_students.sort_values(by=["marks"], ascending=False)
```

### **value_counts()**
The ``value_counts()`` method returns the number of times a value has appear in a dataset.

To check the columns in the value_counts() series object use the ``.columns`` 
Example
```
student_grades = student_data_df.value_counts()
student_grades.columns
```


### **Filtering data between values**
Given students marks and you would want to filter a specific range do the following:
```
student_average_df = student_df[student_df["marks"].between(5, 7.9)]
```

## **Combining multiple datasets**
To combine multiple datasets use:
1. concat() method
the concat() method takes a single argument. The dataframe to be combined are given in an array
Example:
```

 import pandas as pd
>>> my_student_dict ={"name": ["alson", "java", "html5"], "age":[23, 24, 25]}
>>> my_class_b = {"name": ["nodejs", "expressjs", "mongodb"]}
>>> print("#get each dataframe object")
#get each dataframe object
>>> class_b_df = pd.DataFrame(my_class_b)
>>> class_a_df = pd.DataFrame(my_student_dict)
>>> student_data_df =pd.concat([class_b_df, class_a_df], ignore_index=True)
```

## **To remove duplicates**
To remove duplicates use the ``drop_duplicates()`` method which by default drops all duplicate rows. 
```
new_data_df = data_df.drop_duplicates()
```

### **``df.loc[]``**
The **`df.loc[]`** method in Pandas is used for **label-based indexing** to access rows and columns of a DataFrame.
(one can access the entire row of a given dataset and if the column is specified only the columns in the given row are returned)
Syntax:
```
df.loc[row_index, column_label]
```

if no column_label is given it returns the entire columns
Example:
```
>>> import pandas as pd
>>> data = {
...     "Name": ["Alice", "Bob", "Charlie"],
...     "Age": [25, 30, 22],
...     "Grade": [85, 92, 78]
... }
>>> data_df = pd.DataFrame(data)
>>> data_df
      Name  Age  Grade
0    Alice   25     85
1      Bob   30     92
2  Charlie   22     78
>>> data_df.loc[1]
Name     Bob
Age       30
Grade     92
Name: 1, dtype: object
>>> data_df.loc[2]
Name     Charlie
Age           22
Grade         78
Name: 2, dtype: object
>>> data_df.loc[2, ["Name", "Grade"]]
Name     Charlie
Grade         78
Name: 2, dtype: object
```

## **Retrieve Maximum and Minimum Values For Entire Row**
To retrieve the entire row for Maximum and Minimum values, we use, **`idxmax()`** and **`idxmin()`**

