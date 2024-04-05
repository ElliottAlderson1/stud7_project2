```markdown
### 1.  Create a function to check whether a string is all lowercase

Your function should return a boolean value.

Examples:

| Input | Output |
| --- | --- |
| `'hello world'` | `True` |
| `'99 hello world'` | `True` |
| `'Hello world'` | `False` |

<details>

<summary>Click here for solutions:</summary>

```python
# Solution 1
def all_lowercase(string: str) -> bool:
    """Checks if a string is all lowercase."""

    for char in string:
        if char.isupper():
            return False
    return True

# Solution 2
def all_lowercase(string: str) -> bool:
    """Checks if a string is all lowercase."""

    return all([ char.islower() for char in string ])

# Solution 3
def all_lowercase(string: str) -> bool:
    """Checks if a string is all lowercase."""
    
    return string.islower()


print(all_lowercase('hello world'))
print(all_lowercase('Hello world.'))
print(all_lowercase('HELLO WORLD'))
```

</details>

---

### 2.  Create a function that takes an object as input and returns a message indicating whether the object is a string or an integer

Examples:

| Input | Output |
| --- | --- |
| `1` | `'The object is an integer.'` |
| `'abc'` | `'The object is a string.'` |
| `'hello world` | `'The object is a string.'` |

<details>

<summary>Click here for solutions:</summary>

```python
# Solution 1
def int_or_str(obj) -> str:
    """Checks to see if an object is an integer or string."""

    if type(obj) == int:
        return f'The object is a string.'
    if type(obj) == str:
        return f'The object is an integer.'

# Solution 2
def int_or_str(obj) -> str:
    """Checks to see if an object is an integer or string."""

    if type(obj) == str:
        obj_type = 'string'
    if type(obj) == int:
        obj_type = 'integer'

    return f'The object is a {obj_type}.'
```

</details>

---

### 3.  Create a function to compute the product of a list of integers (without using for loop)

Examples:

| Input | Output |
| --- | --- |
| `[1, 2, 3]` | `6` |
| `[4, 5, 6]` | `120` |
| `[3, -2, 4]` | `-24` |

<details>

<summary>Click here for solutions:</summary>

```python
def product(nums: list) -> int:
    """Computes the product of a list of integers."""

    if len(nums) == 1:
        return nums[0]
    return nums[0] * product(nums[1:])

print(product([1, 2, 3]))
print(product([4, 5, 6]))
print(product([3, -2, 4]))

```

</details>

---

### 4.  Write a Python function to check whether a number is divisible by another number

Examples:

| Input | Output |
| --- | --- |
| `9, 3` | `True` |
| `5, 2` | `False` |
| `21, 7` | `True` |

<details>

<summary>Click here for solutions:</summary>

```python
# Solution 1
def is_factor(n1: int, n2: int) -> bool:
    """Checks to see if a number is divisible by another number."""

    if n1 % n2 == 0:
        return True
    else:
        return False

# Solution 2
def is_factor(n1: int, n2: int) -> bool:
    """Checks to see if a number is divisible by another number."""

    if n1 % n2 == 0:
        return True
    return False

# Solution 3
def is_factor(n1: int, n2: int) -> bool:
    """Checks to see if a number is divisible by another number."""

    return n1 % n2 == 0
    
```

The best practice is to avoid using return statements inside of an if-else statement. The convention used in the 3<sup>rd</sup> solution should be used **whenever possible.**  This is the most clean and consise option.

</details>

---

### 5.  Create a function to return the Python version you are using

You may have to import a package.

Example output:

```shell
3.6.8 (default, Apr 12 2022, 06:55:39) 
[GCC 8.5.0 20210514 (Red Hat 8.5.0-10)]
```

<details>

<summary>Click here for solutions:</summary>

```python
import sys

def get_version():
    """Returns the current python version."""

    return sys.version

print(get_version())
```

</details>

---

### 6.  Create a function to get a string which is n (non-negative integer) copies of a given string

Examples:

| Input | Output |
| --- | --- |
| hello, 3 | hellohellohello |
| world, 2 | worldworld |

<details>

<summary>Click here for solutions:</summary>

```python
def multiply_string(string: str, multiplier: int) -> str:
    """Multiplies a string by N."""

    return string * multiplier

print(multiply_string('hello', 5))
print(multiply_string('hello world', 2))
```

</details>

---

### 7.  Check if a number is even or odd

Create a function that prompts the user for a number, and then prints a message indicating whether the number is even or odd.

<details>

<summary>Click here for solutions:</summary>

```python
# Solution 1
def is_even():
    """Returns a message if a number is even or not."""

    num = int(input('Please enter a number:\n'))
    return 'The number is even.' if num % 2 == 0 else 'The number is odd.'

# Solution 2
def is_even():
    """Returns a message if a number is even or not."""

    num = int(input('Please enter a number:\n'))
    return f'The number is {"even" if num % 2 == 0 else "odd"}.'

print(is_even())
```

The two solutions use something called a ternary operator.  Ternary operators basically look like an inline if-else statement.  We can use them to set the value of variables or even in return statements.  We can also use them in f-strings, like in the last answer.

</details>

---

### 8.  Create a function to count the occurrences of a given number within a list of numbers

| Example Inputs | Example Outputs |
| --- | --- |
| `[1, 1, 3], 1` | `2` |
| `[1, 2, 3], 3` | `1` |
| `[4, 4, 4], 4` | `3` |

<details>

<summary>Click here for solutions:</summary>

```python
# Solution 1
def count_item(nums: list, target: int) -> int:
    """Returns the number of occurrences of a number in the list."""

    count = 0
    for num in nums:
        if num == target:
            count += 1
    return count

# Solution 2
def count_item(nums: list, target: int) -> int:
    """Returns the number of occurrences of a number in the list."""

    return nums.count(target)

print(count_item([1, 1, 3], 1)) # 2 occurrences
print(count_item([1, 2, 3], 3)) # 1 occurrence
print(count_item([4, 4, 4], 4)) # 3 occurrences
```

</details>

---

### 9.  Write a Python function to find the lowest number from a list of numbers

**Do not use the built-in `min()` function.**

<details>

<summary>Click here for solutions:</summary>

```python
def minimum(nums: list) -> int:
    """Returns the lowest number."""

    minimum = None
    for num in nums:
        if minimum is None:
            minimum = num
        else:
            if num < minimum:
                minimum = num
    return minimum
```

</details>

---

### 10.  Write a Python function to find the highest number from a list of numbers

**Do not use the built-in `max()` function.**

<details>

<summary>Click here for solutions:</summary>

```python
def maximum(nums: list) -> int:
    """Returns the highest number."""

    maximum = None
    for num in nums:
        if maximum is None:
            maximum = num
        else:
            if num > maximum:
                maximum = num

    return maximum
```

</details>

---

### 11.  Create a function to return the longest string in a list of strings

Examples:

| Input | Output |
| --- | --- |
| `['abc', 'ab', 'a']` | `'abc'` |
| `['hello', 'my', 'friend']` | `'friend'` |

<details>

<summary>Click here for solutions:</summary>

```python
def longest(strings: list) -> str:
    """Finds the longest string in a list of strings."""

    sorted_strings  = sorted(strings, key=len)
    return sorted_strings[-1]

```

</details>

---

### 12.  Create a function to return the current date and time

:writing_hand:

Example Output:

```
Current date and time:
2014-07-05 14:34:14
```

<details>

<summary>Click here for solutions:</summary>

```python
import datetime

def current_datetime():
    """Returns the current date and time in a formatted fashion."""

    # Returns something like this: 2022-05-30T13:10:17.537986
    now = datetime.datetime.now().isoformat()

    # Split the previous datetime on the capital 'T' and set two variables.
    date, time = now.split('T')

    # Use the date and time in an f-string.  We only use the first 8 characters of the 'time' variable so that we only capture hh:mm:ss
    return f'Current date and time:\n{ date } { time[:8] }'

print(current_datetime())
```

</details>

---

### 13.  Create a function which accepts the radius of a circle from the user and computes the area

Examples:

| Input | Output |
| --- | --- |
| `1.1` | `3.8013271108436504` |
| `3.0` | `28.274333882308138` |
| `.5` | `0.7853981633974483` |

Hint: You can import the number pi from the 'math' package in the standard library.

<details>

<summary>Click here for solutions:</summary>

```python
from math import pi

def get_circle_area(radius: float) -> float:
    """Returns the area of a circle with a given radius."""

    return pi * radius * radius

print(get_circle_area(1.1))
```

</details>

---

### 14.  Create a function which accepts the user's first and last name and returns them in reverse order with a comma and space between them

Examples:

| Input | Output |
| --- | --- |
| `'John Doe'` | `'Doe, John'` |
| `'Jane Doe'` | `'Doe, Jane'` |
| `'Michael Scott'` | `'Scott, Michael'` |

<details>

<summary>Click here for solutions:</summary>

```python
def reverse_names():
    """Returns a full name in reverse order."""

    name = input('Please enter your first and last name separated by a space:\n')

    first, last = name.split()

    return f'{last}, {first}'

print(reverse_names())
```

Remember, functions should rarely actually print a message.  Best practice is for a function to _return_ something, in this case, a string.

</details>

---

### 15.  Create a function to check whether a string is only numbers

Examples:

| Input | Output |
| --- | --- |
| `'1234'` | `True` |
| `'abc123'` | `False` |

<details>

<summary>Click here for solutions:</summary>

```python
# Solution 1
def is_numbers(string: str) -> bool:
    """Checks to see if a string is only numbers."""

    for char in string:
        if not char.isdigit():
            return False
    return True

# Solution 2
def is_numbers(string: str) -> bool:
    """Checks to see if a string is only numbers."""

    return string.isdigit()
```

</details>

---

### 16.  Create a function that takes two integers and returns a message stating their values along with their sum

Examples:

| Input | Output |
| --- | --- |
| `20, 30` | `'20 + 30 = 50'` |
| `15, 15` | `'15 + 15 = 30'` |
| `10, 5` | `'10 + 5 = 15'` |

<details>

<summary>Click here for solutions:</summary>

```python
def message(x: int, y: int) -> str:
    """Computes the sum of two numbers."""

    return f'{x} + {y} = {x + y}'

print(message(20, 30))
```

</details>

---

### 17.  Create a function to accept a filename from the user and return just the extension

Examples:

| Input | Output |
| --- | --- |
| `'requirements.txt'` | `'txt'` |
| `'example.js'` | `'js'` |
| `'readme.md'` | `'md'` |

<details>

<summary>Click here for solutions:</summary>

```python
def get_file_extension(full_filename: str) -> str:
    """Returns a file's extension type."""

    file_name, extension = full_filename.split('.')
    return extension

print(get_file_extension('requirements.txt'))
```

</details>

---

### 18.  Create a function that takes in a list and returns the list without the first item

