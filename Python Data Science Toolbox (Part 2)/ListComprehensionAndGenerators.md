# List Comprehension

Creating list from other lists, from DataFrames columns etc

Single line of code. e.g. We want to take year from a timestamp, we have to use for loop, perform operations and then append the result in list

More efficient than using a for loop

> We can write list over any iterable
> There is a iterator variable
> Ouput expression

```
doctor = ['house', 'cuddy', 'chase', 'thirteen', 'wilson']
The list comprehension is [doc[0] for doc in doctor] and produces the list ['h', 'c', 'c', 't', 'w']
```
```
# Create list comprehension: squares
squares = [i**2 for i in range(10)]

```

## Nested list comprehensions

> [[output expression] for iterator variable in iterable]

```
# Create a 5 x 5 matrix using a list of lists: matrix
matrix = [[col for col in range(5)] for row in range(5)]

# Print the matrix
for row in matrix:
    print(row)

```

## Conditionals in Comprehension

you can apply a conditional statement to test the iterator variable by adding an if statement in the optional predicate expression part after the for statement in the comprehension:

> [ output expression for iterator variable in iterable if predicate expression ].
```
# Create a list of strings: fellowship
fellowship = ['frodo', 'samwise', 'merry', 'aragorn', 'legolas', 'boromir', 'gimli']

# Create list comprehension: new_fellowship
new_fellowship = [member for member in fellowship if len(member)>6]

# Print the new list
print(new_fellowship)

```

```
# Create a list of strings: fellowship
fellowship = ['frodo', 'samwise', 'merry', 'aragorn', 'legolas', 'boromir', 'gimli']

# Create list comprehension: new_fellowship
new_fellowship = [member if len(member)>6 else '' for member in fellowship]

# Print the new list
print(new_fellowship)

```

## Dictionary Comprehensions
```
# Create a list of strings: fellowship
fellowship = ['frodo', 'samwise', 'merry', 'aragorn', 'legolas', 'boromir', 'gimli']

# Create dict comprehension: new_fellowship
new_fellowship = {member: len(member) for member in fellowship}

# Print the new list
print(new_fellowship)

```

# Generater Expressions

( num*2 for num in range(10))  => Generator object

It is just like the list, but it is not stores the list in memory, it is not contruct the list. But the object on which we can iterate over. We can create list from this.

> This is what called is Lazy Evaluation


```
# Create generator object: result
result = (num for num in range(31))

# Print the first 5 values
print(next(result))
print(next(result))
print(next(result))
print(next(result))
print(next(result))

# Print the rest of the values
for value in result:
    print(value)

```
```
# Create a list of strings: lannister
lannister = ['cersei', 'jaime', 'tywin', 'tyrion', 'joffrey']

# Create a generator object: lengths
lengths = (len(person) for person in lannister)

# Iterate over and print the values in lengths
for value in lengths:
    print(value)

```
## Generate Functions

> returns Generator object when called

> Rather than returning a single value, they yields a sequence of values using a **yield** keyword.

```
# Create a list of strings
lannister = ['cersei', 'jaime', 'tywin', 'tyrion', 'joffrey']

# Define generator function get_lengths
def get_lengths(input_list):
    """Generator function that yields the
    length of the strings in input_list."""

    # Yield the length of a string
    for person in input_list:
        yield len(person)

# Print the values generated by get_lengths()
for value in get_lengths(lannister):
    print(value)

```

## Exercise

In this exercise, you will be using a list comprehension to extract the time from time-stamped Twitter data. The pandas package has been imported as pd and the file 'tweets.csv' has been imported as the df DataFrame for your use.

You can think of DataFrame columns as single-dimension arrays called Series.

Create a list comprehension that extracts the time from each row in tweet_time. Each row is a string that represents a timestamp, and you will access the 12th to 19th characters in the string to extract the time. Use entry as the iterator variable and assign the result to tweet_clock_time. Remember that Python uses 0-based indexing!

```
# Extract the created_at column from df: tweet_time
# the extracted column in tweet_time here is a Series data structure!
tweet_time = df['created_at']

# Extract the clock time: tweet_clock_time
tweet_clock_time = [entry[11:19] for entry in tweet_time]

# Print the extracted times
print(tweet_clock_time)
```

Great, you've successfully extracted the data of interest, the time, from a pandas DataFrame! Let's tweak your work further by adding a conditional that further specifies which entries to select.

>Additionally, add a conditional expression that checks whether entry[17:19] is equal to '19'.

```
# Extract the created_at column from df: tweet_time
tweet_time = df['created_at']

# Extract the clock time: tweet_clock_time
tweet_clock_time = [entry[11:19] for entry in tweet_time if entry[17:19] == '19']

# Print the extracted times
print(tweet_clock_time)

```