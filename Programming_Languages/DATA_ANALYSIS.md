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