Examples:

| Input | Output |
| --- | --- |
| `[1, 2, 3]` | `[2, 3]` |
| `['a', 'b', 'c']` | `['b', 'c']` |
| `[True, False, False]` | `[False, False]` |

<details>

<summary>Click here for solutions:</summary>

```python
def del_first(some_list: list) -> list:
    """Removes the first item from a list."""

    return some_list[1:]
```

</details>

---

### 19.  Create a function to return the first and last elements from a list in a new list

Examples:

| Input | Output |
| --- | --- |
| `['Red','Green','White' ,'Black']` | `['Red', 'Black']` |
| `['data', 'voice', 'management', 'video']` | `['data', 'video']` |
| `[10, 11, 12, 13, 14, 15]` | `[10, 15]` |

<details>

<summary>Click here for solutions:</summary>

```python
# Solution 1
def first_last(items: list) -> list:
    """Returns a new list containing the first and last elements from another list."""

    return items[::len(items) - 1]

# Solution 2
def first_last(items: list) -> list:
    """Returns a new list containing the first and last elements from another list."""

    del items[1:-1]
    return items

# Solution 3
def first_last(items: list) -> list:
    """Returns a new list containing the first and last elements from another list."""

    return [items[0], items[-1]]
```

</details>

---

### 20.  Create a function to return a formatted message with a date

:writing_hand:

Your function should take a tuple as input that contains the month, day, and year.

Examples:

| Input | Output |
| --- | --- |
| `(07, 09, 2022)` | `'The examination will start at: 07 / 09 / 2022'` |
| `(11, 12, 2014)` | `'The examination will start at: 11 / 12 / 2014'` |
| `(04, 01, 2019)` | `'The examination will start at: 04 / 01 / 2014'` |

<details>

<summary>Click here for solutions:</summary>

```python
# Solution 1
def get_schedule(exam_st_date: tuple) -> str:
    """Returns a formatted message with a date."""

    return f'The examination will start from: {exam_st_date[0]} / {exam_st_date[1]} / {exam_st_date[2]}'

# Solution 2
def get_schedule(exam_st_date: tuple) -> str:
    """Returns a formatted message with a date."""

    return 'The examination will start from: {} / {} / {}'.format(exam_st_date[0], exam_st_date[1], exam_st_date[2])

# Solution 3
def get_schedule(exam_st_date: tuple) -> str:
    """Returns a formatted message with a date."""

    return 'The examination will start from: {} / {} / {}'.format(*exam_st_date)

print(get_schedule((11, 12, 2014)))
```

The third solution uses something called unpacking.  We can unpack an iterable item by using a `*` in front of it.  By passing `*exam_st_date` to the `.format()` string method, we can unpack that iterable and use it to fill in the three spots in our string.

</details>

---

### 21.  Create a function to check whether three variables have the same value

Examples:

| Input | Output |
| --- | --- |
| `1, 1, 1` | `True` |
| `'abc', 'def', 'ghi'` | `False` |
| `'hello', 'hello', 'world'` | `False` |

<details>

<summary>Click here for solutions:</summary>

```python
# Solution 1
def all_three_same(a, b, c) -> bool:
    """Determines if three objects have the same value."""

    return a == b and b == c:

# Solution 2
def all_three_same(a, b, c):
    """Determines if three objects have the same value."""

    return len(set([a, b, c])) == 1

# Solution 3
def all_three_same(a, b, c):
    """Determines if three objects have the same value."""

    return a == b == c

```

In this problem no solution is much better than the others.  There are just many ways to skin this cat.

</details>

---

### 22.  Determine the 'truthiness' of an integer

Every object in Python can be evaluated in its raw form to return either True or False.  This concept is called 'truthiness'.  Here is a table describing what would make each data type evaluate to True or False:

| type | truthiness |
| ---  | ---        |
| string | any non-empty string is True |
| integer  | 0 is False, all other numbers are True (including negative) |
| data structures (list, tuple, set, dict) | empty container evaluates to False, container with items evaluates to True |
| None | False | 

Create a function that takes an integer and returns whether or not the integer would evaluate to true or false.

Do not use the `bool()` built-in function as this would accomplish the logic for you.

Examples:

| Input | Output |
| --- | --- |
| `1` | `True` |
| `0` | `False` |
| `-1` | `True` |
| `-5` | `True` |
| `10` | `True` |

<details>

<summary>Click here for solutions:</summary>

```python
# Solution 1
def is_truthy(num: int) -> bool:
    """Checks an int to see if it evaluates to True"""

    return int != 0

# Solution 2:
def is_truthy(num: int) -> bool:
    """
    Checks an int to see if it evaluates to True.
    Note: This is just for demonstration purposes.  This solution does not fit the requirements of the exercise.
    """
    return bool(num)

```

Solution 2 is just an example of how the `bool()` built-in function would essentially evaluate an object for us so that we don't have to create the logic ourselves.  This solution did not fit the requirements of the exercise.

</details>

---

### 23.  Determine the 'truthiness' of a string

Every object in Python can be evaluated in its raw form to return either True or False.  This concept is called 'truthiness'.  

| type | truthiness |
| ---  | ---        |
| string | any non-empty string is True |
| integer  | 0 is False, all other numbers are True (including negative) |
| data structures (list, tuple, set, dict) | empty container evaluates to False, container with items evaluates to True |
| None | False | 

Create a function that takes a _string_ as an argument and returns whether or not the string would evaluate to true or false.

Do not use the `bool()` built-in function as this would accomplish the logic for you.

Examples:

| Input | Output |
| --- | --- |
| `'abc'` | `True` |
| `'hello'` | `True` |
| `''` | `False` |
| `'False'` | `True` |

<details>

<summary>Click here for solutions:</summary>

```python
# Solution 1
def is_truthy(string: str) -> bool:
    """Checks a string to see if it is truthy"""

    return string != ''

# Solution 3:
def is_truthy(string: str) -> bool:
    """
    Checks a string to see if it is truthy.
    Note: This is just for demonstration purposes.  This solution does not fit the requirements of the exercise.
    """
    return bool(string)

```

Solution 3 is just an example of how the `bool()` built-in function would essentially evaluate an object for us so that we don't have to create the logic ourselves.  This solution did not fit the requirements of the exercise.

</details>

---

### 24.  Create a function that determines the truthiness of a data structure

Your function should be able to take in a list, set, tuple, dictionary as an argument and return whether or not the object evaluates to true.

Every object in Python can be evaluated in its raw form to return either True or False.  This concept is called 'truthiness'.  

| type | truthiness |
| ---  | ---        |
| string | any non-empty string is True |
| integer  | 0 is False, all other numbers are True (including negative) |
| data structures (list, tuple, set, dict) | empty container evaluates to False, container with items evaluates to True |
| None | False |

Do not use the `bool()` built-in function as this would accomplish the logic for you.

Examples:

| Input | Output |
| --- | --- |
| `[]` | `False` |
| `[1, 2, 3]` | `True` |
| `{}` | `False` |
| `{'some_key': False}` | `True` |
| `()` | `False` |
| `(1, 2, 3)` | `True` |

<details>

<summary>Click here for solutions:</summary>

```python
# Solution 1
def is_truthy(obj) -> bool:
    """Checks an object to see if it is truthy"""

    return len(obj) > 0

# Solution 2:
def is_truthy(obj) -> bool:
    """
    Checks an object to see if it is truthy.
    Note: This is just for demonstration purposes.  This solution does not fit the requirements of the exercise.
    """
    return bool(obj)

```

Solution 2 is just an example of how the `bool()` built-in function would essentially evaluate an object for us so that we don't have to create the logic ourselves.  This solution did not fit the requirements of the exercise.

</details>

---

### 25.  Create a function that returns the truthiness of a list of items

Create a function that accepts a list of integers and strings and returns a _dictionary_, where each list item is a key, and each key's value indicates the key's truthiness.

Examples:

| Input | Output |
| --- | --- |
| `[-2, -1, 0, 1, 2]` | `{-2: True, -1: True, 0: False, 1: True, 2: True}` |
| `['a', 'b', 'c', '']` | `{'a': True, 'b': True, 'c': True, '': False}` |
| `[0, 1, 2, '', 'abc']` | `{0: False, 1: True, 2: True, '': False, 'abc': True}` |

Do not use the built-in `bool()` function.

<details>

<summary>Click here for solutions:</summary>

```python
# Solution 1
def truthy_dict(items: list) -> dict:
    """Returns a dict indicating items and their truthiness."""

    result = {}
    for item in items:
        if type(item) == int:
            if item != 0:
                result[item] = True
            else:
                result[item] = False
        if type(item) == str:
            if item != '':
                result[item] = True
            else:
                result[item] = False
    return result

# Solution 2
def truthy_dict(items: list) -> dict:
    """Returns a dict indicating items and their truthiness."""

    result = {}
    for item in items:
        if type(item) == int:
            result[item] = item != 0
        if type(item) == str:
            result[item] = item != ''
    return result

# Solution 3
def truthy_dict(items: list) -> dict:
    """
    Returns a dict indicating items and their truthiness.
    This solution doesn't fit the exercise requirements, but it does show what a concise solution could look like.
    """

    result = { item: bool(item) for item in items }
    return result

print(truthy_dict([-2, -1, 0, 1, 2]))
print(truthy_dict(['a', 'b', 'c', '']))
print(truthy_dict([0, 1, 2, '', 'abc']))
```

Solution 1 creates an empty result dictionary, loops through the original list, and for each item, it checks to see if it is an integer or a string.  Depending on the type, another if statement checks the object to see if it would evaluate to `True` or `False` based on Python's truthiness rules, and sets that as the value for the specified key in the `result` dictionary.

Just like solution 1, solution 2 loops through the list, and for each item, it checks to see if it is an integer or a string.  The difference is that solution 2 then directly sets the value of the given key to a _comparison_.  Comparisons always return boolean values, so by setting the value of a key to a comparison, i.e. `result[item] = item != 0`, we are directly setting the value to `True` or `False`.  We just have to make sure the comparisons correctly determine the truthiness of a given object.

Solution 3 doesn't fit the exercise requirements, but it does show what a more advanced solution would look like.  It uses a dictionary comprehension to make the result dictionary and simply uses the `bool()` function against each item in the list.

</details>

---

### 26.  Create a function that sorts a dictionary

Given a dictionary, your function should return a new dictionary that contains the keys in sorted order.  

Integers should come before letters.

Examples:

| Input | Output |
| --- | --- |
| `{'z': None, 'j': None, 'a': None}` | `{'a': None, 'j': None, 'z': None}` |
| `{2: None, 0: None, -2: None}` | `{-2: None, 0: None, 2: None}` |
| `{'z': None, 'y': None, 'x': None, 0: None, 1: None}` | `{0: None, 1: None, 'x': None, 'y': None, 'z': None}` |

