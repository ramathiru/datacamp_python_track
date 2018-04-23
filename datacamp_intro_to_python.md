DataCamp Intro to Python
================
Mark Blackmore
April 22, 2018

Install Python
--------------

1.  Download the x86 64-bit executable version from <https://www.python.org/>
2.  Check add to path box. Allow long path names option.
3.  Check istallation at the Start menu.

Installing Python Packages
--------------------------

1.  Get Package Import Manager "pip": <http://pip.readthedocs.io/en/stable/installing/#installing-with-get-pip-py>

2.  Upgrade pip with the following call in a terminal window: python -m pip install -U pip

3.  Install some packages, for example numpy, pandas matplotlib. From a terminal window: pip3 install numpy pip3 install pandas pip3 install matplotlib

First NumPy Array
-----------------

``` python
# Create list baseball
baseball = [180, 215, 210, 210, 188, 176, 209, 200]

# Import the numpy package as np
import numpy as np

# Create a numpy array from baseball: np_baseball
np_baseball = np.array(baseball)

# Print out type of np_baseball
print(type(np_baseball))
```

    ## <class 'numpy.ndarray'>

1D Arrays
---------

``` python

# Baseball player's heights
height = list([74, 74, 72, 75, 75, 73])

# Import numpy
import numpy as np

# Create a numpy array from height: np_height
np_height = np.array(height)

# Print out np_height
print(np_height)

# Convert np_height to m: np_height_m
np_height_m = np_height * 0.0254

# Print np_height_m
print(np_height_m)

weight = list([170, 220, 156, 190, 202, 221])

# Calculate the BMI: bmi
np_height_m = np.array(height) * 0.0254
np_weight_kg = np.array(weight) * 0.453592
bmi = np_weight_kg / np_height_m ** 2

# Create the light array
light = bmi < 21

# Print out light
print(light)

# Print out BMIs of all baseball players whose BMI is below 21
print(bmi[light])
```

    ## [74 74 72 75 75 73]
    ## [1.8796 1.8796 1.8288 1.905  1.905  1.8542]
    ## [False False False False False False]
    ## []

2D Arrays
---------

``` python

# Create baseball, a list of lists
baseball = [[180, 78.4],
            [215, 102.7],
            [210, 98.5],
            [188, 75.2]]

# Import numpy
import numpy as np

# Create a 2D numpy array from baseball: np_baseball
np_baseball = np.array(baseball)

# Print out the type of np_baseball
print(type(np_baseball))

# Print out the shape of np_baseball
print(np_baseball.shape)
```

    ## <class 'numpy.ndarray'>
    ## (4, 2)

Basic Statistics
----------------

``` python

# Import numpy
import numpy as np

# Generate data
height = np.round(np.random.normal(1.75, 0.20, 5000),2)
weight = np.round(np.random.normal(60.32, 15, 5000),2)
np_city = np.column_stack((height, weight))

# Print mean height (first column)
avg = np.mean(np_city[:,0])
print("Average: " + str(avg))

# Print median height
med = np.median(np_city[:,0])
print("Median: " + str(med))

# Print out the standard deviation on height
stddev = np.std(np_city[:,0])
print("Standard Deviation: " + str(stddev))

# Print out correlation between first and second column
corr = np.corrcoef(np_city[:,0], np_city[:,1])
print("Correlation: " + str(corr))
```

    ## Average: 1.749118
    ## Median: 1.75
    ## Standard Deviation: 0.19519703398361357
    ## Correlation: [[1.         0.01752332]
    ##  [0.01752332 1.        ]]

Basic plots with Matplotlib
---------------------------

``` python

import matplotlib.pyplot as plt
year = [1950, 1970, 1990, 2010]
pop = [2.519, 3.692, 5.263, 6.972]
plt.plot(year, pop)
plt.show()
```
