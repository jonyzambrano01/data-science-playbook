# Notebook Overview

- Description:
    - This cheat sheet is focused on Python basics and core elements.

- Table of contents:
    - [Notebook Overview](#notebook-overview)
        - [Important Resources](#important-resources)
        - [Notation](#notation)
        - [Useful Commands](#useful-commands)
        - [Data Types](#data-types)
            - [Numeric](#numeric)
            - [String](#string)
            - [Datetime](#datetime)
        - [Conversion Between Data Types](#conversion-between-data-types)
        - [Data Structures](#data-structures)
            - [List](#list)
            - [Dictionary](#dictionary)
            - [Range](#range)

## Important Resources

- [Python 3.8 documentation](https://rb.gy/8hto6g)

## Notation

- `[param]`: optional parameter.
- `*args`: variable non-keyword arguments - more details in the functions section.
- `**kwargs`: variable keyword arguments - more details in the functions section.
- `***<param_name>`: self-explanatory parameter.
- `***self`: function that does not require parameter - part of the class.
- ```>>>```: executed code.

## Useful Commands

```python
>>> # Print a value - parameters: *args, [sep] = separator, [end] = character to put at the end of the printing process, [file] = file to print
>>> print('lorem ipsum')
>>> # Get the type of an object - parameters: ***object
>>> print(type('lorem ipsum'))
>>> # Ask for help - parameters: command = command that requires clarification 
>>> help(print)

lorem ipsum
<class 'str'>
Help on built-in function print in module builtins:

print(...)
    print(value, ..., sep=' ', end='\n', file=sys.stdout, flush=False)
...
```

## Data Types

### Numeric

- Types:
    - Int - a whole number, positive or negative, without decimals, of unlimited length.
    - Float (a floating-point number) - number, positive or negative, containing one or more decimals.

- Create variables:

    ```python
    >>> int_1 = 5
    >>> print(int_1)
    >>> float_1 = 5.1
    >>> print(float_1)

    5
    5.1
    ```

- Operations:

    ```python
    >>> # Variable assignment
    >>> x = 5
    >>> # Sum of two variables
    >>> print(x + 2)
    >>> # Subtraction of two variables
    >>> print(x - 2)
    >>> # Multiplication of two variables
    >>> print(x * 2)
    >>> # Exponentiation of a variable
    >>> print(x ** 2)
    >>> # Remainder of a division
    >>> print(x % 2)
    >>> # Division of a variable
    >>> print(x / 2)

    7
    3
    10
    25
    1
    2.5
    ```

### String

- Characters surrounded by quotation marks. String variables are iterable lists.
- Create variables:

    ```python
    >>> str_1 = 'lorem ipsum'
    >>> print(str_1)
    >>> # Embedded quotes
    >>> str_2 = 'lorem " ipsum'
    >>> print(str_2)
    >>> # Multiline strings - 3 double quotes
    >>> str_3 = """lorem ipsum dolor sit amet,
    consectetur adipiscing elit,
    sed do eiusmod tempor incididunt
    ut labore et dolore magna aliqua."""
    >>> print(str_3)
    ```

- String list properties:

    ```python
    >>> str_1 = 'lorem ipsum'
    >>> # Extract first character
    >>> print(str_1[0])
    >>> # Evaluate if string is in another
    >>> in_str = 'lorem' in str_1
    >>> print(in_srt)

    l
    True
    ```

- Additional string functions:

    ```python
    >>> str_1 = 'lorem ipsum'
    >>> str_2 = 'LOREM IPSUM'
    >>> str_3 = 'lorem ipsum '
    >>> str_4 = '1234'
    >>> # Upper - parameters: ***self
    >>> print(str_1.upper())
    >>> # Lower - parameters: ***self
    >>> print(str_2.lower())
    >>> # Capitalize - parameters: ***self
    >>> print(str_2.capitalize())
    >>> # Remove leading and trailing spaces or defined chars - parameters: [chars] = string to consider in the removal process
    >>> print(str_3.strip())
    >>> # Replace - parameters: old = old char, new = new char, [count] = max number of replacements
    >>> print(str_1.replace('lorem', 'dolor'))
    >>> # Split string by separator - parameters: sep = separator
    >>> print(str_1.split(sep = ' '))
    >>> # Insert value in placeholder - parameters: *args, **kwargs
    >>> print('lorem ipsum {}'.format('sit amet'))
    >>> # Check if all the characters are numbers - parameters: ***self
    >>> print(str_4.isnumeric())

    LOREM IPSUM
    lorem ipsum
    Lorem ipsum
    lorem ipsum
    dolor ipsum
    ['lorem', 'ipsum']
    lorem ipsum sit amet
    True
    ```

### Datetime

- Dates and hours.
- Create variables:

    ```python
    >>> # Import external library - datetime is not a built-in type 
    >>> import datetime
    >>> # Create datetime - parameters: ***year, ***month, ***day, ***[hour], ***[minute], ***[second], ***[microsecond]
    >>> datetime_1 = datetime.datetime(2021, 12, 5, 17, 50 )
    >>> print(datetime_1)
    >>> # Get date - parameters - ***self
    >>> print(datetime_1.date())
    >>> # Get time - parameters - ***self
    >>> print(datetime_1.time())
    >>> # Get year - parameters - ***self
    >>> print(datetime_1.year)
    >>> # Get day - parameters - ***self
    >>> print(datetime_1.day)
    >>> # Get hour - parameters - ***self
    >>> print(datetime_1.hour)
    >>> # Get minute - parameters - ***self
    >>> print(datetime_1.minute)

    2021-12-05 17:50:00
    2021-12-05
    17:50:00
    2021
    5
    17
    50
    ```

- Format a date:
    - A format is formed joining several directives (check table below) into a single string.
    | directive | meaning                                                                                        | example                                 |
    |-----------|------------------------------------------------------------------------------------------------|-----------------------------------------|
    | %a        | Weekday as locale’s abbreviated name.                                                          | Sun, Mon, …, Sat (en_US);               |
    | %A        | Weekday as locale’s full name.                                                                 | Sunday, Monday, …, Saturday (en_US);    |
    | %w        | Weekday as a decimal number, where 0 is Sunday and 6 is Saturday.                              | 0, 1, …, 6                              |
    | %d        | Day of the month as a zero-padded decimal number.                                              | 01, 02, …, 31                           |
    | %b        | Month as locale’s abbreviated name.                                                            | Jan, Feb, …, Dec (en_US);               |
    | %B        | Month as locale’s full name.                                                                   | January, February, …, December (en_US); |
    | %m        | Month as a zero-padded decimal number.                                                         | 01, 02, …, 12                           |
    | %y        | Year without century as a zero-padded decimal number.                                          | 00, 01, …, 99                           |
    | %Y        | Year with century as a decimal number.                                                         | 0001, 0002, …, 2013, 2014, …, 9998, 9999|
    | %H        | Hour (24-hour clock) as a zero-padded decimal number.                                          | 00, 01, …, 23                           |
    | %I        | Hour (12-hour clock) as a zero-padded decimal number.                                          | 01, 02, …, 12                           |
    | %p        | Locale’s equivalent of either am or pm.                                                        | AM, PM (en_US);                         |
    | %M        | Minute as a zero-padded decimal number.                                                        | 00, 01, …, 59                           |
    | %S        | Second as a zero-padded decimal number.                                                        | 00, 01, …, 59                           |
    | %f        | Microsecond as a decimal number, zero-padded to 6 digits.                                      | 000000, 000001, …, 999999               |
    | %j        | Day of the year as a zero-padded decimal number.                                               | 001, 002, …, 366                        |
    | %U        | Week number of the year (Sunday as the first day of the week) as a zero padded decimal number. | 00, 01, …, 53                           |
    | %W        | Week number of the year (Monday as the first day of the week) as a decimal number.             | 00, 01, …, 53                           |

    ```python
    >>> import datetime
    >>> datetime_1 = datetime.datetime(2021, 12, 5)
    >>> # Format a date - parameters: format: more information in the section above 
    >>> datetime_1.strftime("%d/%m/%Y")

    '05/12/2021'
    ```

- Timedeltas:
    - It is a duration expressing the difference between two datetime instances.

    ```python
    >>> import datetime
    >>> from datetime import timedelta
    >>> datetime_1 = datetime.datetime(2021, 12, 5)
    >>> datetime_2 = datetime_1 + timedelta(days = 2)
    >>> print(datetime_1)
    >>> print(datetime_2)

    2021-12-05 00:00:00 
    2021-12-07 00:00:00
    ```

## Conversion Between Data Types

```python
>>> str_1 = '5'
>>> int_1 = 2
>>> float_1 = 2.3
>>> # To float
>>> print(float(str_1))
>>> print(float(int_1))
>>> # To int
>>> print(int(str_1))
>>> print(int(float_1))
>>> # To str
>>> print(str(int_1))
>>> print(str(float_1))

5.0
2.0
5
2
2
2.3
```

## Data Structures

### List

- A list has ordered, changeable and indexed values. Values can be duplicated and have different data types.
- Create and get properties:

    ```python
    >>> list_1 = [1, 2, 3, 'a', 'b', 'c']
    >>> list_2 = [1, 2, 3]
    >>> print(list_1)
    >>> # Len of list - parameters: ***list
    >>> print(len(list_1))
    >>> # Max of list - parameters: ***list
    >>> print(max(list_2))
    >>> # Min of list - parameters: ***list
    >>> print(min(list_2))

    [1, 2, 3, 'a', 'b', 'c']
    6
    3
    1
    ```

- Extract data:

    ```python
    >>> list_1 = [1, 2, 3, 'a', 'b', 'c']
    >>> # Get element from a position (indexes start at 0)
    >>> print(list_1[0])
    >>> print(list_1[-1])
    >>> # Get sub-set of elements (slicing - the last number is not considered, just the previous)
    >>> print(list_1[1:3])
    >>> print(list_1[:3]) 
    >>> print(list_1[3:])
    >>> print(list_1[-5:-2])
    >>> # Define stride (step)
    >>> print(list_1[0:5:2])

    1
    c
    [2, 3]
    [1, 2, 3]
    ['a', 'b', 'c']
    [2, 3, 'a']
    [1, 3, 'b']
    ```

- Change items on the list, insert and delete items:

    ```python
    >>> list_1 = [1, 2, 3, 'a', 'b', 'c']
    >>> # Change an specific item
    >>> list_1[0] = 2
    >>> print (list_1)
    >>> # Change a range of items
    >>> list_1[0:2] = [3, 4]
    >>> print (list_1)
    >>> # Insert items - parameters: i = position, x = element to insert
    >>> list_1.insert(2, 5)
    >>> print(list_1)
    >>> # Insert at the end of the list - parameters: x = element to insert
    >>> list_1.append('d')
    >>> print(list_1)
    >>> # Append list - alternative: extend(): append any type of iterable
    >>> list_1 += ['h', 'i', 'j'] 
    >>> print(list_1)
    >>> # Remove the first element that matches the input - parameters: x = value to remove
    >>> list_1.remove(3)
    >>> print(list_1)
    >>> # Remove by index and return it - parameters: x = index of value to remove - alternative: del: does not return element
    >>> list_1.pop(0)
    >>> print(list_1)

    [2, 2, 3, 'a', 'b', 'c']
    [3, 4, 3, 'a', 'b', 'c']
    [3, 4, 5, 3, 'a', 'b', 'c']
    [3, 4, 5, 3, 'a', 'b', 'c', 'd']
    [3, 4, 5, 3, 'a', 'b', 'c', 'd', 'h', 'i', 'j']
    [4, 5, 3, 'a', 'b', 'c', 'd', 'h', 'i', 'j']
    [5, 3, 'a', 'b', 'c', 'd', 'h', 'i', 'j']
    ```

- Additional list functions:

    ```python
    >>> list_1 = [1, 2, 3, 'a', 'b', 'c']
    >>> list_2 = [1, 2, 3]
    >>> # Validate that an item exists in the list
    >>> in_list = 1 in list_1
    >>> print(in_list)
    >>> # Sort list - parameters: [reverse] = descending order
    >>> list_2.sort(reverse = True)
    >>> print(list_2)
    >>> # Multiply lists
    >>> list_3 = list_1 * 2
    >>> print(list_3)
    >>> # Return number of times that a specific value occurs - parameters: x = element to count
    >>> count_3 = list_3.count(3)
    >>> print(count_3)
    >>> # Return the position of the first occurrence of the value - parameters: x = element to find - alternative: find(): does not raise an exception if the item is not found
    >>> pos_3 = list_3.index(3)
    >>> print(pos_3)

    True
    [3, 2, 1]
    [1, 2, 3, 'a', 'b', 'c', 1, 2, 3, 'a', 'b', 'c']
    2
    2
    ```

### Dictionary

- A dictionary has value-key pairs. Keys are ordered (from python 3.7). Changeable values and keys. Keys cannot be duplicated and can have different data types.
- Create and get properties:

    ```python
    >>> dict_1 = {1: 'a', 2: 'b', 3: 'c'}
    >>> # Len of dict - parameters: ***dictionary
    >>> print(len(dict_1))
    >>> # Keys - parameters: ***self
    >>> print(dict_1.keys())
    >>> # Values - parameters: ***self
    >>> print(dict_1.values())
    >>> # Items - parameters: ***self
    >>> print(dict_1.items())

    3
    dict_keys([1, 2, 3])
    dict_values(['a', 'b', 'c'])
    dict_items([(1, 'a'), (2, 'b'), (3, 'c')])
    ```

- Extract data:

    ```python
    >>> dict_1 = {1: 'a', 2: 'b', 3: 'c'}
    >>> # Get element from a key
    >>> print(dict_1[1])

    a
    ```

- Change items of the dictionary, insert and delete items:

    ```python
    >>> dict_1 = {1: 'a', 2: 'b', 3: 'c'}
    >>> # Add an element
    >>> dict_1[4] = 'd'
    >>> print(dict_1.items())
    >>> # Change an element
    >>> dict_1[4] = 'e'
    >>> print(dict_1.items())
    >>> # Remove item - parameters: x = item to remove
    >>> dict_1.pop(4)
    >>> print(dict_1.items())

    dict_items([(1, 'a'), (2, 'b'), (3, 'c'), (4, 'd')])
    dict_items([(1, 'a'), (2, 'b'), (3, 'c'), (4, 'e')])
    dict_items([(1, 'a'), (2, 'b'), (3, 'c')])
    ```

- Additional dictionary functions:

    ```python
    >>> dict_1 = {1: 'a', 2: 'b', 3: 'c'}
    >>> # Validate that a key exists in the dictionary
    >>> in_dict = 1 in set_1
    >>> print(in_dict)

    True
    ```

### Range

- A range has an ordered, unchangeable and indexed sequence of consecutive and non-repeated numbers.
- Create and get properties:

    ```python
    >>> range_1 = range(3, 20, 2) # Range from 3 to 19. Last parameter is the step
    >>> print(list(range_1))
    >>> range_2 = range(5) # Range from 0 to 4
    >>> print(list(range_2))
    >>> # Len of range - parameters: iterable = range
    >>> print(len(range_1))

    [3, 5, 7, 9, 11, 13, 15, 17, 19]
    [0, 1, 2, 3, 4]
    9
    ```

- Extract data from a range:

    ```python
    >>> range_1 = range(3, 20, 2)
    >>> # Get element from an index
    >>> print(range_1[1])

    5
    ```