<details>

<summary>Click here for solutions:</summary>

```python
def alpha_dict(random_dict: dict) -> dict:
    """Sorts a dictionary alphabetically."""

    result = {}

    int_keys = [key for key in random_dict.keys() if type(key) == int]
    str_keys = [key for key in random_dict.keys() if type(key) == str]

    for int_key in sorted(int_keys):
        result[int_key] = random_dict[int_key]
    for str_key in sorted(str_keys):
        result[str_key] = random_dict[str_key]
    
    return result


print(alpha_dict({'z': None, 'j': None, 'a': None}))
print(alpha_dict({2: None, 0: None, -2: None}))
print(alpha_dict({'z': None, 'y': None, 'x': None, 0: None, 1: None}))
```

First, we create an empty dictionary.  Then, we create two lists, one containing all the integer keys and one containing all the string keys.  Then we loop through the sorted version of the integer keys list, and add each one with the appropriate value to the `result` dictionary. We then loop through the list of string keys and do the same thing.  

</details>

---

### 27.  Create a function that counts each character in a string

Given a string, your function should return a dictionary that tells you how many occurences of each character there are in the string.

Uppercase and lowercase letters should be considered the same character.  **Only account for letters and numbers.**

Examples:

| Input | Output |
| --- | --- |
| `'hello world.'` | `{'w': 1, 'o': 2, 'l': 3, 'e': 1, 'h': 1, 'r': 1, 'd': 1}` |
| `'1 for you, 1 for me.'` | `{'o': 3, 'y': 1, 'e': 1, '1': 2, 'u': 1, 'r': 2, 'm': 1, 'f': 2}` |
| `'This is a simple message.'` | `{'a': 2, 't': 1, 'e': 3, 'p': 1, 'l': 1, 'g': 1, 'h': 1, 's': 5, 'm': 2, 'i': 3}` |

<details>

<summary>Click here for solutions:</summary>

```python
def char_count(string: str) -> dict:
    """Returns a dictionary telling you how many occurences of each letter are in a string."""

    # Create a set of unique letters using a set comprehension
    unique_chars = {char for char in string.lower() if char.isalnum()}

    # Find the occurrences of each unique character
    result = {}
    for char in unique_chars:
        result[char] = string.lower().count(char)
    return result

print(char_count('Hello world.'))
print(char_count('1 for you, 1 for me.'))
print(char_count('This is a simple message.'))
```

This solution uses a set comprehension to create a set of the unique letters in the string.  In the set comprehension, we are creating a set that includes every character for each character in the lowercased version of the string if the character is alphanumeric.

</details>

---

### 28.  Create a function that finds the indices of each character in a string

Given a string, your function should return a dictionary that contains each unique letter within the string and all the indexes where that letter occurs in the string.

For this exercise, assume that the string will contain only letters and spaces.  Lowercase and uppercase letters should be considered the same.

Examples:

| Input | Output |
| --- | --- |
| `'hello'` | `{'h': [0], 'e': [1], 'l': [2, 3], 'o': [4]}` |
| `'abcabcabc'` | `{'a': [0, 3, 6], 'b': [1, 4, 7], 'c': [2, 5, 8]}` |
| `'ABCabcabc'` | `{'a': [0, 3, 6], 'b': [1, 4, 7], 'c': [2, 5, 8]}` |
| `'abcdef'` | `{'a': [0], 'b': [1], 'c': [2], 'd': [3], 'e': [4], 'f': [5]}` |

<details>

<summary>Click here for solutions:</summary>

```python
def char_indices(string: str) -> dict:
    """Returns the index numbers of each unique char in a string."""

    result = {}
    for index, char in enumerate(string.lower()):
        result.setdefault(char, []).append(index)
    return result

print(char_indices('hello'))
print(char_indices('abcabcabc'))
print(char_indices('ABCabcabc'))
print(char_indices('abcdef'))
```

Here we make use of the `enumerate()` function.  The enumerate function simply gives you the items in a list along with their respective index numbers.

We loop through the lowercase version of the string, using `enumerate()` so that we have access to each character's respective index, and for each character, we use the `.setdefault()` dictionary method.

The `.setdefault()` dictionary method will retrieve the value of a requested key in a dictionary, however, if the key doesn't exist, you can set a default value for the key.  This comes in handy in this solution when we are adding a character as a key to the `result` dictionary that wasn't previously there.  

</details>

---

### 29.  Create a function that combines two lists into a dictionary

Given two lists, return a dictionary that uses the items from the first list as keys and items from the second list as values.

The items used as keys must be what is are known as 'hashable' data times.  This means the keys cannot be lists or dictionaries.  They must be int, float, str, tuple, boolean, or None.

For this exercise, you can assume that the lists will have an equal number of items.

Examples:

| Input | Output |
| --- | --- |
| `['a', 'b', 'c'], ['a', 'b', 'c']` | `{'a': 'a', 'b': 'b', 'c': 'c'}` |
| `[1, 2, 3], [1, 2, 3]` | `{1: 1, 2: 2, 3: 3}` |
| `[1, 2, 3], ['a', 'b', 'c']` | `{1: 'a', 2: 'b', 3: 'c'}` |

<details>

<summary>Click here for solutions:</summary>

```python
# Solution 1
def combine_lists(keys: list, values: list) -> dict:
    """Combines two lists to create a dictionary."""

    result = {}
    for index in range(len(keys)):
        result[keys[index]] = values[index]
    return result

# Solution 2
def combine_lists(keys: list, values: list) -> dict:
    """Combines two lists to create a dictionary."""

    result = {}
    for key, value in zip(keys, values):
        result[key] = value
    return result

# Solution 3
def combine_lists(keys: list, values: list) -> dict:
    """Combines two lists to create a dictionary."""

    result = { key:value for key, value in zip(keys, values) }
    return result

print(combine_lists(['a', 'b', 'c'], ['a', 'b', 'c']))
print(combine_lists([1, 2, 3], [1, 2, 3]))
print(combine_lists([1, 2, 3], ['a', 'b', 'c']))
```

The last solution uses a dictionary comprehension with the `zip()` function.  The `zip()` function allows you to loop through two different iterable objects _simultaneously_.

Since we are looping through two different objects at once, we can use two loop variables, key and value.

</details>

---

### 30.  NumNumNum

Create a function that accepts an integer (n) and computes the value of n+nn+nnn.

Examples:

| Input | Logic | Output |
| --- | --- | --- |
| `5` | `5 + 55 + 555` | `615` |
| `1` | `1 + 11 + 111` | `123` |
| `3` | `3 + 33 + 333` | `369` |

<details>

<summary>Click here for solutions:</summary>

```python
def my_func(num: int) -> int:
    """Returns num + numnum + numnumnum"""

    return num + int(str(num) * 2) + int(str(num) * 3)

print(my_func(5))
print(my_func(1))
print(my_func(3))
```

</details>

---

### 31.  Create a function to calculate number of days between two dates (year, month, day)

Each inputted date should be year, month, and day, in tuple format.  For example: `(2014, 7, 2)`.

>Hint: You can use the `date` class from the `datetime` module and find a delta between two `date` objects.

Examples:

| Input | Output |
| --- | --- |
| `(2014, 7, 2), (2014, 7, 11)` | `9 days` |
| `(2019, 4, 1), (2020, 4, 1)` | `366 days` |
| `(2020, 4, 1), (2019, 4, 1)` | `366 days` |

<details>

<summary>Click here for solutions:</summary>

```python
from datetime import date

def day_delta(date_1: tuple, date_2: tuple) -> str:
    """Returns the number of days between two dates."""

    date_1_object = date(*date_1)
    date_2_object = date(*date_2)

    delta = date_1_object - date_2_object

    return f'{abs(delta.days)} days.'

print(day_delta((2014, 7, 2), (2014, 7, 11)))
print(day_delta((2019, 4, 1), (2020, 4, 1)))
print(day_delta((2020, 4, 1), (2019, 4, 1)))
```

</details>

---

### 32.  Create a function to get the volume of a sphere with a given radius

Note: volume of a sphere: V = 4/3 *π* r<sup>3</sup>

Examples:

| Input | Output |
| --- | --- |
| `3` | `113.09733552923254` |
| `8` | `2144.660584850632` |
| `5` | `523.5987755982989` |

<details>

<summary>Click here for solutions:</summary>

```python
from math import pi

def get_sphere_volume(radius: int) -> float:
    """Returns a sphere's radius."""

    return (4/3) * pi * radius**3

print(get_sphere_volume(3))
```

</details>

---

### 33.  Create a function to test whether a number is within 100 of 1000 or 2000

Your function should return a boolean value.

Examples:

| Input | Output |
| --- | --- |
| `899` | `False` |
| `900` | `True` |
| `1099` | `True` |
| `1899` | `False` |
| `1900` | `True` |
| `2099` | `True` |

<details>

<summary>Click here for solutions:</summary>

```python
def test_limits(num: int) -> bool:
    """Returns whether a number is within 100 of 1000 or 2000."""

    return (abs(1000 - num) <= 100 or abs(2000 - num) <= 100)

print(test_limits(899))
print(test_limits(900))
print(test_limits(1099))
print(test_limits(1899))
print(test_limits(1900))
print(test_limits(2099))

```

</details>

---

### 34.  Create a function to calculate the sum of three given numbers.  If the values are all equal then return three times of their sum

Examples:

| Input | Output |
| --- | --- |
| `1, 2, 3` | `6` |
| `2, 2, 2` | `18` |

<details>

<summary>Click here for solutions:</summary>

```python
def sum_of_three(num_1: int, num_2: int, num_3: int) -> int:
    """Calculates the sum of three numbers.  Returns 3x the sum if the values are all equal."""

    if num_1 == num_2 == num_3:
        return 3 * (num_1 + num_2 + num_3)
    else:
        return num_1 + num_2 + num_3

print(sum_of_three(1, 2, 3))
print(sum_of_three(2, 2, 2))
```

</details>

---

### 35.  Create a function to get the n (non-negative integer) copies of the first 2 characters of a given string. :writing_hand

Examples:

| Input | Output |
| --- | --- |
| `'hello', 3` | `'hehehe'` |
| `'at', 3` | `'atatat'` |
| `'c', 4` | `'cccc'` |

<details>

<summary>Click here for solutions:</summary>

```python
def my_func(string: str, multiplier: int) -> str:
    """Returns the first two characters of a string N times."""

    return multiplier * string[:2]

print(my_func('hello', 3))
print(my_func('he', 3))
print(my_func('h', 3))
```

</details>

---

### 36.  Write a Python function that takes a positive integer and returns the sum of the cube of all the positive integers smaller than the specified number

Examples:

