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

3.  Install some packages, for example numpy and pandas: pip3 install numpy pip3 install pandas

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

Baseball Players' Height
------------------------

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
```

    ## [74 74 72 75 75 73]
    ## [1.8796 1.8796 1.8288 1.905  1.905  1.8542]
