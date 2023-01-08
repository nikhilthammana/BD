```python
Q1. How do you load a CSV file into a Pandas DataFrame?

A)->A simple way to store big data sets is to use CSV files (comma separated files).
  ->CSV files contains plain text and is a well know format that can be read by everyone including Pandas.
  ->In our examples we will be using a CSV file called 'data.csv'.

Example:

import pandas as pd
df=pd.read_csv('marketing_campaign_C.csv')
print(df.to_string())
using to_string method we can print entire data frame
print(df)
by using above method If you have a large DataFrame with many rows, Pandas will only return the first 5 rows, and the last 5 rows
```

Q2. How do you check the data type of a column in a Pandas DataFrame?
A)To check the data type in pandas DataFrame we can use the “dtype” attribute. The attribute returns a series with the data   type of each column.And the column names of the DataFrame are represented as the index of the resultant series object and   the corresponding data types are returned as values of the series object.
  If any column has mixed data types are stored then the data type of the entire column is indicated as object dtype.



```python
import pandas as pd

df = pd.DataFrame({'Column1':[4.1, 23.43], 'Col2':['a', 'w'], 'Col3':[1, 8]})

print("DataFrame:")
print(df)

# apply the dtype attribute
result = df.dtypes

print(result)
```

    DataFrame:
       Column1 Col2  Col3
    0     4.10    a     1
    1    23.43    w     8
    Column1    float64
    Col2        object
    Col3         int64
    dtype: object
    


```python
Q3. How do you select rows from a Pandas DataFrame based on a condition?
A)
import pandas as pd

data3={'Name':["Jai","Anuj","Jai","Prince"],
       'Age':[27,24,22,32],
       'Address':['Nagpur','Kanpur','Allahabad','Kannuaj'],
       'Qualification':['MSC','MA','MCA','PHD'],
       'Salary':[1231,2351,3282,4637]
}
df3=pd.DataFrame(data3,columns=['Name', 'Age', 'Address', 'Qualification','Salary'])
print(df3)
print("""""""""""""""""")
rdf3=df3[df3['Salary']>4000]
print(rdf3)

```


```python
Q4. How do you rename columns in a Pandas DataFrame?
import pandas as pd

data3={'Name':["Jai","Anuj","Jai","Prince"],
       'Age':[27,24,22,32],
       'Address':['Nagpur','Kanpur','Allahabad','Kannuaj'],
       'Qualification':['MSC','MA','MCA','PHD'],
       'Salary':[1231,2351,3282,4637]
}
sd=pd.DataFrame(data3)
sd.rename(columns = {'Name':'Names'}, inplace = True)
sd
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Names</th>
      <th>Age</th>
      <th>Address</th>
      <th>Qualification</th>
      <th>Salary</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Jai</td>
      <td>27</td>
      <td>Nagpur</td>
      <td>MSC</td>
      <td>1231</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Anuj</td>
      <td>24</td>
      <td>Kanpur</td>
      <td>MA</td>
      <td>2351</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Jai</td>
      <td>22</td>
      <td>Allahabad</td>
      <td>MCA</td>
      <td>3282</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Prince</td>
      <td>32</td>
      <td>Kannuaj</td>
      <td>PHD</td>
      <td>4637</td>
    </tr>
  </tbody>
</table>
</div>




```python
Q5. How do you drop columns in a Pandas DataFrame?
A)To drop a single column in a pandas dataframe, you can use the del command which is inbuilt in python.
del sd['Salary']
sd
->multiple columns
You can use the drop method of Dataframes to drop single or multiple columns
df.drop(labels=['Salary', 'Age'], axis=1)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Names</th>
      <th>Age</th>
      <th>Address</th>
      <th>Qualification</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Jai</td>
      <td>27</td>
      <td>Nagpur</td>
      <td>MSC</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Anuj</td>
      <td>24</td>
      <td>Kanpur</td>
      <td>MA</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Jai</td>
      <td>22</td>
      <td>Allahabad</td>
      <td>MCA</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Prince</td>
      <td>32</td>
      <td>Kannuaj</td>
      <td>PHD</td>
    </tr>
  </tbody>
</table>
</div>



Q6. How do you find the unique values in a column of a Pandas DataFrame?
A)pandas.DataFrame().unique() method is used when we deal with a single column of a DataFrame and returns all unique elements of a column. The method returns a DataFrame containing the unique elements of a column, along with their corresponding index labels.
sd["Names"].unique()
o/p:array(['Jai', 'Anuj', 'Prince'], dtype=object)

Q7. How do you find the number of missing values in each column of a Pandas DataFrame?
1)Use isnull() function to identify the missing values in the data frame
2)Use sum() functions to get sum of all missing values per column.
3)use sort_values(ascending=False) function to get columns with the missing values in descending order.
4)Divide by len(df) to get % of missing values in each column.
We can use pandas “isnull()” function to find out all the fields which have missing values. This will return True if a field has missing values and false if the field does not have missing values.