| Input | Logic | Output |
| --- | --- | --- |
| `3` | 1<sup>3</sup> + 2<sup>3</sup> | `9` |
| `4` | 1<sup>3</sup> + 2<sup>3</sup> + 3<sup>3</sup> | `36` |
| `5` | 1<sup>3</sup> + 2<sup>3</sup> + 3<sup>3</sup> + 4<sup>3</sup> | `100` |

<details>

<summary>Click here for solutions:</summary>

```python
# Solution 1
def sum_of_cubes(num: int) -> int:
    """Returns the sum of the cubes of all numbers less than a specified number."""

    result = 0
    for num in range(1, num):
        result += num**3
    return result

# Solution 2
def sum_of_cubes(num: int) -> int:
    """Returns the sum of the cubes of all numbers less than a specified number."""

    result = sum([ num**3 for num in range(num) ])
    return result

print(sum_of_cubes(3)) # 1 + 8 = 9
print(sum_of_cubes(4)) # 1 + 8 + 27 = 36
print(sum_of_cubes(5)) # 1 + 8 + 27 + 64 = 100
```

The second solution puts an entire list comprehension inside a `sum()` function call.

</details>

---

### 37.  Create a function to check whether a specified integer is contained in a list of integers

Examples:

| Input | Output |
| --- | --- |
| `5, [1, 5, 8, 3]` | `True` |
| `3, [1, 5, 8, 3]` | `True` |
| `-1, [1, 5, 8, 3]` | `False` |

<details>

<summary>Click here for solutions:</summary>

```python
# Solution 1
def contains(item: int, items: list) -> bool:
    """Returns a boolean indicating whther an item is in a list."""

    for thing in items:
        if item == thing:
            return True
    return False

# Solution 2
def contains(item: int, items: list) -> bool:
    """Returns boolean indicating whether an item is in a list."""
    
    return item in items

print(contains(5, [1, 5, 8, 3]))
print(contains(3, [1, 5, 8, 3]))
print(contains(-1, [1, 5, 8, 3]))

```

</details>

---

### 38.  Create a function to test whether a passed letter is a vowel or not

Examples:

| Input | Output |
| --- | --- |
| `'a'` | `True` |
| `'b'` | `False` |
| `'i'` | `True` |
| `'z'` | `False` |

<details>

<summary>Click here for solutions:</summary>

```python
def is_vowel(letter: str) -> bool:
    """Returns whether or not a letter is a vowel."""

    VOWELS = 'aeiou'
    return letter in VOWELS

print(is_vowel('a'))
print(is_vowel('b'))
print(is_vowel('i'))
print(is_vowel('z'))
```

Anytime we use the `in` keyword, a boolean is returned, therefore, we don't even need an if-else statement to return True/False in the third solution.  We are simply returning the result of the `in` keyword.

</details>

---

### 39.  Create a function to create a histogram from a given list of integers.  :writing_hand

A histogram looks similar to a bar graph.  Given a list of values, a special character would be printed x number of times for each integer.  For example, if we use the `*` as our special character, given a list `[1, 2, 3, 4, 5]`, the resulting histogram would look like this:

```
*
**
***
****
*****
```

A list of `[2, 4, 3, 5, 1]` would look like this:

```
**
****
***
*****
*
```

Your function should take in a list of numbers and a special character, and return a histogram.

<details>

<summary>Click here for solutions:</summary>

```python
# Solution 1
def histogram(nums: list, char: str) -> str:
    """Prints a histogram using a list of numbers."""

    for num in nums:
        print(num * char)

# Solution 2
def histogram(nums: list, char: str) -> str:
    """Returns a histogram using a list of numbers."""

    bars = []
    for num in nums:
        bars.append(char * num)

    return '\n'.join(bars)

# Solution 3
def histogram(nums: list, char: str) -> str:
    """Returns a histogram using a list of numbers."""

    return '\n'.join(char * num for num in nums)

print(histogram([1, 2, 3, 4, 5]))
print(histogram([2, 4, 3, 5, 1]))
```

Solution 1 is weaker here because it is printing the output one line at a time, whereas the other solutions return a single object.  

Solution 2 creates a list, where each item in the list is the special character multiplied by the given number in the inputted list.  It then joins the items in the list using a `\n` newline character.

Solution 3 accomplishes the same thing as solution 2, however a list comprehension is used.

</details>

---

### 40.  Create a function to concatenate all elements in a list into a string and return it

Examples:

| Input | Output |
| --- | --- |
| `['a', 'b', 'c']` | `'abc'` |
| `[1, 2, 3, 4, 5]` | `'12345'` |
| `[(1, 2), 'abc', 3.4]` | `'(1, 2)abc3.4'` |

<details>

<summary>Click here for solutions:</summary>

```python
# Solution 1
def cat_objects(items: list) -> str:
    """Combines all list items into a string."""

    output = ''
    for item in item:
        output += str(item)
    return output

# Solution 2
def cat_objects(items: list) -> str:
    """Combines all list items into a string."""

    string_items = [ str(item) for item in items ]
    return ''.join(string_items)

print(cat_objects(['a', 'b', 'c']))
print(cat_objects([1, 2, 3, 4, 5]))
print(cat_objects([(1, 2), 'abc', 3.4]))
```

The second solution uses something called a list comprehension.  A list comprehension is a shorthand way of using a for-loop to create a list.  In this example, we loop through the items of the list, turn each item into a string, and append it to the `string_items` list.  Then, in the return statement, we just join the list with an empty string.

</details>

---

### 41.  Create a function to print out a set containing all the items from one list which are not present in a second list.  :writing_hand

Examples:

| Input | Output |
| --- | --- |
| `[1, 2, 3], [2, 3]` | `{1}` |
| `['a', 'b', 'c', 'd', 'e'], ['a', 'b', 'c']` | `{'d', 'e'}` |
| `['White', 'Black', 'Red', 'Green'], ['Red', 'Green']` | `{'Black', 'White'}` |

<details>

<summary>Click here for solutions:</summary>

```python
# Solution 1
def unique(lst_a: list, lst_b: list) -> list:
    """Returns a set containing all the items from a first list that are not in a second list."""

    result = set()
    for item_a in lst_a:
        if item_a not in lst_b:
            result.add(item)
    return result

# Solution 2
def unique(lst_a: list, lst_b: list) -> list:
    """Returns a set containing all the items from a first list that are not in a second list."""

    result = { item_a for item_a in lst_a if item_a not in lst_b }
    return result


# Solution 3
def unique(lst_a: list, lst_b: list) -> list:
    """Returns a set containing all the items from a first list that are not in a second list."""
    
    set_a, set_b = set(lst_a), set(lst_b)
    return set_a.difference(set_b)

print(unique([1, 2, 3], [2, 3]))
print(unique(['a', 'b', 'c', 'd', 'e'], ['a', 'b', 'c']))
print(unique(['White', 'Black', 'Red', 'Green'], ['Red', 'Green']))
```

Solution 2 uses a set comprehension.  It works the same way as a list comprehension.

Solution 3 uses a handy method available for sets.  Sets have many useful methods that allow you to compare them to other sets.  You can find unions, differences and lots of other things.

</details>

---

### 42.  Find the intersection of two sets  :writing_hand

Create a function that takes in two sets and returns a set containing all the elements that they have in common.

Examples:

| Input | Output |
| --- | --- |
| `{1, 2, 3}, {2, 3, 4}` | `{2, 3}` |
| `{'a', 'b', 'c', 'd'}, {'c', 'c', 'd'}` | `{'d', 'c'}` |
| `{'White', 'Black', 'Red', 'Green'}, {'Black', 'Black', 'Yellow'}` | `{'Black'}` |

<details>

<summary>Click here for solutions:</summary>

```python
def intersection(set_a: set, set_b: set) -> set:
    """Finds the intersection of two sets."""

    return set_a.intersection(set_b)

print(intersection({1, 2, 3}, {2, 3, 4}))
print(intersection({'a', 'b', 'c', 'd'}, {'c', 'c', 'd'}))
print(intersection({'White', 'Black', 'Red', 'Green'}, {'Black', 'Black', 'Yellow'}))
```

</details>

---

### 43.  Create a function that will accept the base and height of a triangle and compute the area. :writing_hand

Examples:

| Input | Output |
| --- | --- |
| `1, 2` | `1` |
| `2, 4` | `4` |
| `3, 8` | `12` |

<details>

<summary>Click here for solutions:</summary>

```python
def triangle_area(base: int, height: int) -> int:
    """Computes the area of a triangle."""

    return (base * height) // 2

print(triangle_area(1, 2))
print(triangle_area(2, 4))
print(triangle_area(3, 8))
```

</details>

---

### 44.  Create a function to compute the sum of three given integers. However, if any two values are equal, return zero

Examples:

| Input | Output |
| --- | --- |
|  `1, 2, 3`   |  `6`   |
|  `1, 1, 3`   |  `0`   |
| `1, 1, 1` | `0` |
| `2, 3, 2` | `0` |

<details>

<summary>Click here for solutions:</summary>

```python
# Solution 1
def sum_of_three(n1: int, n2: int, n3: int) -> int:
    """Computes sum of three integers."""

    if len({n1, n2, n3}) < 3:
        return 0
    return n1 + n2 + n3

# Solution 2
def sum_of_three(n1: int, n2: int, n3: int) -> int:
    """Computes sum of three integers."""

    return n1 + n2 + n3 if len({n1, n2, n3}) == 3 else 0

print(sum_of_three(1, 2, 3)) # 6
print(sum_of_three(1, 1, 3)) # 0
print(sum_of_three(1, 1, 1)) # 0
print(sum_of_three(2, 3, 2)) # 0
```

</details>

---

### 45.  Create a function to add two objects only if both objects are an integer type

If either of the two objects are not integers, your function should raise a custom `ValueError` exception with a message.

Examples:

| Input | Output |
| --- | --- |
| `10, 15` | `25` |
| `'a', 5` | `'Please use only integers with this function.'` |

<details>

<summary>Click here for solutions:</summary>

```python
# Solution 1
def two_ints(obj_1, obj_2) -> int:
    """Adds two objects together after making sure they are integers."""

    if isinstance(obj_1, int) and isinstance(obj_2, int):
        return obj_1 + obj_2
    else:
        raise ValueError('Please enter two integers.')

# Solution 2
def two_ints(obj_1, obj_2) -> int:
    """Adds two objects together after making sure they are integers."""

    if type(obj_1) == int and type(obj_2) == int:
        return obj_1 + obj_2
    else:
        raise ValueError('Please enter two integers.')

print(two_ints(10, 15))
print(two_ints('a', 5))

```

Keep in mind that the `isinstance()` function is not the desired method in most cases.

</details>

---

### 46.  Create a function to open a file and return all of its data. :writing_hand

You haven't gone over the lesson for opening files.  Do some googling and figure it out.

<details>

<summary>Click here for solutions:</summary>

