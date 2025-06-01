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

### **checking multiple conditions**
```
filted_data = data_df[data_df['age'] > 30 & data_df['profession'] == "IT"]
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
The ``value_counts()`` method returns the number of times a value has appear in a dataset column.
```
data_df['columnName'].value_counts()
```

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

To retrieve the row which has the maximum value use:
```
max_row = data_df[data_df["columnName]==data_df["columnName"].max()]
print(max_row)

min_row = data_df[data_df["columnName"] == data_df["columnName"].min()]
```

To retrieve the entire row for Maximum and Minimum values, we use, **`idxmax()`** and **`idxmin()`**


## **Working with correlation**
correlation  checks how features in a dataset associate with each other. A correlation value   near 0 mean have no corerelation(features are independent), positive value +1, strong positive correlation(one inscrease, the other increases) while negative correlation means as once increases the other decreases.
to get the correlation we use: ``corr()`` function
The correlation function only works with numerical data.
```
data_df.corr()
```
Use heatmap to make it more readable:
```
import seaborn as sns
sns.heatmap(data_df.corr(), annot=True, cmap='')
```


### **Plotting counts using sns.countplot**
To plot value_counts for a specific column we can use the ``sns.countplot()`` function to plot this data.
```
data_df = pd.read_csv('file_location')
sns.countplot(x=data_df['columnName'], data=data_df, hue='ColumnName')
```

You can change the  ``x`` argument to get the different orientation for the bars.
``x``: vertical bars
``h`` : horizontal bars


# VISUALIZATION IN DATA ANALYSIS

there are 2 main libaries that are used in visualization:
1. matplotlib.pyplot
2. seaborn

Matplotlib.pyplot
```
import matplotlib.pyplot as plt
plt.pie(values, labels=[list] | label=['apple', 'banana], auto_pct='%1.1f%')
```

auto_pct definition:
The `autopct` parameter in the `plt.pie()` function is used to format the percentage labels on each wedge of the pie chart. Let's break down the string `"%1.1f%%"`:

- `%` : This is the percentage sign literal that will be included after the formatted number.
- `1.1f` : This is a formatting specifier for a floating-point number. It means:
    - `1`: Minimum width of the entire formatted field (including decimal point and digits).
    - `.1`: Precision (number of decimal places).
    - `f`: The 'f' character indicates that the number should be formatted as a floating-point number.
So, `"%1.1f%%"` specifies that the percentage values should be formatted with one digit before the decimal point, one digit after the decimal point, and followed by a percentage sign.



# data preprocessing
1. Extraction
to extract a particular value for a column we can use the str.extract() function which returns a pandas series frame.  the ``.str``  is applied to a pandas column for string objects. 
Example:
```
data_df['columnName'] = data_df.str_extract(r"-(\d+)")
```

as you can see from the above code, we use regex:
``r``: the ``r`` is used to represent raw form/string, it prevents the backslash from being interpreted as an escape character
``\d`` : match any digit
``()`` : defines a capturing group
``+`` : match more than one digit


To view all rows or columns in a dataset use:
by default pandas truncates rows and columns if they're to long. To view all rows or columns one is required to change display setting for pandas. This is acquired by using ``pd.set_option()`` for both max_rows and max_columns.
```
pd.set_option('display.max_rows', None)
pd.dataframe()

pd.set_option('display.max_columns', 100) # this sets columns display to be 100

pd.set_option('display.max_rows', 100) # set rows to be displayed to 100
```

Syntax: ``pd.set_option(display.max_columns/row', value|none)`` : one can combine both for row and columns: ``pd.set_option('display.max_rows`, None, 'display.max_columns', 20)``


By default the max_rows and max_columns is 10..


**Using IPython.display**
The context manager is useful for temporary basis
```
from IPython.display import display
with pd.option_context('display.max_columns', None, 'display.max_rows', 100):
	print(data_df)
```

To reset the  ``pd.set_option()``
```
pd.reset_option('display.max_columns')
pd.reset_option('display.max_rows')
```


Difference between a series and a data-frame:
a series is a single column in a dataset while a data-frame is a combination of  multiple columns(series)


```
# when you have an empty column(continet) in which it's other column('location') has the data it acquires use; 
data_df['continent'].fillna(data_df['location'])
```

### **Rearranging values for month**