Q8. How do you fill missing values in a Pandas DataFrame with a specific value?
The fillna() method replaces the NULL values with a specified value.

The fillna() method returns a new DataFrame object unless the inplace parameter is set to True, in that case the fillna() method does the replacing in the original DataFrame instead.

Example

import pandas as pd

df = pd.read_csv('data.csv')

newdf = df.fillna(222222)


```python
Q9. How do you concatenate two Pandas DataFrames?
import pandas as pd
# First DataFrame
df1 = pd.DataFrame({'id': ['A01', 'A02', 'A03', 'A04'],
                    'Name': ['ABC', 'PQR', 'DEF', 'GHI']})
  
# Second DataFrame
df2 = pd.DataFrame({'id': ['B05', 'B06', 'B07', 'B08'],
                    'Name': ['XYZ', 'TUV', 'MNO', 'JKL']})
  
  
frames = [df1, df2]
  
result = pd.concat(frames)
display(result)
```


```python
Q10. How do you merge two Pandas DataFrames on a specific column?

import pandas as pd

df1 = pd.DataFrame({'Name':['Raju', 'Rani', 'Geeta', 'Sita', 'Sohit'],
                    'Marks':[80, 90, 75, 88, 59]})
  

df2 = pd.DataFrame({'Name':['Raju', 'Divya', 'Geeta', 'Sita'],
                    'Grade':['A', 'A', 'B', 'A'],
                    'Rank':[3, 1, 4, 2 ],
                    'Gender':['Male', 'Female', 'Female', 'Female']})

display(df1)
  

display(df2)

df1.merge(df2[['Name', 'Grade', 'Rank']])
```

Q11. How do you group data in a Pandas DataFrame by a specific column and apply an aggregation function?
Dataframe.aggregate() function is used to apply some aggregation across one or more column. Aggregate using callable, string, dict, or list of string/callables. Most frequently used aggregations are:

sum: Return the sum of the values for the requested axis
min: Return the minimum of the values for the requested axis
max: Return the maximum of the values for the requested axis

import pandas as pd


df = pd.read_csv("nba.csv")

df[:10]
df.aggregate(['sum', 'min'])

#method2

import pandas as pd

df = pd.read_csv("nba.csv")

df.aggregate({"Number":['sum', 'min'],
			"Age":['max', 'min'],
			"Weight":['min', 'sum'],
			"Salary":['sum']})


Q12. How do you pivot a Pandas DataFrame?
The pivot() function is used to reshaped a given DataFrame organized by given index / column values. This function does not support data aggregation, multiple values will result in a MultiIndex in the columns.


```python
df = pd.DataFrame({'A': ['John', 'Boby', 'Mina'],
      'B': ['Masters', 'Graduate', 'Graduate'],
      'C': [27, 23, 21]})
  
df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>John</td>
      <td>Masters</td>
      <td>27</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Boby</td>
      <td>Graduate</td>
      <td>23</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Mina</td>
      <td>Graduate</td>
      <td>21</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.pivot('A', 'B', 'C')
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>B</th>
      <th>Graduate</th>
      <th>Masters</th>
    </tr>
    <tr>
      <th>A</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Boby</th>
      <td>23.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>John</th>
      <td>NaN</td>
      <td>27.0</td>
    </tr>
    <tr>
      <th>Mina</th>
      <td>21.0</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>




Q13. How do you change the data type of a column in a Pandas DataFrame?
DataFrame.astype() method is used to cast pandas object to a specified dtype. This function also provides the capability to convert any suitable existing column to a categorical type.
#importing pandas as pd
import pandas as pd
df = pd.DataFrame({
	'A': [1, 2, 3, 4, 5],
	'B': ['a', 'b', 'c', 'd', 'e'],
	'C': [1.1, '1.0', '1.3', 2, 5]})

df = df.astype(str)
print(df.dtypes)


Q14. How do you sort a Pandas DataFrame by a specific column?
To sort the DataFrame based on the values in a single column, you'll use . sort_values() . By default, this will return a new DataFrame sorted in ascending order. It does not modify the original DataFrame.
new=df.sort_values(by=['Column_name'], ascending=True)
new

Q15. How do you create a copy of a Pandas DataFrame?
The copy() method returns a copy of the DataFrame. By default, the copy is a "deep copy" meaning that any changes made in the original DataFrame will NOT be reflected in the copy.
ea=df.copy()
ea


```python
Q16. How do you filter rows of a Pandas DataFrame by multiple conditions?
A)# import module
import pandas as pd

# assign data
dataFrame = pd.DataFrame({'Name': [' RACHEL ', ' MONICA ', ' PHOEBE ',
              ' ROSS ', 'CHANDLER', ' JOEY '],
             'Age': [30, 35, 37, 33, 34, 30],
            'Salary': [100000, 93000, 88000, 120000, 94000, 95000],
           'JOB': ['DESIGNER', 'CHEF', 'MASUS', 'PALENTOLOGY','IT', 'ARTIST']})
