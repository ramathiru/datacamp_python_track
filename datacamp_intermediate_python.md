DataCamp Intermediate Python
================
Mark Blackmore
April 23, 2018

Source for setup script: <https://stackoverflow.com/questions/36437028/rstudio-with-python-matplotlib-graph>

Basic Plots with Matplotlib
---------------------------

``` python
# Import matplotlib.pyplot
import matplotlib.pyplot as plt
year = [1950, 1970, 1990, 2010]
pop = [2.519, 3.692, 5.263, 6.972]
# Line plot
plt.plot(year, pop)
plt.xlabel('Year')
plt.ylabel('Population')
plt.show()
```

![](datacamp_intermediate_python_files/figure-markdown_github-ascii_identifiers/unnamed-chunk-1-1.png)

``` python
plt.clf()
#Scatter plot
plt.scatter(year, pop)
plt.xlabel('Year')
plt.ylabel('Population')
plt.show()
```

![](datacamp_intermediate_python_files/figure-markdown_github-ascii_identifiers/unnamed-chunk-1-2.png)

``` python
plt.clf()
# Import numpy
import numpy as np
# Generate data
height = np.round(np.random.normal(1.75, 0.20, 5000),2)
weight = np.round(np.random.normal(60.32, 15, 5000),2)
# Histogram
plt.hist(height, bins = 5)
plt.xlabel('Histogram of Heights, 5 Bins')
plt.show()
```

![](datacamp_intermediate_python_files/figure-markdown_github-ascii_identifiers/unnamed-chunk-1-3.png)

``` python
plt.clf()
```

Dictionaries
------------

``` python
# Definition of countries and capital
countries = ['spain', 'france', 'germany', 'norway']
capitals = ['madrid', 'paris', 'berlin', 'oslo']
# Get index of 'germany': ind_ger
ind_ger = countries.index('germany')
# Use ind_ger to print out capital of Germany
print(capitals[ind_ger])
# From string in countries and capitals, create dictionary europe
```

    ## berlin

``` python
europe = {
    'spain':'madrid',
    'france': 'paris',
    'germany':'berlin',
    'norway':'oslo'
    }
# Print europe
print(europe)
# Print out the keys in europe
```

    ## {'spain': 'madrid', 'france': 'paris', 'germany': 'berlin', 'norway': 'oslo'}

``` python
print(europe.keys())
# Print out value that belongs to key 'norway'
```

    ## dict_keys(['spain', 'france', 'germany', 'norway'])

``` python
print(europe['norway'])
# Add italy to europe
```

    ## oslo

``` python
europe['italy'] = 'rome'
# Print out italy in europe
print('italy' in europe)
# Add poland to europe
```

    ## True

``` python
europe['poland'] = 'warsaw'
# Print europe
print(europe)
# New Definition of dictionary
```

    ## {'spain': 'madrid', 'france': 'paris', 'germany': 'berlin', 'norway': 'oslo', 'italy': 'rome', 'poland': 'warsaw'}

``` python
europe = {'spain':'madrid', 'france':'paris', 'germany':'bonn',
          'norway':'oslo', 'italy':'rome', 'poland':'warsaw',
          'australia':'vienna' }
# Update capital of germany
europe['germany'] = 'berlin'
# Remove australia
del(europe['australia'])
# Print europe
print(europe)
```

    ## {'spain': 'madrid', 'france': 'paris', 'germany': 'berlin', 'norway': 'oslo', 'italy': 'rome', 'poland': 'warsaw'}

More Dictionaries
-----------------

``` python
# Dictionary of dictionaries
europe = { 'spain': { 'capital':'madrid', 'population':46.77 },
           'france': { 'capital':'paris', 'population':66.03 },
           'germany': { 'capital':'berlin', 'population':80.62 },
           'norway': { 'capital':'oslo', 'population':5.084 } }
# Print out the capital of France
print(europe['france']['capital'])
# Create sub-dictionary data
```

    ## paris

``` python
data = { 'capital':'rome', 'population':59.83 }
# Add data to europe under key 'italy'
europe['italy'] = data
# Print europe
print(europe)
```

    ## {'spain': {'capital': 'madrid', 'population': 46.77}, 'france': {'capital': 'paris', 'population': 66.03}, 'germany': {'capital': 'berlin', 'population': 80.62}, 'norway': {'capital': 'oslo', 'population': 5.084}, 'italy': {'capital': 'rome', 'population': 59.83}}

Dictionaries to DataFrames
--------------------------