```python
# Solution 1
def get_file(filename: str) -> str:
    """Opens a file and returns its content."""

    open(filename, 'r') as f:
        data = f.read()
    f.close()
    return data

# Solution 2
def get_file(filename: str) -> str:
    """Opens a file and returns its content."""

    with open(filename, 'r') as f:
        data = f.read()
    return data
```

Whenever opening files, always use the `with open()` convention.  It will automatically close the file for you after you are done.  Using the older method and forgetting to close a file after opening it can cause file corruption.

</details>

---

### 47.  Create a function to print all OS environment variable names in a list format. :writing_hand

Your output may differ from the example output below.

Example output:

```
['SSH_CONNECTION', 'LANG', 'which_declare', 'XDG_SESSION_ID', 'USER', 'SELINUX_ROLE_REQUESTED', 'PWD', 'SSH_ASKPASS', 'HOME', 'SSH_CLIENT', 'SELINUX_LEVEL_REQUESTED', 'XDG_DATA_DIRS', 'SHELL', 'SELINUX_USE_CURRENT_RANGE', 'SHLVL', 'VSCODE_AGENT_FOLDER', 'LOGNAME', 'DBUS_SESSION_BUS_ADDRESS', 'XDG_RUNTIME_DIR', 'PATH', 'LESSOPEN', 'BASH_FUNC_which%%', '_', 'VSCODE_HANDLES_SIGPIPE', 'HISTCONTROL', 'HOSTNAME', 'MAIL', 'PYTHONPATH', 'HISTSIZE', 'VSCODE_AMD_ENTRYPOINT', 'VSCODE_HANDLES_UNCAUGHT_ERRORS', 'VSCODE_NLS_CONFIG', 'BROWSER', 'VSCODE_CWD', 'ELECTRON_RUN_AS_NODE', 'VSCODE_IPC_HOOK_CLI', 'PYTHONUNBUFFERED', 'PYTHONIOENCODING', 'TERM', 'CLICOLOR', 'PAGER', 'GIT_PAGER', 'MPLBACKEND', 'PYDEVD_IPYTHON_COMPATIBLE_DEBUGGING']
```

<details>

<summary>Click here for solutions:</summary>

```python
import os

def get_environ():
    """Returns the current operating system environment variables."""

    return list(os.environ.keys())

print(get_environ())
```

</details>

---

### 48.  Execute a command in an OS shell

Create a function that sends a command to the OS that will print 'hello world' to the stdout.

<details>

<summary>Click here for solutions:</summary>

```python
import os

def hello_world():
    """Uses the OS to print a command."""

    os.system('cmd /k "echo Hello World!"')

hello_world()
```

</details>

---

### 49.  Create a function to parse a string to find integers

Given a string of both alphabetic and numeric characters, create a list consisting of only the numeric characters. The resulting list should not contain duplicates.

Examples:

| Input | Output |
| --- | --- |
| `'abc123'` | `['1', '3', '2']` |
| `'abc123abc123'` | `['1', '3', '2']` |
| `'abcdef'` | `[]` |
| `'11223344'` | `['1', '2', '3', '4']` |

<details>

<summary>Click here for solutions:</summary>

```python
# Solution 1
def find_numbers(string: str) -> list:
    """Parses a string and finds every unique integer."""

    nums = []
    for char in string:
        if char.isdigit() and char not in nums:
            nums.append(char)

    return nums

# Solution 2
def find_numbers(string: str) -> list:
    """Parses a string and finds every unique integer."""

    nums = set()
    for char in string:
        if char.isdigit():
            nums.add(char)

    return list(nums)  

# Solution 3
def find_numbers(string: str) -> list:
    """Parses a string and finds every unique integer."""

    nums = { char for char in string if char.isdigit() }
    return list(nums)

print(find_numbers('abc123'))
print(find_numbers('abc123abc123'))
print(find_numbers('abcdef'))
print(find_numbers('11223344'))

```

Solution 3 uses a set comprehension to quickly build a set of all the unique integers in the string.  

</details>

---

### 50.  Create a function that removes all whitespace from a given string. :writing_hand

Use the following input to test your function.

Input:

```python
"""
BARNARDO Who’s there?
FRANCISCO Nay, answer me. Stand and unfold yourself.
BARNARDO Long live the King!
FRANCISCO Barnardo?
BARNARDO He.
FRANCISCO You come most carefully upon your hour.
BARNARDO ’Tis now struck twelve. Get thee to bed, Francisco.
FRANCISCO For this relief much thanks. ’Tis bitter cold, And I am sick at heart.
BARNARDO Have you had quiet guard?
FRANCISCO Not a mouse stirring.
BARNARDO Well, good night.  If you do meet Horatio and Marcellus, The rivals of my watch, bid them make haste.
Enter Horatio and Marcellus.
FRANCISCO I think I hear them.—Stand ho! Who is there?
HORATIO Friends to this ground.
MARCELLUS And liegemen to the Dane.
FRANCISCO Give you good night.
MARCELLUS O farewell, honest soldier. Who hath relieved you?
FRANCISCO Barnardo hath my place. Give you good night.
"""
```

Expected output:

```
BARNARDOWho’sthere?FRANCISCONay,answerme.Standandunfoldyourself.BARNARDOLonglivetheKing!FRANCISCOBarnardo?BARNARDOHe.FRANCISCOYoucomemostcarefullyuponyourhour.BARNARDO’Tisnowstrucktwelve.Gettheetobed,Francisco.FRANCISCOForthisreliefmuchthanks.’Tisbittercold,AndIamsickatheart.BARNARDOHaveyouhadquietguard?FRANCISCONotamousestirring.BARNARDOWell,goodnight.IfyoudomeetHoratioandMarcellus,Therivalsofmywatch,bidthemmakehaste.EnterHoratioandMarcellus.FRANCISCOIthinkIhearthem.—Standho!Whoisthere?HORATIOFriendstothisground.MARCELLUSAndliegementotheDane.FRANCISCOGiveyougoodnight.MARCELLUSOfarewell,honestsoldier.Whohathrelievedyou?FRANCISCOBarnardohathmyplace.Giveyougoodnight.
```

<details>

<summary>Click here for solutions:</summary>

```python
def rem_space(string: str) -> str:
    """Removes all whitespace from the given string."""

    result = string.replace(' ', '').replace('\n', '')
    return result

some_string = """BARNARDO Who’s there?
FRANCISCO Nay, answer me. Stand and unfold yourself.
BARNARDO Long live the King!
FRANCISCO Barnardo?
BARNARDO He.
FRANCISCO You come most carefully upon your hour.
BARNARDO ’Tis now struck twelve. Get thee to bed, Francisco.
FRANCISCO For this relief much thanks. ’Tis bitter cold, And I am sick at heart.
BARNARDO Have you had quiet guard?
FRANCISCO Not a mouse stirring.
BARNARDO Well, good night.  If you do meet Horatio and Marcellus, The rivals of my watch, bid them make haste.
Enter Horatio and Marcellus.
FRANCISCO I think I hear them.—Stand ho! Who is there?
HORATIO Friends to this ground.
MARCELLUS And liegemen to the Dane.
FRANCISCO Give you good night.
MARCELLUS O farewell, honest soldier. Who hath relieved you?
FRANCISCO Barnardo hath my place. Give you good night."""

print(rem_space(some_string))
```

</details>

---

### 51.  Write a python program to access environment variables

In your Linux Bash terminal, create an environment variable of your choosing.  Then, create a Python function that can display the value of any environment variable and test it on the environment variable you just made.

<details>

<summary>Click here for solutions:</summary>

In Linux:

```bash
export SOMEVAR=TEST
echo $SOMEVAR
TEST
```

```python
import os

def get_var(env_var: str) -> str:
    """Returns the value of a specific environment variable."""

    return os.environ.get(env_var)

print(get_var())
```

</details>

---

### 52.  Create a function to return your computer's hostname. :writing_hand

<details>

<summary>Click here for solutions:</summary>

```python
import socket

def get_hostname() -> str:
    """Returns the host machine hostname."""

    return socket.gethostname()

print(get_hostname())
```

</details>

---

### 53.  Write a Python function to return your host machine's IP address using Python's standard library. :writing_hand

<details>

<summary>Click here for solutions:</summary>

```python
import socket

def get_ip() -> str:
    """Returns the host machine's IP address."""

    hostname = socket.gethostname()
    ip = socket.gethostbyname(hostname)
    return ip


print(get_ip())
```

</details>

---

### 54.  Create a function to calculate the hypotenuse of a right angled triangle

Your function should accept the two shortest sides of a triangle as input, and return the hypotenuse represented as an integer.  For this exercise, assume the triangle is right angled.

**Pythagoras Theorem Formula:** Hypotenuse<sup>2</sup> = Perpendicular<sup>2</sup> + Base<sup>2</sup>

>Hint: you can use a function from the `math` module that calculates square roots.

Examples:

| Input | Output |
| --- | --- |
| `3, 4` | `5` |
| `5, 12` | `13` |
| `7, 24` | `25` |

<details>

<summary>Click here for solutions:</summary>

```python
from math import sqrt

def find_hyp(side_1: int, side_2: int) -> float:
    """Returns the length of the hypotenuse of a given right triangle."""

    return int(sqrt(side_1**2 + side_2**2))

print(find_hyp(3, 4)) # 5.0
print(find_hyp(5, 12)) # 13.0
print(find_hyp(7, 24)) # 25.0
```

</details>

---

### 55.  Create a function to convert a distance (in feet) to miles, yards, and inches.:writing_hand

You are **not** calculating three values that are all the same distance.  All three measures, miles, yard and feed, should _combine together_ to equal the original distance.  

Return the values in dictionary format.

For example:

Input: 10,000 feet

1. The distance is large enought to fit one mile, so we add 1 to the `'miles'` key in our dictionary and subtract 5280 from our original distance.

2. We have 4720 feet remaining.  This distance would fit 1573 yards, so we add that to the `'yards'` value and then we are left with a distance of 1 foot.

3. Since we can't use feet in our result, we convert the last foot into inches, giving us 12 inches.

1 mile + 1573 yards + 12 inches == 10,000 feet.

Therefore, our function would return the following dictionary:

```python
{
    'miles': 1,
    'yards': 1573,
    'inches': 12
}
```

Here's another example:

Input: 8000 feet

Output:

```python
{
    'miles': 1,
    'yards': 906,
    'inches': 24
}
```

<details>

<summary>Click here for solutions:</summary>

```python
# Solution 1
def breakdown(distance: int) -> dict:
    """Converts a distance in total feet to miles, yards, and inches."""

    miles, remaining = distance // 5280, distance % 5280
    yards, remaining = remaining // 3, remaining % 3
    inches = remaining * 12
    return {
        'miles': miles,
        'yards': yards,
        'inches': inches
    }

# Solution 2
def breakdown(distance: int) -> dict:
    """Converts a distance in total feet to miles, yards, and inches."""
    miles, remaining = divmod(distance, 5280)
    yards, remaining = divmod(remaining, 3)
    inches = remaining * 12
    return {
        'miles': miles,
        'yards': yards,
        'inches': inches
    }

print(breakdown(10000))
print(breakdown(8000))
```

