# Dictionaries

world = {"India":2.2, ...}

world["india"]

world.keys()

world.values()

keys are unique, if more then latter wins

Keys have to be immutable objects: int float bool str **not list as it is error**
Such that the contents of the objects can not be changed after they are created

### Creating new pair

world["Afganistan"] = .27

'Afganistan' in world => True

### Updating

world["Afganistan"] = .28  => Because python knows there is only one Afganistan

### Deleting:

del(world["Afganistan"])

## Dictionariception

```
# Dictionary of dictionaries
europe = { 'spain': { 'capital':'madrid', 'population':46.77 },
           'france': { 'capital':'paris', 'population':66.03 },
           'germany': { 'capital':'berlin', 'population':80.62 },
           'norway': { 'capital':'oslo', 'population':5.084 } }


# Print out the capital of France
print(europe['france']['capital'])

# Create sub-dictionary data
data = {'capital': 'rome', 'population' : 59.83}

# Add data to europe under key 'italy'
europe['italy'] = data

# Print europe
print(europe)
```

# Pandas

Tabular data 
for e.g Country, Capital, Population(in M), area

We require a retangular data type:
> 2Dnumpy but one data type

So **Pandas**
1. High level manipulation tool
2. Wes Mckinney
3. Built on numpy
4. DataFrame : Tabular data is called

Pandas is an open source library, providing high-performance, easy-to-use data structures and data analysis tools for Python. Sounds promising!

The DataFrame is one of Pandas' most important data structures. It's basically a way to store tabular data where you can label the rows and the columns. One way to build a DataFrame is from a dictionary.

## DataFrames:

> rows = observations
> columns = variables

Each row has unique row label
Each column has different column label

## dataFrames from dictionary

```
import pandas as pd

Use pd.DataFrame() to turn your dict into a DataFrame

>> brics = pd.DataFrame(dict)

brics indexes are in the order 0f 0,1,2,3,4,5...

To assign manually

brics.index = ["BR", "RU", "IN"...]  => Correct lables

# Definition of row_labels
row_labels = ['US', 'AUS', 'JAP', 'IN', 'RU', 'MOR', 'EG']

# Specify row labels of cars
cars.index = row_labels

# Print cars again
print(cars)
```

Example:Three lists are defined in the script:

1. names, containing the country names for which data is available.
2. dr, a list with booleans that tells whether people drive left or right in the corresponding country.
3. cpc, the number of motor vehicles per 1000 people in the corresponding country.

```
# Pre-defined lists
names = ['United States', 'Australia', 'Japan', 'India', 'Russia', 'Morocco', 'Egypt']
dr =  [True, False, False, False, True, True, True]
cpc = [809, 731, 588, 18, 200, 70, 45]

# Import pandas as pd
import pandas as pd

# Create dictionary my_dict with three key:value pairs: my_dict
my_dict = {'country': names, 'drives_right' :dr, 'cars_per_cap': cpc}
# Build a DataFrame cars from my_dict: cars
cars = pd.DataFrame(my_dict)

# Print cars
print(cars)
```

## Data frames from CSV

>brics = pd.read_csv("path/to/brics.csv")

>brics = pd.read_csv("path/to/brics.csv", index_col = 0)

Example:
```
# Import pandas as pd
import pandas as pd

# Fix import by including index_col
cars = pd.read_csv('cars.csv', index_col = 0)

# Print out cars
print(cars)
```

## Index and select data

> brics['country']

> type(brics['country'])  => pandas.core.series.**Series** : Series is as 1D labelled array

### Column access []
If we wnats to keep the data in data frame we have to use the double square backets

> brics[['country']]  => pandas.core.frame.DataFrame

> brics[['country', 'capital']]

```
# Import cars data
import pandas as pd
cars = pd.read_csv('cars.csv', index_col = 0)

# Print out country column as Pandas Series
print(cars['country'])

# Print out country column as Pandas DataFrame
print(cars[['country']])

# Print out DataFrame with country and drives_right columns
print(cars[['country', 'drives_right']])
```

## Row access
> slicing: brics[1,4]

```
# Import cars data
import pandas as pd
cars = pd.read_csv('cars.csv', index_col = 0)

# Print out first 3 observations
print(cars[0:3])

# Print out fourth, fifth and sixth observation
print(cars[3:6])
```

## pandas loc and iloc

loc = label based

iloc = integer position based

> bric.loc["IN"]    Contains extra data

> bric.loc[["IN"]]   =======    bric.loc[[1]]

> bric.loc[['RU', 'IN']]  =======  bric.iloc[[1,2]]

> bric.loc[["RU", "IN", "CH"], ["country", "capital"]]  ==== brics.iloc[[1,2,3], [0,1]]

> bric.loc[:, ["country", "capital"]]    ======  brics.iloc(: , [1,2,3]]]

```
# Import cars data
import pandas as pd
cars = pd.read_csv('cars.csv', index_col = 0)

# Print out observation for Japan
print(cars.loc['Japan'])

# Print out observations for Australia and Egypt
print(cars.loc['Australia', 'Egypt'])
```

```
# Import cars data
import pandas as pd
cars = pd.read_csv('cars.csv', index_col = 0)

# Print out drives_right value of Morocco
print(cars.loc[['MOR'],['drives_right']])

# Print sub-DataFrame
print(cars.loc[['RU', 'MOR'],['country', 'drives_right']])
```

