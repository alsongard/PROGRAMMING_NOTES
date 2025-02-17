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