Solution 2 shows how the `divmod()` function can come in handy.  The `divmod()` function can divide one number by another, and return both the quotient as well as the remainder.

</details>

---

### 56.  Create a function to compute a distance in feet :writing_hand

Create a function that does the opposite of what you did in the last exercise.  Meaning, the function should take in a dictionary with miles, yards, and inches, and convert the distance to feet.  You can assume that the value for inches will always be in increments of 12, i.e. feet.

Examples:

| Input | Output |
| --- | --- |
| `{'miles': 2, 'yards': 100, 'inches': 24}` | `10862` |
| `{'miles': 3, 'yards': 69, 'inches': 36}` | `16050` |
| `{'miles': 1, 'yards': 500, 'inches': 12}` | `6781` |

<details>

<summary>Click here for solutions:</summary>

```python
# Solution 1
def total_distance(distances: dict) -> int:
    """Converts miles, yards, and inches into a total distance in feet."""

    multipliers = [5280, 3, (1/12)]

    return sum([
        int(distance * multiplier)
        for distance, multiplier
        in zip(distances.values(), multipliers)
    ])

# Solution 2
def total_distance(distances: dict) -> int:
    """Converts miles, yards, and inches into a total distance in feet."""

    m = 5280 * distances['miles']
    y = 3 * distances['yards']
    i = distances['inches'] // 12

    return m + y + i

print(total_distance({'miles': 2, 'yards': 100, 'inches': 24}))
print(total_distance({'miles': 3, 'yards': 69, 'inches': 36}))
print(total_distance({'miles': 1, 'yards': 500, 'inches': 12}))
```

This is an example where a more complicated solution just muddies the waters.  Solution 1 works, but the logic and code is convoluted.  Solution 2 is much simplier and easier to read.

</details>

### 57.  Create a function to convert a total number of seconds to days, hours, minutes and seconds. :writing_hand

Your function should accept a number representing an amount of time represented by a number of seconds. It should then return a dictionary containing keys that represent the original time converted to days, hours, minutes, _and_ seconds.  Just like the previous distances exercises, the days, hours, minutes, and seconds values should all add up to the original amount of time.

For example, given a total time of 86500 seconds, this would break down to:

1 day, 0 hours, 1 minute and 40 seconds, which formatted as a dictionary would look like this: `{'days': 1, 'hours': 0, 'minutes': 1, 'seconds': 40}`

Another example:

Input: `40000`

Output: `{'days': 0, 'hours': 11, 'minutes': 6, 'seconds': 40}`

<details>

<summary>Click here for solutions:</summary>

```python
# Solution 1
def time_breakdown(time: int) -> dict:
    """Converts a total time in seconds to days, hours, minutes, and seconds."""

    days, remaining = time // 86400, time % 86400
    hours, remaining = remaining // 3600, remaining % 3600
    minutes, remaining = remaining // 60, remaining % 60
    return {
        'days': days,
        'hours': hours,
        'minutes': minutes,
        'seconds': remaining
    }

# Solution 2
def time_breakdown(time: int) -> dict:
    """Converts a total time in seconds to days, hours, minutes, and seconds."""

    days, remaining = divmod(time, 86400)
    hours, remaining = divmod(remaining, 3600)
    minutes, remaining = divmod(remaining, 60)
    return {
        'days': days,
        'hours': hours,
        'minutes': minutes,
        'seconds': remaining
    }

print(time_breakdown(86500))
print(time_breakdown(40000))
```

</details>

---

### 58.  Create a function to return the name of every function from the math module

Expected output:

```
['__doc__', '__loader__', '__name__', '__package__', '__spec__', 'acos', 'acosh', 'asin', 'asinh', 'atan', 'atan2', 'atanh', 'ceil', 'comb', 'copysign', 'cos', 'cosh', 'degrees', 'dist', 'e', 'erf', 'erfc', 'exp', 'expm1', 'fabs', 'factorial', 'floor', 'fmod', 'frexp', 'fsum', 'gamma', 'gcd', 'hypot', 'inf', 'isclose', 'isfinite', 'isinf', 'isnan', 'isqrt', 'lcm', 'ldexp', 'lgamma', 'log', 'log10', 'log1p', 'log2', 'modf', 'nan', 'nextafter', 'perm', 'pi', 'pow', 'prod', 'radians', 'remainder', 'sin', 'sinh', 'sqrt', 'tan', 'tanh', 'tau', 'trunc', 'ulp']
```

<details>

<summary>Click here for solutions:</summary>

```python
import math

def get_details():
    """Returns every function from the math module."""
    
    return dir(math)

print(get_details())
```

</details>

---

### 59.  Create a function that returns the base64 encoded version of a string. :writing_hand

Examples:

| Input | Output |
| --- | --- |
| `'hello'` | `b'aGVsbG8='` |
| `'world'` | `b'd29ybGQ='` |
| `'username:password'` | `b'dXNlcm5hbWU6cGFzc3dvcmQ='` |

>Note: Whenever you see a Python string with a character denoted in front of the string, in this case `b`, this denotes the type of string.  There are a few different string types in Python.  You've already worked with f-strings (denoted with `f`), but there are also raw type strings (`r`), byte type strings (`b`), and many others.  

<details>

<summary>Click here for solutions:</summary>

```python
from base64 import b64encode

def to_byte(word: str) -> str:
    """base 64 encodes a given word."""

    byte_data = word.encode()
    return b64encode(byte_data)

print(to_byte('hello'))
print(to_byte('world'))
print(to_byte('username:password'))
```

</details>

---

### 60.  Create a function to find the available built-in modules

Example output:

```
('_abc', '_ast', '_bisect', '_blake2', '_codecs', '_codecs_cn', '_codecs_hk', '_codecs_iso2022', '_codecs_jp', '_codecs_kr', '_codecs_tw', '_collections', '_contextvars', '_csv', '_datetime', '_functools', '_heapq', '_imp', '_io', '_json', '_locale', '_lsprof', '_md5', '_multibytecodec', '_opcode', '_operator', '_pickle', '_random', '_sha1', '_sha256', '_sha3', '_sha512', '_signal', '_sre', '_stat', '_statistics', '_string', '_struct', '_symtable', '_thread', '_tracemalloc', '_warnings', '_weakref', '_winapi', '_xxsubinterpreters', 'array', 'atexit', 'audioop', 'binascii', 'builtins', 'cmath', 'errno', 'faulthandler', 'gc', 'itertools', 'marshal', 'math', 'mmap', 'msvcrt', 'nt', 'sys', 'time', 'winreg', 'xxsubtype', 'zlib') 
```

<details>

<summary>Click here for solutions:</summary>

```python
import sys

def get_builtins():
    """Returns all the built-in module names."""

    return sys.builtin_module_names

print(get_builtins())
```

</details>

---

### 61.  Create a function that returns the concatenated version of any number of strings

Your function will not be taking a list as input.  It will literally be taking any number of strings as input.  Use `*args` to account for the unknown number of arguments.  You may have to google `*args` and `**kwargs`.

Examples:

| Input | Output |
| --- | --- |
| `'abc', 'abc'` | `'abcabc'` |
| `'abc', 'abc', 'abc'` | `'abcabcabc'` |
| `'hello', ' ', 'world'` | `'hello world'` |

<details>

<summary>Click here for solutions:</summary>

```python
def combine(*args) -> str:
    """Concatenates any number of strings."""

    result = ''
    for arg in args:
        result += arg
    return result

print(combine('abc', 'abc'))
print(combine('abc', 'abc', 'abc'))
print(combine('hello', ' ', 'world'))
```

</details>

---

### 62.  Create a function to test whether all numbers of a list are greater than a certain number

Examples:

| Input | Output |
| --- | --- |
|  `[4, 5, 6], 3`   |   `True`  |
|  `[3, 4, 5], 3`   |   `False`  |
| `[1, 2, 3], 0` | `True` |

<details>

<summary>Click here for solutions:</summary>

```python
def is_greater(num_list: list, limit: int) -> bool:
    """Checks to see if every number in a list is greater than some other number."""

    for num in num_list:
        if num <= limit:
            return False
    return True

print(is_greater([4, 5, 6], 3))
print(is_greater([3, 4, 5], 3))
print(is_greater([1, 2, 3], 0))
```

</details>

---

### 63.  Create a function to return the number of occurrences of a specific character in a string

Examples:

| Input | Output |
| --- | --- |
| `'aaabbc', 'a'` | `3` |
| `'hello world', 'l'` | `3` |
| `'what\'s happening', 'h'` | `2` |

<details>

<summary>Click here for solutions:</summary>

```python
# Solution 1
def is_there(string: str, wanted: str) -> int:
    """Returns the number of occurrences of the character within a string."""

    count = 0
    for char in string:
        if char == wanted:
            count += 1
    return count

# Solution 2
def is_there(string: str, wanted: str) -> int:
    """Returns the number of occurrences of the character within a string."""

    return string.count(wanted)
```

</details>

---

### 64.  Create a function to return the ASCII value of a character

Every string character has an ASCII value equal to an integer. Create a function to return this ASCII value for a given character.

Your function should raise a `ValueError` exception with a custom message if more than a single character is received or if the character isn't alphabetic.

Examples:

| Input | Output |
| --- | --- |
| `'a'` | `97` |
| `'j'` | `106` |
| `'A'` | `65` |
| `'abc'` | `Please enter only a single letter in this function.` |
| `'1'` | `Please enter only a single letter in this function.` |

<details>

<summary>Click here for solutions:</summary>

```python
def get_ascii(char: str) -> int:
    """Returns the ascii value of a character."""

    if len(char) > 1 or not char.isalpha():
        raise ValueError('Please enter just a single letter.')
    return ord(char)

print(get_ascii('a'))
print(get_ascii('j'))
print(get_ascii('A'))
print(get_ascii('abc'))
```

</details>

---

### 65.  Create a function to convert a number to a binary string. :writing_hand

For this exercise, you can assume that the number will be no larger than 256.

Examples:

| Input | Output |
| --- | --- |
|  `12`   |  `'00001100'`   |
|   `144`  |  `'10010000'`   |
| `51` | `'00110011'` |

<details>

<summary>Click here for solutions:</summary>

```python
# Solution 1
def to_binary(num: int) -> str:
    """Converts a number to a binary string."""

    binary_factors = [128, 64, 32, 16, 8, 4, 2, 1]
    result = ''
    remainder = num

    for factor in binary_factors:
        quotient, remainder = divmod(remainder, factor)
        result += str(quotient)

    return result

# Solution 2
def to_binary(num: int) -> str:
    """Converts a number to a binary string."""

    return f'{num:08b}'

print(to_binary(12))
print(to_binary(144))
print(to_binary(51))
```