# filter dataframe
display(dataFrame.loc[(dataFrame['Salary']>=100000) & (dataFrame['Age']< 40) & (dataFrame['JOB'].str.startswith('D')),
['Name','JOB']])

```

Q17. How do you calculate the mean of a column in a Pandas DataFrame?
Pandas dataframe.mean() function return the mean of the values for the requested axis. If the method is applied on a pandas series object, then the method returns a scalar value which is the mean value of all the observations in the dataframe. If the method is applied on a pandas dataframe object, then the method returns a pandas series object which contains the mean of the values over the specified axis.
#Even if we do not specify axis = 0,
#the method will return the mean over
#the index axis by default
df = pd.DataFrame({"A":[12, 4, 5, 44, 1],
                   "B":[5, 2, 54, 3, 2], 
                   "C":[20, 16, 7, 3, 8],
                   "D":[14, 3, 17, 2, 6]})
df.mean(axis = 0)



```python
Q18. How do you calculate the standard deviation of a column in a Pandas DataFrame?
import pandas as pd
import numpy as np
 
#Create a DataFrame
d = {
    'Name':['Alisa','Bobby','Cathrine','Madonna','Rocky','Sebastian','Jaqluine',
   'Rahul','David','Andrew','Ajay','Teresa'],
   'Score1':[62,47,55,74,31,77,85,63,42,32,71,57],
   'Score2':[89,87,67,55,47,72,76,79,44,92,99,69],
   'Score3':[56,86,77,45,73,62,74,89,71,67,97,68]}

df = pd.DataFrame(d)
answer= df.std()
print("The standard deviations of the 3 columns are:")
print (answer)
```

Q19. How do you calculate the correlation between two columns in a Pandas DataFrame?
Correlation is used to summarize the strength and direction of the linear association between two quantitative variables. It is denoted by r and values between -1 and +1. A positive value for r indicates a positive association, and a negative value for r indicates a negative association.

By using corr() function we can get the correlation between two columns in the dataframe.
syntax:
dataframe[‘first_column’].corr(dataframe[‘second_column’])

Q20. How do you select specific columns in a DataFrame using their labels?
A)Select Rows by Name in Pandas DataFrame using loc 
The .loc[] function selects the data by labels of rows or columns. It can select a subset of rows and columns. There are many ways to use this function.

df = pd.DataFrame(employees,
                columns =['Name', 'Age',
                'City', 'Salary'])
 
#Set 'Name' column as index
#on a Dataframe
df.set_index("Name", inplace = True)
 
#Using the operator .loc[]
#to select single row
result = df.loc["Stuti"]
 


```python
Q21. How do you select specific rows in a DataFrame using their indexes?
If you’d like to select rows based on integer indexing, you can use the .iloc function.

If you’d like to select rows based on label indexing, you can use the .loc function.
#select the 3rd, 4th, and 5th rows of the DataFrame
df.iloc[[2, 3, 4]]
```


```python
Q22. How do you sort a DataFrame by a specific column?
new=df.sort_values(by=['Column_name'], ascending=True)
```


Q23. How do you create a new column in a DataFrame based on the values of another column?
You can add/append a new column to the DataFrame based on the values of another column using df.assign(), df.apply(), and, np.where() functions and return a new Dataframe after adding a new column.


```python
Q24. How do you remove duplicates from a DataFrame?
import pandas as pd
  
data = {
    "A": ["TeamA", "TeamB", "TeamB", "TeamC", "TeamA"],
    "B": [50, 40, 40, 30, 50],
    "C": [True, False, False, False, True]
}
  
df = pd.DataFrame(data)
  
display(df.drop_duplicates())

#removing all duplcates
# length before adding row
length1 = len(data)

# manually inserting duplicate of a row of row 440
data.loc[1001] = [data["First Name"][440],
				data["Gender"][440],
				data["Start Date"][440],
				data["Last Login Time"][440],
				data["Salary"][440],
				data["Bonus %"][440],
				data["Senior Management"][440],
				data["Team"][440]]

# length after adding row
length2 = len(data)

# sorting by first name
data.sort_values("First Name", inplace=True)

# dropping duplicate values
data.drop_duplicates(keep=False, inplace=True)

# length after removing duplicates
length3 = len(data)

# printing all data frame lengths
print(length1, length2, length3)

```

Q25. What is the difference between .loc and .iloc in Pandas?
The Difference Between .iloc and .loc
The examples above illustrate the subtle difference between .iloc an .loc:

.iloc selects rows based on an integer index. So, if you want to select the 5th row in a DataFrame, you would use df.iloc[[4]] since the first row is at index 0, the second row is at index 1, and so on.
.loc selects rows based on a labeled index. So, if you want to select the row with an index label of 5, you would directly use df.loc[[5]].


```python

```