``` python
# Pre-defined lists
names = ['United States', 'Australia', 'Japan', 'India', 'Russia', 'Morocco', 'Egypt']
dr =  [True, False, False, False, True, True, True]
cpc = [809, 731, 588, 18, 200, 70, 45]
# Import pandas as pd
import pandas as pd
# Create dictionary my_dict with three key:value pairs: my_dict
my_dict = { 'country':names, 'drives_right':dr, 'cars_per_cap':cpc }
# Build a DataFrame cars from my_dict: cars
cars = pd.DataFrame(my_dict)
# Print cars
print(cars)
# Definition of row_labels
```

    ##    cars_per_cap        country  drives_right
    ## 0           809  United States          True
    ## 1           731      Australia         False
    ## 2           588          Japan         False
    ## 3            18          India         False
    ## 4           200         Russia          True
    ## 5            70        Morocco          True
    ## 6            45          Egypt          True

``` python
row_labels = ['US', 'AUS', 'JAP', 'IN', 'RU', 'MOR', 'EG']
# Specify row labels of cars
cars.index = row_labels
# Print cars again
print(cars)
```

    ##      cars_per_cap        country  drives_right
    ## US            809  United States          True
    ## AUS           731      Australia         False
    ## JAP           588          Japan         False
    ## IN             18          India         False
    ## RU            200         Russia          True
    ## MOR            70        Morocco          True
    ## EG             45          Egypt          True

CSV to DataFrame
================

``` python
# Import pandas as pd
import pandas as pd
# Import the cars.csv data: cars
cars  = pd.read_csv("https://assets.datacamp.com/production/course_799/datasets/cars.csv")
print(cars)
# Fix import by including index_col
```

    ##   Unnamed: 0  cars_per_cap        country  drives_right
    ## 0         US           809  United States          True
    ## 1        AUS           731      Australia         False
    ## 2        JAP           588          Japan         False
    ## 3         IN            18          India         False
    ## 4         RU           200         Russia          True
    ## 5        MOR            70        Morocco          True
    ## 6         EG            45          Egypt          True

``` python
cars = pd.read_csv("https://assets.datacamp.com/production/course_799/datasets/cars.csv", index_col = 0)
# Print out cars
print(cars)
```

    ##      cars_per_cap        country  drives_right
    ## US            809  United States          True
    ## AUS           731      Australia         False
    ## JAP           588          Japan         False
    ## IN             18          India         False
    ## RU            200         Russia          True
    ## MOR            70        Morocco          True
    ## EG             45          Egypt          True

Subsetting DataFrames
---------------------

``` python
# Import pandas as pd
import pandas as pd
# Import the cars.csv data: cars
cars  = pd.read_csv("https://assets.datacamp.com/production/course_799/datasets/cars.csv", index_col = 0)
# Print out country column as Pandas Series
print(cars['country'])
# Print out country column as Pandas DataFrame
```

    ## US     United States
    ## AUS        Australia
    ## JAP            Japan
    ## IN             India
    ## RU            Russia
    ## MOR          Morocco
    ## EG             Egypt
    ## Name: country, dtype: object

``` python
print(cars[['country']])
# Print out DataFrame with country and drives_right columns
```

    ##            country
    ## US   United States
    ## AUS      Australia
    ## JAP          Japan
    ## IN           India
    ## RU          Russia
    ## MOR        Morocco
    ## EG           Egypt

``` python
print(cars[['country', 'drives_right']])
# Print out first 3 observations
```

    ##            country  drives_right
    ## US   United States          True
    ## AUS      Australia         False
    ## JAP          Japan         False
    ## IN           India         False
    ## RU          Russia          True
    ## MOR        Morocco          True
    ## EG           Egypt          True

``` python
print(cars[0:3])
# Print out fourth, fifth and sixth observation
```

    ##      cars_per_cap        country  drives_right
    ## US            809  United States          True
    ## AUS           731      Australia         False
    ## JAP           588          Japan         False

``` python
print(cars[3:6])
# Print out observation for Japan
```

    ##      cars_per_cap  country  drives_right
    ## IN             18    India         False
    ## RU            200   Russia          True
    ## MOR            70  Morocco          True

``` python
print(cars.loc['JAP'])
# Print out observations for Australia and Egypt
```

    ## cars_per_cap      588
    ## country         Japan
    ## drives_right    False
    ## Name: JAP, dtype: object

``` python
print(cars.loc[['AUS', 'EG']])
# Print out drives_right value of Morocco
```

    ##      cars_per_cap    country  drives_right
    ## AUS           731  Australia         False
    ## EG             45      Egypt          True

``` python
print(cars.loc['MOR', 'drives_right'])
# Print sub-DataFrame
```

    ## True

