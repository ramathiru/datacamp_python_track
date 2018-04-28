DataCamp Python Data Science Toolbox 1
================
Mark Blackmore
April 26, 2018

-   [Writing Functions](#writing-functions)
    -   [Twitter DataFrame Analysis Function](#twitter-dataframe-analysis-function)
-   [Scope and User-Defined Functions](#scope-and-user-defined-functions)
    -   [Default and Flexible Arguments](#default-and-flexible-arguments)

Writing Functions
-----------------

``` python
# Strings in Python
company = 'DataCamp'
object1 = "data" + "analysis" + "visualization"
object2 = 1 * 3
object3 = "1" * 3
print(object1, object2, object3)
# Variable types
```

    ## dataanalysisvisualization 3 111

``` python
x = 4.89
y1 = str(x)
y2 = print(x)
```

    ## 4.89

``` python
print(type(x), type(y1), type(y2))
# Define the function shout
```

    ## <class 'float'> <class 'str'> <class 'NoneType'>

``` python
def shout():
    """Print a string with three exclamation marks"""
    # Concatenate the strings: shout_word
    shout_word = 'congratulations' + '!!!'
    # Print shout_word
    print(shout_word)
# Call shout
shout()
# Define shout with the parameter, word
```

    ## congratulations!!!

``` python
def shout(word):
    """Print a string with three exclamation marks"""
    # Concatenate the strings: shout_word
    shout_word = word + '!!!'
    # Print shout_word
    print(shout_word)
# Call shout with the string 'congratulations'
shout('congratulations')
# Define shout with the parameter, word
```

    ## congratulations!!!

``` python
def shout(word):
    """Return a string with three exclamation marks"""
    # Concatenate the strings: shout_word
    shout_word = word + '!!!'
    # Replace print with return
    return(shout_word)
# Pass 'congratulations' to shout: yell
yell = shout('congratulations')
# Print yell
print(yell)
# Define shout with parameters word1 and word2
```

    ## congratulations!!!

``` python
def shout(word1, word2):
    """Concatenate strings with three exclamation marks"""
    # Concatenate word1 with '!!!': shout1
    shout1 = word1 +'!!!'
    
    # Concatenate word2 with '!!!': shout2
    shout2 = word2 +'!!!'
    
    # Concatenate shout1 with shout2: new_shout
    new_shout = shout1 + shout2
    # Return new_shout
    return new_shout
# Pass 'congratulations' and 'you' to shout(): yell
yell = shout('congratulations', 'you')
# Print yell
print(yell)
# Tuples
```

    ## congratulations!!!you!!!

``` python
nums = (3, 4, 5)
# Unpack nums into num1, num2, and num3
num1,num2,num3 = nums
# Construct even_nums
even_nums = (2, 4, 6)
# Define shout_all with parameters word1 and word2
def shout_all(word1, word2):
    
    # Concatenate word1 with '!!!': shout1
    shout1 = word1 + '!!!'
    
    # Concatenate word2 with '!!!': shout2
    shout2 = word2 + '!!!'
    
    # Construct a tuple with shout1 and shout2: shout_words
    shout_words = (shout1, shout2)
    # Return shout_words
    return shout_words
# Pass 'congratulations' and 'you' to shout_all(): yell1, yell2
yell1, yell2 = shout_all('congratulations', 'you')
# Print yell1 and yell2
print(yell1)
```

    ## congratulations!!!

``` python
print(yell2)
```

    ## you!!!

### Twitter DataFrame Analysis Function

``` python
# Import pandas
import pandas as pd
# Import Twitter das as DataFrame
tweets = 'https://assets.datacamp.com/production/course_1532/datasets/tweets.csv'
df = pd.read_csv(tweets)
# Define count_entries()
def count_entries(df, col_name):
    """Return a dictionary with counts of 
    occurrences as value for each key."""
    # Initialize an empty dictionary: langs_count
    langs_count = {}
    
    # Extract column from DataFrame: col
    col = df[col_name]
    
    # Iterate over lang column in DataFrame
    for entry in col:
        # If the language is in langs_count, add 1
        if entry in langs_count.keys():
            langs_count[entry] +=1
            
        # Else add the language to langs_count, set the value to 1
        else:
            langs_count[entry] = 1
    # Return the langs_count dictionary
    return(langs_count)
# Call count_entries(): result
result = count_entries(df,'lang')
# Print the result
print(result)
```

    ## {'en': 97, 'et': 1, 'und': 2}

Scope and User-Defined Functions
--------------------------------

``` python
# Create a string: team
team = "teen titans"
# Define change_team()
def change_team():
    """Change the value of the global variable team."""
    # Use team in global scope
    global team
    # Change the value of team in global: team
    team = 'justice league'
# Print team
print(team)
# Call change_team()
```

    ## teen titans

``` python
change_team()
# Print team
print(team)
# Define three_shouts
```

    ## justice league

``` python
def three_shouts(word1, word2, word3):
    """Returns a tuple of strings
    concatenated with '!!!'."""
    # Define inner
    def inner(word):
        """Returns a string concatenated with '!!!'."""
        return word + '!!!'
    # Return a tuple of strings
    return (inner(word1), inner(word2), inner(word3))
# Call three_shouts() and print
print(three_shouts('a', 'b', 'c'))
# Define echo
```

    ## ('a!!!', 'b!!!', 'c!!!')

``` python
def echo(n):
    """Return the inner_echo function."""
    # Define inner_echo
    def inner_echo(word1):
        """Concatenate n copies of word1."""
        echo_word = word1 * n
        return echo_word
    # Return inner_echo
    return inner_echo
# Call echo: twice
twice = echo(2)
# Call echo: thrice
thrice = echo(3)
# Call twice() and thrice() then print
print(twice('hello'), thrice('hello'))
# Define echo_shout()
```

    ## hellohello hellohellohello

``` python
def echo_shout(word):
    """Change the value of a nonlocal variable"""
    
    # Concatenate word with itself: echo_word
    echo_word = word + word
    
    #Print echo_word
    print(echo_word)
    
    # Define inner function shout()
    def shout():
        """Alter a variable in the enclosing scope"""    
        #Use echo_word in nonlocal scope
        nonlocal echo_word
        
        #Change echo_word to echo_word concatenated with '!!!'
        echo_word = echo_word + '!!!'
    
    # Call function shout()
    shout()
    
    #Print echo_word
    print(echo_word)
#Call function echo_shout() with argument 'hello'    
echo_shout('hello')
```

    ## hellohello
    ## hellohello!!!

### Default and Flexible Arguments

``` python
# Define shout_echo
def shout_echo(word1, echo = 1):
    """Concatenate echo copies of word1 and three
     exclamation marks at the end of the string."""
    # Concatenate echo copies of word1 using *: echo_word
    echo_word = word1 * echo
    # Concatenate '!!!' to echo_word: shout_word
    shout_word = echo_word + '!!!'
    # Return shout_word
    return shout_word
# Call shout_echo() with "Hey": no_echo
no_echo = shout_echo('Hey')
# Call shout_echo() with "Hey" and echo=5: with_echo
with_echo = shout_echo('Hey', echo = 5)
# Print no_echo and with_echo
print(no_echo)
```

    ## Hey!!!

``` python
print(with_echo)
```

    ## HeyHeyHeyHeyHey!!!