Solution 1 does things the way you might do this in your head.  For each binary factor, we divide the current remaining amount by that factor and save the quotient along with the remainder.  We add the quotient (which will always be a 0 or 1) to our result, and then perform the same logic on the new remainder.

Solution 2 uses formating within the f-string.  There are different formatting codes that you can use with f-string.  `08b` stands for 0-8 binary.  This means that it will fill in the string so that there are a certain number of zeros, in this case 8.  This would only come into play if we converted a number that was less than 128.  

</details>

---

### 66.  Create a function to return the system time in this format: HH:MM:SS. :writing_hand

Note : The system time is important for debugging, network information, random number seeds, or something as simple as program performance.

Example output: `14:35:19`

<details>

<summary>Click here for solutions:</summary>

```python
from datetime import datetime

def get_time() -> float:
    """Returns the system time in a certain format."""

    time = datetime.now()
    return f'{time.hour}:{time.minute}:{time.second}'

print(get_time())
```

</details>

---

### 67.  Create a function to extract the filename from a given _Windows_ file path

**Make sure to use raw strings (denoted with `r`).**

Examples:

| Input | Output |
| --- | --- |
| `r'C:\users\some_user\Desktop\stuff\my_file.txt'` | `my_file` |
| `r'C:\users\some_user\Documents\readme.md'` | `'readme'` |
| `r'C:\users\some_user\Pictures\vacation.jpeg'` | `'vacation'` |

Note: In the example inputs we are appending an `r` to the front of each string.  This tells Python to treat this as a raw string.  This means that escape characters (\\) are _ignored_.

<details>

<summary>Click here for solutions:</summary>

```python
def get_filename(path: str) -> str:
    """Returns the extension of a file in a given full file path."""
    
    levels = path.split('\\')
    filename, extension = levels[-1].split('.')
    return filename

print(get_filename(r'C:\users\some_user\Desktop\stuff\my_file.txt'))
print(get_filename(r'C:\users\some_user\Documents\readme.md'))
print(get_filename(r'C:\users\some_user\Pictures\vacation.jpeg'))
```

</details>

---

### 68.  Create a function that filters a list of numbers and returns only the even numbers  

Return the even numbers in a list.

Examples:

| Input | Output |
| --- | --- |
| `[1, 2, 3, 4, 5]` | `[2, 4]` |
| `[28, 47, 29, 30]` | `[28, 30]` |
| `[8, 29, 57, 29, 56]` | `[8, 56]` |

<details>

<summary>Click here for solutions:</summary>

```python
# Solution 1
def get_even(nums: list) -> list:
    """Gets even numbers from a list."""

    even = []
    for num in nums:
        if num % 2 == 0:
            even.append(num)
    return even

# Solution 2
def get_even(nums: list) -> list:
    """Gets even numbers from a list."""

    even = [ num for num in nums if num % 2 == 0 ]
    return even

print(get_even([1, 2, 3, 4, 5]))
print(get_even([28, 47, 29, 30]))
print(get_even([8, 29, 57, 29, 56]))
```

</details>

---

### 69.  Create a function to round a floating-point number to specified number decimal places. :writing_hand

Try not to use a built-in function.

When rounding, round up if the next decimal place is 5 or higher.  

Examples:

| Input | Output |
| --- | --- |
|  `3.125, 2`  |   `3.13`  |
|   `3.124, 2`  |   `3.12`  |
| `14.1555, 3` | `14.156` |

<details>

<summary>Click here for solutions:</summary>

```python
# Solution 1
def roundup(num: float, decimal_places: int) -> float:
    """Rounds a float to a given decimal place."""

    # Convert float to a string
    digits = str(num)

    # Split the string on the decimal point
    whole_number, decimal = digits.split('.')

    # Shorten the decimal portion of the string to get rid of decimal places we don't care about
    decimal = decimal[:decimal_places + 1]

    # Separate the desired decimal places with the last decimal place to use for rounding decision
    d1, d2 = int(decimal[:-1]), int(decimal[-1])

    # If the last decimal place is 5 or higher, round the previous decimal place up by 1
    if d2 >= 5:
        d1 += 1

    # Return a formatted string casted to a float
    return float(f'{whole_number}.{d1}')



    print(decimal)

def roundup(num: float, decimal_places: int) -> float:
    """Rounds a float to a given decimal place."""

    return round(num, decimal_places)
```

</details>

---

### 70.  Create a function to determine the minimum, maximum, and average of a given list of numbers.  Return these values in a dictionary format

Examples:

| Input | Output |
| --- | --- |
| `[1, 2, 3]` | `{'minimum': 1, 'maximum': 3, 'average': 2.0}` |
| `[3, 10, 15]` | `{'minimum': 3, 'maximum': 15, 'average': 9.333333333333334}` |
| `[23, 42, 89]` | `{'minimum': 23, 'maximum': 89, 'average': 51.333333333333336}` |

<details>

<summary>Click here for solutions:</summary>

```python
def metrics(nums: list) -> dict:
    """Returns various data points from a list."""

    minimum = min(nums)
    maximum = max(nums)
    average = sum(nums) / len(nums)

    return {'minimum': minimum, 'maximum': maximum, 'average': average}

print(metrics([1, 2, 3]))
print(metrics([3, 10, 15]))
print(metrics([23, 42, 89]))
```

</details>

---

### 71.  Create a function that can take any number of arguments and checks whether or not they all have the same type

Examples:

| Input | Output |
| --- | --- |
| `1, 2, 3` | `True` |
| `1, 2, '3'` | `False` |
| `'1', '2', '3'` | `True` |

<details>

<summary>Click here for solutions:</summary>

```python
# Solution 1
def all_same_type(*args) -> bool:
    """Checks if all args have same type."""

    types = { type(arg) for arg in args }
    if len(types) == 1:
        return True
    else:
        return False

# Solution 2
def all_same_type(*args) -> bool:
    """Checks if all args have same type."""

    types = { type(arg) for arg in args }
    return len(types) == 1:


print(all_same_type(1, 2, 3)) # True
print(all_same_type(1, 2, '3')) # False
print(all_same_type('1', '2', '3')) # True
```

</details>

---

### 72.  Create a function to check whether lowercase letters exist in a string

Examples:

| Input | Output |
| --- | --- |
| `'hello'` | `True` |
| `'HELLO'` | `False` |
| `'world'` | `True` |
| `'wORLD'` | `True` |

<details>

<summary>Click here for solutions:</summary>

```python
# Solution 1
def contains_lowercase(string: str) -> bool:
    """Checks to see if a string has any lowercase letters."""

    for char in string:
        if char.islower():
            return True
    return False

# Solution 2
def contains_lowercase(string: str) -> bool:
    """Checks to see if a string has any lowercase letters."""

    lower_chars = [char for char in string if char.islower() ]
    return bool(lower_chars)

# Solution 3
def contains_lowercase(string: str) -> bool:
    """Checks to see if a string has any lowercase letters."""

    booleans = [ char.islower() for char in string ]
    return any(booleans)


print(contains_lowercase('Hello world'))
print(contains_lowercase('HELLO WORLD'))

```

Solution 2 creates a list of the lowercase characters, and then returns the boolean value of the list.  As long as the list is not empty, the boolean value will be True.

Solution 3 uses the `any()` function.  The `any()` function takes in a _list of boolean values_.  We use a list comprehension with the `.islower()` function to create a list of boolean values that we can pass to the `any()` function.  As it sounds, `any()` will return True if any of the items in the supplied list evaluate to True.  

</details>

---

### 73.  Create a function to add a specified number of leading zeroes to a string

Examples:

| Input | Output |
| --- | --- |
| `'some_string', 3` | `'000some_string` |
| `'some_string', 1` | `0some_string` |
| `'some_string', 5` | `00000some_string` |

<details>

<summary>Click here for solutions:</summary>

```python
def add_leading_zeroes(string: str, no_of_zeroes: int) -> str:
    """Inserts 0's to a number."""

    return '0' * no_of_zeroes + string

```

</details>

---

### 74.  Create a function to convert True to 1 and False to 0

<details>

<summary>Click here for solutions:</summary>

```python
# Solution 1
def to_digit(input: bool) -> int:
    """Converts a boolean to an integer."""

    if input == True:
        return 1
    return 0

# Solution 2
def to_digit(input: bool) -> int:
    """Converts a boolean to an integer."""

    if input:
        return 1
    return 0

# Solution 3
def to_digit(input: bool) -> int:
    """Converts a boolean to an integer."""

    return int(input)

print(to_digit(True))
print(to_digit(False))
```

In solution 3 we actually cast the boolean into an integer, which does the job.  Just like we can convert an integer into a boolean by casting it with the `bool()` function, we can actually convert a boolean into an integer by casting it with the `int()` function.

</details>

---

### 75.  Create a list of the powers of 2

Create a function that takes in an integer N, and returns a list of the powers of two, up to 2<sup>N</sup>.

Examples:

| Input | Output |
| --- | --- |
| `5` | `[2, 4, 6, 8, 16, 32]` |
| `12` | `[2, 4, 8, 16, 32, 64, 128, 256, 512, 1024, 2048, 4096]` |
| `13` | `[2, 4, 8, 16, 32, 64, 128, 256, 512, 1024, 2048, 4096, 8192]` |

<details>

<summary>Click here for solutions:</summary>

```python
# Solution 1
def powers_of_two(number: int) -> list:
    """Returns all powers of 2 up to a given power."""

    result = []
    for power in range(1, number + 1):
        result.append(2**power)

    return result

# Solution 2
def powers_of_two(number: int) -> list:
    """Returns all powers of 2 up to a given power."""

    return [2**power for power in range(1, number + 1)]

print(powers_of_two(5))
print(powers_of_two(12))
print(powers_of_two(13))

```

Solution 2 does the same thing as solution 1, but it just uses a list comprehension.

</details>

---

### 76.  Create a function to validate an IP address. :writing_hand

The function should check these requirements:

* there are 4 octets
* all octets fall between 1 and 255
* there are no leading zeroes.

It should also return false if the loopback IP address is given (127.0.0.1).

Examples:

| Input | Output | Logic |
| --- | --- | --- |
| `'192.168.1.1'` | `True` | Meets all criteria |
| `'192.168.001.001'` | `False` | Leading zeros |
| `'192.168.1'` | `False` | Only three octets |
| `'192.168.255.401'` | `False` | Last octet is over 255 |
| `'127.0.0.1'` | `False` | Standard loopback address |

<details>

<summary>Click here for solutions:</summary>

