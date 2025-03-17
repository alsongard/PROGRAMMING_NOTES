streamlit is a library used for building data   application using python, mostly for data science.

**Installation**
To install streamlit use the following syntax:
```
python3 -m pip install streamlit
```

Getting Started using Streamlit:
```
import streamlit as st
st.write("# YTS MOVIE RATING")
```

## **Streamlit dashboard**

To build a streamlit dashboard identify the following:
1. Define key metrics
2.  Perform exploratory data analysis
3. Build the dashboard
4. deploy the dashboard



*  Defining key metrics


### **get started with the dashboard**
```
import streamlit as st
option_list = ["year", "movie_category"]
option = st.sidebar.selectbox("Select an option", option_list)
```

### implementing real-time data updates
the streamlit dashboard reflect changes in data in real-time. 
to implement real-time updates, one might user a combination of streamlist's ``st.empty()`` placeholder and a loop that periodically checks for new data.

```
placeholder = st.empty()
```

### **streamlit selectbox default value**
To pass a default value for the streamlit selectbox do the following:
```
year_based_answer = ["--select--", 2025, 2024, 2023, 2022]
default_value = year_based_answer.index("--select--")
user_yeare_answer = st.sidebar.selectbox("Enter year to view movie", year_based_answer, index=default_value)

```