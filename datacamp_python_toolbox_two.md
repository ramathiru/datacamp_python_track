DataCamp Python Data Science Toolbox 2
================
Mark Blackmore
April 26, 2018

-   [Start Here](#start-here)
-   [Iterators] (#iterators)

Start Here
----------

``` python
print('Hello new course')
```

    ## Hello new course

Iterators
----------

``` python
# Create a list of strings: flash
flash = ['jay garrick', 'barry allen', 'wally west', 'bart allen']

# Print each list item in flash using a for loop
for values in flash:
    print (values)

# Create an iterator for flash: superhero
superhero = iter(flash)

# Print each item from the iterator
print(next(superhero))
print(next(superhero))
print(next(superhero))
print(next(superhero))
```

    jay garrick
    barry allen
    wally west
    bart allen
    jay garrick
    barry allen
    wally west
    bart allen

``` python
# Create an iterator for range(3): small_value
small_value = iter(range(3))

# Print the values in small_value
print(next(small_value))
print(next(small_value))
print(next(small_value))

# Loop over range(3) and print the values
for num in range(3):
    print(num)

# Create an iterator for range(10 ** 100): googol
googol = iter(range(10 ** 100))

# Print the first 5 values from googol
print(next(googol))
print(next(googol))
print(next(googol))
print(next(googol))
print(next(googol))
```
    0
    1
    2
    0
    1
    2
    0
    1
    2
    3
    4

``` python