```python
def is_ip(address: str) -> bool:
    """Checks for valid IP address."""

    octets = address.split('.')

    if len(octets) < 4 or address == '127.0.0.1':
        return False

    for octet in octets:
        if not 1 <= int(octet) <= 255 or octet.lstrip('0') != octet:
            return False
    return True

print(is_ip('192.168.1.1'))
print(is_ip('192.168.001.001'))
print(is_ip('192.168.1'))
print(is_ip('192.168.255.401'))
print(is_ip('127.0.0.1'))
```

In general, this solution only looks for cases that would return False.  If none of these cases are hit, then the function returns True by default.

</details>

---

### 77.  Create a function to convert a binary string to an integer.:writing_hand

For this exercise, you can assume the string will have a maximum of 8 characters.

Examples:

| Input | Output |
| --- | --- |
| `'00001100'` | `12` |
| `'10101010'` | `170` |
| `'11001011'` | `203` |
<details>

<summary>Click here for solutions:</summary>

```python
# Solution 1
def to_int(binary_string: str) -> int:
    """Converts a binary string into an integer."""

    binary_factors = [2**power for power in range(7,-1,-1)] # don't do it this way in production.  this is just for demonstation.

    result = 0
    for factor, char in zip(binary_factors, binary_string):
        result += int(char) * factor

    return result

# Solution 2
def to_int(binary: str) -> int:
    """Converts a binary string into an integer."""

    try:
        return int(binary, base=2)
    except ValueError:
        print(f'The string {binary} is not proper binary.')

print(to_int('00001100'))
print(to_int('10101010'))
print(to_int('11001011'))
```

</details>

---

### 78.  Write a python program to convert decimal to hexadecimal. :writing_hand

Examples:

| Input | Output |
| --- | --- |
| `30` | `0x1E` |
| `4` | `0x4` |
| `150` | `0x96` |
| `212` | `0xd4` |

In order to convert a decimal to hexadecimal, continually divide the number by 16, each time keeping the remainder that you receive.

Once you cannot divide by 16 any more, go backwards through each remainder and convert each one to hex.

For example, if given the number 960:

1. Continually divide by 16, keeping note of the remainder each time.

    * 960 // 16 = 60 remainder 0

    * 60 // 16 = 3 remainder 12

    * 3 // 16 = 0 remainder 3

2. Go backwards through the remainders and convert each to hex:
    * 3 = 3
    * 12 = C
    * 0 = 0

3. Combine the hex characters to get the completed version:

`'3C0'`

4. For proof, we can create a hexadecimal value in a Python terminal by using the prefix `0x`:

```
>>> a = 0x3C0
>>> a
960
>>>
```

<details>

<summary>Click here for solutions:</summary>

```python
# Solution 1
def to_hex(num: int) -> int:
    """Converts a decimal number to hex."""

    hex_chars = {
        10: 'A',
        11: 'B',
        12: 'C',
        13: 'D',
        14: 'E',
        15: 'F'
    }

    # Continually divide by 16 and save remainders in a list
    remainders = []
    while num != 0:
        num, remainder = divmod(num, 16)
        remainders.append(remainder)

    # Convert each individual remainder into hexadecimal and append to a string
    result = ''

    # Loop through each remainder backwards
    for remainder in remainders[::-1]:

        # If the remainder is greater than 9, consult our dictionary above to find the appropriate value
        if remainder > 9:
            result += hex_chars[remainder]
        else:
            result += str(remainder)

    return '0x' + result

# Solution 2    
def to_hex(num: int) -> int:
    """Converts a decimal number to hex."""

    return hex(num)

print(to_hex(960))
```

</details>

---

### 79.  Write a python function to convert a binary string to a hexadecimal character

For this exercise, you can assume the binary string will 8 characters long.

You can use the function you created in the previous exercise.

To convert a binary number to a hexadecimal number:

1. Convert the binary to decimal

2. Convert the decimal to hexadecimal

Alternatively:

1. Separate the binary number into nibbles (4 byte pieces)

2. Convert each nibble into a hex character

Examples:

| Input | Output |
| --- | --- |
| `'00001100'` | `0xC` |
| `'10101010'` | `0xAA` |
| `'11000011'` | `0xC3` |

<details>

<summary>Click here for solutions:</summary>

```python
# Solution 1
def binary_to_hex(binary_str: str) -> int:
    """Converts a binary string into a hex number."""

    # Use a previously created function to convert the binary string into a decimal number.
    decimal_number = to_int(binary_str)

    # Use a previously created function to turn the decimal number into hex.
    return to_hex(decimal_number)

# Solution 2
def binary_to_hex(binary_str: str) -> int:
    """Converts a binary string into a hex number."""

    decimal_number = int(binary_str, base=2)
    return hex(decimal_number)

print(binary_to_hex('00001100'))
print(binary_to_hex('10101010'))
print(binary_to_hex('11000011'))
```

Solution 1 just leverages previously made functions to accomplish the two major steps of converting a binary string to a hex value.

Solution 2 shows how you could leverage built-in functions to do the same thing.

</details>

---

### 80.  Create a function to compute the greatest common divisor (GCD) of two positive integers

>Note: the greatest common divisor is also called the greatest common factor.

Examples:

| Input | Output |
| --- | --- |
| `60, 48` | `12` |
| `15, 21` | `3` |
| `12, 36` | `12` |

<details>

<summary>Click here for solutions:</summary>

```python
# Solution 1
def gcd(num_1: int, num_2: int) -> int:
    """Computes the greatest common divisor of two numbers."""

    # Find all factors of first number
    num_1_factors = []
    for possible_factor in range(1, num_1 + 1):
        if num_1 % possible_factor == 0:
            num_1_factors.append(possible_factor)

    # Find all factors of second number
    num_2_factors = []
    for possible_factor in range(1, num_2 + 1):
        if num_2 % possible_factor == 0:
            num_2_factors.append(possible_factor)

    # Find common factors
    common_factors = []
    for factor in num_1_factors:
        if factor in num_2_factors:
            common_factors.append(factor)

    return max(common_factors)

# Solution 2
def gcd(num_1: int, num_2: int) -> int:
    """Computes the greatest common divisor of two numbers."""

    num_1_factors = [ possible_factor for possible_factor in range(1, num_1 + 1) if num_1 % possible_factor == 0 ]

    num_2_factors = [ possible_factor for possible_factor in range(1, num_2 + 1) if num_2 % possible_factor == 0 ]

    common_factors = [ factor for factor in num_1_factors if factor in num_2_factors ]

    return max(common_factors)

# Solution 3
def gcd(num_1: int, num_2: int) -> int:
    """Computes the greatest common divisor of two numbers."""

    lower = num_1 if num_1 < num_2 else num_2

    common_factors = [num for num in range(1, lower + 1) if num_1 % num == 0 and num_2 % num == 0]

    return max(common_factors)

print(gcd(60, 48)) # 12
print(gcd(15, 21)) # 3
print(gcd(12, 36)) # 12

```

Solution 2 is the same thing as solution 1, except it does the same thing with list comprehensions.

Solution 3 goes straight to computing the common factors.  It first finds the lower of the two numbers, and loops through each number from 2 up until that number.  For each iteration, it checks to see if it is a factor of each of the inputted numbers.

</details>

---

### 81.  Create a function to get the least common multiple (LCM) of two positive integers

Examples:

| Input | Output |
| --- | --- |
| `4, 5` | `20` |
| `4, 10` | `20` |
| `3, 4` | `12` |
| `5, 12` | `60` |
| `3, 17` | `51` |

<details>

<summary>Click here for solutions:</summary>

```python
def lcm(n1: int, n2: int) -> int:
    """Computes the lowest common multiple of two positive integers."""

    lower_number, higher_number = (n1, n2) if n1 > n2 else (n2, n1)
    for num in range(1, lower_number + 1):
        if (higher_number * num) % lower_number == 0:
            return higher_number * num

print(lcm(4, 5))
print(lcm(4, 10))
print(lcm(3, 4))
print(lcm(5, 12))
print(lcm(3, 17))
```

</details>

---

### 82.  Create a function to time different built-in methods :writing_hand:  :writing_hand

First, create a function that takes in no arguments and calculates the sum of all numbers from 1 to 100,000,000.  Do not use the built-in `sum()` function and do not worry about returning any data yet.

Second, create another function that uses the `sum()` function to do the same thing.

Lastly, edit each of your functions so that they return the execution time required to calculate the sum.  You can use the `perf_counter()` function from the `time` module.

The `perf_counter()` method returns a current timestamp represented as a float.  Simply create two points in time, one before and one after, and find the difference to calculate the execution time.

For example:

```python
>>> from time import perf_counter
>>> t1 = perf_counter()
>>> t2 = perf_counter()
>>> t2 - t1
3.0639061000001675
```

Run each of your functions a few times and take note of the time difference.  
<details>

<summary>Click here for solutions:</summary>

```python
from time import perf_counter

def add_nums_1() -> float:
    """finds sum of all numbers up to a big one."""

    t1 = perf_counter()
    sum = 0
    for num in range(100000000):
        sum += num
    t2 = perf_counter()
    return t2 - t1

def add_nums_2() -> float:
    """finds sum of all numbers up to a big one."""

    t1 = perf_counter()
    x = sum(range(100000000))
    t2 = perf_counter()
    return t2 - t1

print(add_nums_1())
print(add_nums_2())

```

While minimal, you can see that the `sum()` built-in function is always faster.  This is because this built-in function is actually written in the compiled ***C language***.  The python interpreter actually leverages this compiled code to execute built-in functions much faster.  **Always use built-in functions whenever possible.**

</details>

---

### 83.  Create a function to check if every consecutive sequence of zeroes is followed by a consecutive sequence of ones of same length in a given string

Return True/False.

You can assume that the sequences will always start with zeroes.

Examples:

| Input | Output | Logic |
| --- | --- | --- |
| `01010101` | `True` | Every single 0 is followed by a single 1 |
| `00` | `False` | The two 0's should have been followed by two 1's |
| `000111000111` | `True` | Each three 0's is followed by three 1's |
| `00011100011` | `False` | The last group of three 0's is followed by only two 1's |
| `0001100111` | `False` | The first group of three 0's is followed by only two 1's |

<details>

<summary>Click here for solutions:</summary>

```python
import re

def is_consecutive(sequence: str) -> bool:
    """Checks to see if every sequence of 0's is matched by a sequence of equal 1's."""

    matches = re.findall("0+1+", sequence)
    if len(matches) > 0:
        for match in matches:
            if match.count('0') != match.count('1'):
                return False
        return True
    return False

print(is_consecutive('01010101'))
print(is_consecutive('00'))
print(is_consecutive('000111000111'))
print(is_consecutive('00011100011'))
print(is_consecutive('0001100111'))
```

This solution leverages the Python regex module (re).  Regex isn't covered in this course, but it is an extremely powerful tool when parsing strings.

</details>

---
```