``` python
print(cars.loc[['RU', 'MOR'], ['country', 'drives_right']])
# Print out drives_right column as Series
```

    ##      country  drives_right
    ## RU    Russia          True
    ## MOR  Morocco          True

``` python
print(cars.loc[:,'drives_right'])
# Print out drives_right column as DataFrame
```

    ## US      True
    ## AUS    False
    ## JAP    False
    ## IN     False
    ## RU      True
    ## MOR     True
    ## EG      True
    ## Name: drives_right, dtype: bool

``` python
print(cars.loc[:,['drives_right']])
# Print out cars_per_cap and drives_right as DataFrame
```

    ##      drives_right
    ## US           True
    ## AUS         False
    ## JAP         False
    ## IN          False
    ## RU           True
    ## MOR          True
    ## EG           True

``` python
print(cars.loc[:,['cars_per_cap','drives_right' ]])
```

    ##      cars_per_cap  drives_right
    ## US            809          True
    ## AUS           731         False
    ## JAP           588         False
    ## IN             18         False
    ## RU            200          True
    ## MOR            70          True
    ## EG             45          True

Comparison Operators
--------------------

``` python
# Comparison of booleans
print(True == False)
# Comparison of integers
```

    ## False

``` python
print(-5 *15 != 75)
# Comparison of strings
```

    ## True

``` python
print("pyscript" == "PyScript")
# Compare a boolean with an integer
```

    ## False

``` python
print(True == 1)
# Comparison of integers
```

    ## True

``` python
x = -3 * 6
print(x >= -10)
# Comparison of strings
```

    ## False

``` python
y = "test"
print('test' <= y)
# Comparison of booleans
```

    ## True

``` python
print(True > False)
# Create arrays
```

    ## True

``` python
import numpy as np
my_house = np.array([18.0, 20.0, 10.75, 9.50])
your_house = np.array([14.0, 24.0, 14.25, 9.0])
# my_house greater than or equal to 18
print(my_house >= 18 )
# my_house less than your_house
```

    ## [ True  True False False]

``` python
print(my_house < your_house)
```

    ## [False  True  True False]

Boolean Operators
-----------------

``` python
# Define variables
my_kitchen = 18.0
your_kitchen = 14.0
# my_kitchen bigger than 10 and smaller than 18?
print(my_kitchen > 10 and my_kitchen < 18)
# my_kitchen smaller than 14 or bigger than 17?
```

    ## False

``` python
print(my_kitchen < 14 or my_kitchen > 17 )
# Double my_kitchen smaller than triple your_kitchen?
```

    ## True

``` python
print(2 * my_kitchen < 3 * your_kitchen)
# Create arrays
```

    ## True

``` python
import numpy as np
my_house = np.array([18.0, 20.0, 10.75, 9.50])
your_house = np.array([14.0, 24.0, 14.25, 9.0])
# my_house greater than 18.5 or smaller than 10
print(np.logical_or(my_house > 18.5, my_house < 10))
# Both my_house and your_house smaller than 11
```

    ## [False  True False  True]

``` python
print(np.logical_and(my_house < 11, your_house < 11))# Create arrays
```

    ## [False False False  True]

``` python
import numpy as np
my_house = np.array([18.0, 20.0, 10.75, 9.50])
your_house = np.array([14.0, 24.0, 14.25, 9.0])
# my_house greater than 18.5 or smaller than 10
print(np.logical_or(my_house > 18.5, my_house < 10))
# Both my_house and your_house smaller than 11
```

    ## [False  True False  True]

``` python
print(np.logical_and(my_house < 11, your_house < 11))
```

    ## [False False False  True]

Conditional Statements
----------------------

``` python
# Define variables
room = "kit"
area = 14.0
# if statement for room
if room == "kit" :
    print("looking around in the kitchen.")
# if statement for area
```

    ## looking around in the kitchen.

``` python
if area > 15:
    print("big place!")
    
# if-else construct for room
if room == "kit" :
    print("looking around in the kitchen.")
else :
    print("looking around elsewhere.")
# if-else construct for area
```

    ## looking around in the kitchen.

``` python
if area > 15 :
    print("big place!")
else :
    print("pretty small.")
# Define variables
```

    ## pretty small.

``` python
room = "bed"
area = 14.0
# if-elif-else construct for room
if room == "kit" :
    print("looking around in the kitchen.")
elif room == "bed":
    print("looking around in the bedroom.")
else :
    print("looking around elsewhere.")
# if-elif-else construct for area
```

    ## looking around in the bedroom.

``` python
if area > 15 :
    print("big place!")
elif area > 10 :
    print("medium size, nice!")
else :
    print("pretty small.")
```

    ## medium size, nice!