**Select Only columns example:**
```
# Import cars data
import pandas as pd
cars = pd.read_csv('cars.csv', index_col = 0)

# Print out drives_right column as Series
print(cars.loc[:,'drives_right'])

# Print out drives_right column as DataFrame
print(cars.loc[:,['drives_right']])

# Print out cars_per_cap and drives_right as DataFrame
print(cars.loc[:, ['cars_per_cap', 'drives_right']])

```

# Comparison operators

> Notice that not has a higher priority than and and or, it is executed first.

```
# Comparison of booleans
True == False

# Comparison of integers
-5*15 != 75

# Comparison of strings
"pyscript" == "PyScript"

# Compare a boolean with an integer
True == 1
```

```
# Comparison of integers
x = -3 * 6


# Comparison of strings
y = "test"


# Comparison of booleans
print(x>= -10)
print("test" <= y)
print(True > False)
```

```
# Create arrays
import numpy as np
my_house = np.array([18.0, 20.0, 10.75, 9.50])
your_house = np.array([14.0, 24.0, 14.25, 9.0])

# my_house greater than or equal to 18
print(my_house >= 18)

# my_house less than your_house
print(my_house < your_house)
```

### Important

> np.logical_and(), np.logical_or(), np.logical_not()

```
# Create arrays
import numpy as np
my_house = np.array([18.0, 20.0, 10.75, 9.50])
your_house = np.array([14.0, 24.0, 14.25, 9.0])

# my_house greater than 18.5 or smaller than 10
print(np.logical_or(my_house > 18.5 , my_house< 10))
# Both my_house and your_house smaller than 11
print(np.logical_and(my_house < 11 , your_house< 11))

```

### Filtering pandas Data Frames

We need a pandas series for this, not panda data frames
1. Get Column as brics['area']  ===  brics.loc[:, 'area']  === brics.iloc[:,2]

2. Compare is_huge = brics['area'] > 8

3. Subset Data Frames: brics[is_huge]

**One Liner**

> brics[brics['area']>8]

**As pandas built on the numpy**

> brics[np.logical_and(brics["area"]>8, brics["area"]< 18)]

```
# Import cars data
import pandas as pd
cars = pd.read_csv('cars.csv', index_col = 0)

# Create car_maniac: observations that have a cars_per_cap over 500
cpc = cars['cars_per_cap']
many_cars = cpc> 500 
car_maniac = cars[many_cars]
# Print car_maniac
print(car_maniac)
```

```
# Import cars data
import pandas as pd
cars = pd.read_csv('cars.csv', index_col = 0)

# Import numpy, you'll need this
import numpy as np

# Create medium: observations with cars_per_cap between 100 and 500

cpc = cars['cars_per_cap']
medium = cars[np.logical_and(cpc> 100, cpc< 500)]

# Print medium
print(medium)
```

# Loops

### While Loop

```
# Initialize offset
offset = -6

# Code the while loop
while offset != 0 :
    print("correcting...")
    if offset > 0:
        offset-= 1
    else:
        offset+= 1
    print(offset)
```

### For Loop

> same for **Strings, List**

```
fam = [1.73, 1.68, 1.71, 1.89]
for index, height in enumerate(fam) :
    print("person " + str(index) + ": " + str(height))
```

```
# house list of lists
house = [["hallway", 11.25], 
         ["kitchen", 18.0], 
         ["living room", 20.0], 
         ["bedroom", 10.75], 
         ["bathroom", 9.50]]
         
# Build a for loop from scratch
for each in house:
    print("the " + each[0] + " is " + str(each[1]) + " sqm")
```

>For Dictionaries : Required a Method


```
# Definition of dictionary
europe = {'spain':'madrid', 'france':'paris', 'germany':'berlin',
          'norway':'oslo', 'italy':'rome', 'poland':'warsaw', 'austria':'vienna' }
          
# Iterate over europe
for key, value in europe.items():
    print('the capital of',key,'is',value)
```

> For numpy: Required a Function

```
for val in np.nditer(np2D):
    print(val)
```

> For loops with DataFrame

Iterate over the columns , by default.
To iterate over rows:

```
# Import cars data
import pandas as pd
cars = pd.read_csv('cars.csv', index_col = 0)

# Iterate over rows of cars
for lab, row in cars.iterrows():
    print(lab)
    print(row)
```

The row data that's generated by iterrows() on every run is a Pandas Series. This format is not very convenient to print out. Luckily, you can easily select variables from the Pandas Series using square brackets:

```
# Import cars data
import pandas as pd
cars = pd.read_csv('cars.csv', index_col = 0)

# Adapt for loop
for lab, row in cars.iterrows() :
    print(lab + ':', row["cars_per_cap"])
```

## Add column(1):

```
# Import cars data
import pandas as pd
cars = pd.read_csv('cars.csv', index_col = 0)

# Code for loop that adds COUNTRY column
for lab, row in cars.iterrows():
    cars.loc[lab,"COUNTRY"] = str.upper(row["country"])


# Print cars
print(cars)
```

## Add column(2):

Using iterrows() to iterate over every observation of a Pandas DataFrame is easy to understand, but not very efficient. On every iteration, you're creating a new Pandas Series.
If you want to add a column to a DataFrame by calling a function on another column, the iterrows() method in combination with a for loop is not the preferred way to go. Instead, you'll want to use apply().

```
# Import cars data
import pandas as pd
cars = pd.read_csv('cars.csv', index_col = 0)

# Use .apply(str.upper)
# for lab, row in cars.iterrows() :
#     cars.loc[lab, "COUNTRY"] = row["country"].upper()
cars["COUNTRY"] = cars['country'].apply(str.upper)
```
