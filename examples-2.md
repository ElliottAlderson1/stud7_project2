```markdown
### 1.  Write a Python function that takes a list of numbers and determines whether all the numbers are different from each other

Examples:

| Input | Output |
| --- | --- |
| `[1, 2, 3]` | `True` |
| `[1, 1, 2]` | `False` |
| `[1, 1, 1]` | `False` |

<details>

<summary>Click here for solutions:</summary>

```python
def is_unique(nums: list ) -> bool:
    """Determines if all numbers in a list of numbers are unique."""

    unique_nums = []
    for num in nums:
        if num not in unique_nums:
            unique_nums.append(num)

    return len(nums) == len(unique_nums)

# Solution 2
def is_unique(nums: list) -> bool:
    """Determines if all numbers in a list of numbers are unique."""

    return len(nums) == len(set(nums))
```

</details>

---

### 2.  Old Fashioned Texting

Remember trying to text on an older cell phone?  You'd have to press a number multiple times to select a certain letter.

Create a function to convert a string into number presses on an old cell phone.  Separate each sequence by a hyphen.

Examples:

| Input | Output |
| --- | --- |
| `'hello world'` | `'44-33-555-555-666-0-9-666-777-555-3'` |
| `'idk my bff jill'` | `'444-3-55-0-6-999-0-22-333-333-0-5-444-555-555'` |
| `'she mad woke frfr'` | `'7777-44-33-0-6-2-3-0-9-666-55-33-0-333-777-333-777'` |

<details>

<summary>Click here for solutions:</summary>

```python
def texting(phrase: str) -> str:
    """Takes a phrase and tells you what numbers you'd have to press on an old cellphone to text the phrase."""

    keypad = {
        '2': 'abc',
        '3': 'def',
        '4': 'ghi',
        '5': 'jkl',
        '6': 'mno',
        '7': 'pqrs',
        '8': 'tuv',
        '9': 'wxyz',
        '0': ' '
    }

    sequences = []
    for letter in phrase:
        for number, letters in keypad.items():
            if letter in letters:
                sequences.append(number * (letters.index(letter) + 1))

    return '-'.join(sequences)

```

</details>

---

### 3.  Create a function to check if three lengths of a triangle are a pythagorean triple

A pythagorean triple is three numbers, representing three lengths of a triangle, that fit this formula: a<sup>2</sup> + b<sup>2</sup> = c<sup>2</sup>, where c is the length of the longest side.

Create a function to check whether or not three lengths of a triangle (represented by integers) are a pythagorean triple.  Your function should be able to take the sides in any order.

Examples:

| Input | Output |
| --- | --- |
| `1, 2, 3` | `False` |
| `3, 4, 5` | `True` |
| `5, 12, 13` | `True` |

<details>

<summary>Click here for solutions:</summary>

```python
# Solution 1
def is_triple(s1: int, s2: int, s3:int) -> bool:
    """Checks to see if three given numbers are a pythagorean triple."""

    sorted_sides = sorted([s1, s2, s3])

    if s1**2 + s2**2 == s3**2:
        return True
    return False

# Solution 2
def is_triple(s1: int, s2: int, s3:int) -> bool:
    """Checks to see if three given numbers are a pythagorean triple."""

    sorted_sides = sorted([s1, s2, s3])

    return s1**2 + s2**2 == s3**2
```

The only difference between the two solutions is that in the second solution, we just put the conditional straight in our return statement.
Since comparisons always return booleans, we don't need to use if-else statements.

</details>

---

### 4.  Import the 'Zen of Python'

Tim Peters, a contributor to the styling standards of Python, created a list of coding principles called the 'Zen of Python'.  You can import and print these principles using a built-in module.

Do some googling and figure out how to import these principles.

<details>

<summary>Click here for solutions:</summary>

```python
import this
```

</details>

---

### 5.  Create a function to find the median among three given numbers

>Hint: In a data set consisting of three items, the median will always be the middle item.

Examples:

| Input | Output |
| --- | --- |
| `1, 2, 3` | `2` |
| `1, 6, 10` | `6` |
| `1, 3, 9` | `3` |

<details>

<summary>Click here for solutions:</summary>

```python
def find_med(s1: int, s2: int, s3: int) -> int:
    """Returns the median of three numbers."""

    sorted_nums = sorted([s1, s2, s3])
    return sorted_nums[1]
```

</details>

---

### 6.  Create a function to compare two lists

Your function should take two lists as input and compute the sum of the N<sup>th</sup> index of each list.

You can assume that each list will have the same number of items.

Examples:

| Input | Output |
| --- | --- |
| `[1, 2, 3], [4, 5, 6]` | `[5, 7, 9]` |
| `[2, 4, 6], [1, 3, 5]` | `[3, 7, 11]` |
| `[5, 2, 9], [2, 4, 2]` | `[7, 6, 11]` |

<details>

<summary>Click here for solutions:</summary>

```python
# Solution 1
def sum_lists(l1: list, l2: list) -> list:
    """Adds each successive index of two lists."""

    result = []
    for index in range(len(l1)):
        result.append(l1[index] + l2[index])

    return result

# Solution 2
def sum_lists(l1: list, l2: list) -> list:
    """Adds each successive index of two lists."""

    result = []
    for a, b in zip(l1, l2):
        result.append(a + b)

    return result

# Solution 3
def sum_lists(l1: list, l2: list) -> list:
    """Adds each successive index of two lists."""

    return [a + b for a, b in zip(l1, l2)]

```

The second solution uses a handy function called `zip()`.  The zip function takes any number of iterables as input and loops through each one simultaneously.  You must use a loop variable for each iterable you pass to zip.  In this case, we zipped through two lists, so we used two loop variables.

The third solution uses the same logic as solution 2, but just in a list comprehension.

</details>

---

### 7.  Create a function to reverse the digits of a given number and add it to the original

Examples:

| Input | Logic | Output |
| --- | --- | --- |
|  `21`   |  21 + 12   | `33` |
|   `32`  |  32 + 23   | `55` |
| `123` | 123 + 321  | `444` |

<details>

<summary>Click here for solutions:</summary>

```python
def rev_sum(num: int) -> int:
    """Reverses a number and adds it to the original."""

    reversed_num = str(num)[::-1]
    return int(reversed_num) + num
```

This solution creates a variable called `reversed_num` set equal to the provided number casted to a string and then sliced with a negative step count.  Then, the `return` statement just casts the new reversed number to an integer and adds it to the original number.

</details>

---

### 8.  Create a function to find the 3 largest numbers

Your function should take a list of numbers as input and return the three highest numbers in _descending_ order.

Examples:

| Input | Output |
| --- | --- |
| `[1, 2, 3, 4, 5]` | `[5, 4, 3]` |
| `[12, 29, 48, 32, 1]` | `[48, 32, 29]` |
| `[98, 38, 29, 3]` | `[98, 38, 29]` |

<details>

<summary>Click here for solutions:</summary>

```python
def top_3(nums: list) -> list:
    """Returns the 3 highest numbers in descending order."""

    sorted_nums = sorted(nums, reverse=True)
    return sorted_nums[:3]
```

</details>

---

### 9.  Create a function to return the number of prime numbers which are less than or equal to a given integer

1 is not a prime number.

Examples:

| Input | Prime numbers less than or equal to input | Output |
| --- | --- | --- |
|  `5`   | 2, 3, 5 | `3`   |
|   `10`  |  2, 3, 5, 7   | `4` |
| `13` | 2, 3, 5, 7, 11, 13 | `6` |

<details>

<summary>Click here for solutions:</summary>

```python
from sympy import isprime

# Solution 1
def lower_prime(limit: int) -> int:
    """Returns the number of prime numbers that are less than a given number."""

    prime_numbers = []
    for num in range(limit + 1):
        if isprime(num):
            prime_numbers.append(num)
    return len(prime_numbers)

# Solution 2
def lower_prime(limit: int) -> int:
    """Returns the number of prime numbers that are less than a given number."""

    prime_numbers = [ num for num in range(limit + 1) if isprime(num) ]
    return len(prime_numbers)
```

These solutions leverage a 3rd party module called sympy.  It has a convenient function that allows you to check if a number is prime.  If you made this code yourself, then that is fine too. This was just a demonstration of how you can save yourself time by using code that is already written.

</details>

---

### 10.  Create a function that given a number N, computes the sum of the first N number of prime numbers, starting with 2

Examples:

| Input | First N prime numbers | Output |
| --- | --- | --- |
|  `3`   | 2, 3, 5 | `10`   |
|   `4`  |  2, 3, 5, 7   | `17` |
| `6` | 2, 3, 5, 7, 11, 13 | `41` |

<details>

<summary>Click here for solutions:</summary>

```python
from sympy import isprime

def sum_of_prime(num: int) -> int:
    """Returns the sum of the first num number of prime numbers."""

    current = 2
    prime_numbers = []

    while len(prime_numbers) < num:
        if isprime(current):
            prime_numbers.append(current)
        current += 1

    return sum(prime_numbers)
```

</details>

---

### 11.  Create a function to reverse only the vowels of a given string

For this exercise, assume that all letters will be lowercase

Examples:

| Input | Output |
| --- | --- |
| `'zaeiz'` | `'zieaz'` |
|  `'w3resource'`   |   `'w3resuorce'`  |
|  `'python'`   |   `'python'`  |
|  `'perl'`   |   `'perl'`  |
|  `'usa'`   |  `'asu'`   |

<details>

<summary>Click here for solutions:</summary>

```python
def rev_vowels(string: str) -> str:
    """Returns the string with only vowels reversed."""

    # Converting the string to a list makes it easier to work with
    string = list(string)
    vowels = 'aeiou'
    indices = []
    matches = []

    # Create a list of vowels and their indices
    for i, char in enumerate(string):
        if char in vowels:
            indices.append(i)
            matches.append(char)

    # Update the new vowels in the indices
    for index, match in zip(indices, matches[::-1]):
        string[index] = match

    return ''.join(string)

    
```

</details>

---

### 12.  Create a function to check whether a given integer is a palindrome or not

Note: An integer is a palindrome when it reads the same backward as forward. Negative numbers are not palindromic because of the negative sign.

Examples:

| Input | Output |
| --- | --- |
|   `100`  |   `False`  |
|  `252`   | `True`    |
| `-838` | `False` |

<details>

<summary>Click here for solutions:</summary>

```python
def is_pal(num: int) -> bool:
    """Checks if a number is a palindrome."""

    return str(num) == str(num)[::-1]
```

</details>

---

### 13.  Have a user guess a random number

Create a function that picks a random number for a user to guess.  They will guess until they get it right.

The program should pick a random number between 1 and 10 and have the user repeatedly guess until they guess it correctly.

On each attempt, tell the user whether their guess is higher or lower to the actual number.

If they guess the number correctly, give them a congratulatory message and exit the function.

The user should be given an option to quit the program at any time.

Bonus points if you can print the messages in the output using colors.

>Important Note:  If you choose to use a while-loop in your function, keep in mind that you may have to avoid using a Jupyter notebook as they don't handle while-loops very well in certain situations.

<details>

<summary>Click here for solutions:</summary>

```python
from random import randint
from termcolor import colored

def guess_a_number():
    """Asks a user to guess a random number between 1 and 10."""

    # Choose a random number
    secret_num = randint(1, 10)
    print('\nI have chosen a random number between 1 and 10. Try to guess it. \nType "quit" to terminate this program at any time.\n')

    # Set the response to None in the beginning 
    response = None

    while True:

        # Check to see if response was set by previous iteration of loop.  If it was, then change the prompt presented to the user
        if response is not None:
            response = input('Please try again...\n')
        else:
            response = input('Please enter a guess...\n')

        # Check to see if player wanted to quit
        if response == 'quit':
            print('Thanks for playing.')
            break

        # Check value of response and tell the user how they did
        if int(response) != secret_num:
            print(colored(f'Your guess was {"lower" if int(response) < secret_num else "higher"} than the target number.', 'red'))
        else:
            print(colored(f'Congrats! you guessed the number correctly. It was {secret_num}', 'green'))
            break
```

In this solution we set the `response` variable to `None` initially.  This is so that we can give a certain prompt to the user on the first iteration of the loop, and then on subsequent iterations, we can give them a different prompt.

We can install and use the `termcolor` package to present colored messages in the terminal.  

In order to use this module, you will have to install it using the following command:

```
pip3 install termcolor --user
```

</details>

---

### 14.  Create a function to replace all but the last five characters of a given string with "*"

Examples:

| Input | Output |
| --- | --- |
|   `'kdi39323swe'`  |  `'******23swe'`   |
|  `'12345abcdef'`   |  `'******bcdef'`   |
| `'12345'` | `'12345'` |

<details>

<summary>Click here for solutions:</summary>

```python
def last_five(string: str) -> str:
    """Returns a string with all but the last 5 characters replaced with *."""

    length_of_stars = len(string) - 5
    return ('*' * length_of_stars) + string[-5:]
```

</details>

---

### 15.  Create a function to check whether every even index of a list contains an even number and every odd index contains odd number of a given list

Examples:

| Input | Output |
| --- | --- |
|  `[2, 1, 4, 3, 6, 7, 6, 3]`   |  `True`   |
|  `[2, 1, 4, 3, 6, 7, 6, 4]`   |  `False`   |
| `[4, 1, 4, 3, 6, 7, 6, 9]` | `True` |

<details>

<summary>Click here for solutions:</summary>

```python
# Solution 1
def odd_even(nums: list) -> bool:
    """Checks a list of numbers to see if every even index is an even number and every odd index is an odd number."""

    for index in range(len(nums)):
        if index % 2 != nums[index] % 2:
            return False

    return True

# Solution 2
def odd_even(nums: list) -> bool:
    """Checks a list of numbers to see if every even index is an even number and every odd index is an odd number."""

    for index, num in enumerate(nums):
        if index % 2 != num % 2:
            return False

    return True
```

As a beginner in Python, you may be tempted to use solution 1, but using the convention `for index in range(len(nums))` is regarded as bad practice once you become a professional developer.  The official Python developers saw people using this code and created the `enumerate()` function to eliminate it and create more beautiful code.

Solution 2 uses enumerate to easily reference both the index and number during the loop.

</details>

---

### 16.  Create a function to find the highest and lowest number from a given _string_ of space separated integers

Your function should return a dictionary with two keys, `'highest'` and `'lowest'`, who's values are the highest and lowest numbers in the inputted string.

Examples:

| Input | Output |
| --- | --- |
|  `'1 4 5 77 9 0'`   |  `{'highest': 77, 'lowest': 0}`   |
|  `'-1 -4 -5 -77 -9 0'`   |  `{'highest': 0, 'lowest': -77}`   |
|  `'0 0'`   |  `{'highest': 0, 'lowest': 0}`   |

<details>

<summary>Click here for solutions:</summary>

```python
def high_low(string: str) -> dict:
    """Returns a dictionary indicating the highest and lowest numbers from a string."""

    nums = [int(num) for num in string.split()]

    return {'highest': max(nums), 'lowest': min(nums)}

```

</details>

---

### 17.  Increment the number in a string

Create a function which increments the number at the end of a string.

If the string already ends with a number, the number should be incremented by 1.
If the string does not end with a number. the number 1 should be appended to the new string.

For the sake of this exercise, you can assume the inputted string will always be a sequence of letters followed by zero or more numbers, i.e. `abc123` not `123abc123`

Examples:

| Input | Output |
| --- | --- |
| `'foo'` | `'foo1'` |
| `'foobar23'` | `'foobar24'` |
| `'foo42'` | `'foo43'` |
| `'foo9'` | `'foo10'` |
| `'foo99'` | `'foo100'` |

<details>

<summary>Click here for solutions:</summary>

```python
# Solution 1
def increment_string(string: str) -> str:
    """Increments the number at the end of a string."""

    if string[-1].isalpha():
        return string + '1'

    # Find the index where the digits start
    for index, char in enumerate(string):
        if char.isdigit():
            word, number = string[:index], string[index:]
            break

    new_number = int(number) + 1

    return word + str(new_number)

# Solution 2
def increment_string(string: str) -> str:
    """Increments the number at the end of a string."""

    for index, char in enumerate(string):
        if char.isdigit():
            letters, num = string[:index], string[index:]
            new_num = int(num) + 1
            
            return letters + str(new_num)

    return string + '1'
    
```

</details>

---

### 18.  Create a function to check whether a list of numbers has an increasing trend or not

Examples:

| Input | Output |
| --- | --- |
|  `[1,2,3,4]`   |  `True`   |
|  `[1,2,5,3,4]`   |  `False`   |
|  `[-1,-2,-3,-4]`   |  `False`   |
| `[-4,-3,-2,-1]` | `True` |
| `[1,2,3,4,0]` | `False` |

<details>

<summary>Click here for solutions:</summary>

```python
# Solution 1
def increasing(nums: list) -> bool:
    """Checks a sequence of numbers to see if they only increase."""

    current = nums[0]

    for num in nums:
        if num < current:
            return False
        current = num

    return True

# Solution 2
def increasing(nums: list) -> bool:
    """Checks a sequence of numbers to see if they only increase."""

    for index, num in enumerate(nums[1:], 1):
        if num < nums[index - 1]:
            return False

    return True

# Solution 3
def increasing(nums: list) -> bool:
    """Checks a sequence of numbers to see if they only increase."""

    return nums == sorted(nums)
```

Solution 2 uses the `enumerate()` function to loop through all but the first number in the list of numbers.

For each number, it just checks to see if the current number is less than the previous number in the list.  If it is, the function will return False and exit.  If no numbers hit this condition, then the list of numbers is assumed to be increasing, and True is returned as a default.

</details>

---

### 19.  Create a function to find the name of the oldest student from a given dictionary containing the names and ages of a group of students

Examples:

| Input | Output |
| --- | --- |
|  `{"Bernita Ahner": 12, "Kristie Marsico": 11, "Sara Pardee": 14, "Fallon Fabiano": 11, "Nidia Dominique": 15}`   |  `Nidia Dominique`   |
|  `{"Nilda Woodside": 12, "Jackelyn Pineda": 12.2, "Sofia Park": 12.4, "Joannie Archibald": 12.6, "Becki Saunder": 12.7}`   |   `Becki Saunder`  |

<details>

<summary>Click here for solutions:</summary>

```python
# Solution 1
def oldest_student(students: dict) -> str:
    """Finds the oldest student from a dictionary."""

    oldest_name = None
    oldest_age = 0

    for name, age in students.items():
        if age > oldest_age:
            oldest_name = name
            oldest_age = age

    return oldest_name

# Solution 2
def oldest_student(students: dict) -> str:
    """Finds the oldest student from a dictionary."""

    oldest = {'name': None, 'age': 0}

    for name, age in students.items():
        if age > oldest['age']:
            oldest['name'] = name
            oldest['age'] = age

    return oldest['name']

print(oldest_student({"Bernita Ahner": 12, "Kristie Marsico": 11, "Sara Pardee": 14, "Fallon Fabiano": 11, "Nidia Dominique": 15}))
print(oldest_student({"Nilda Woodside": 12, "Jackelyn Pineda": 12.2, "Sofia Park": 12.4, "Joannie Archibald": 12.6, "Becki Saunder": 12.7}))
```

These two solutions accomplish the problem mostly in the same way.  The second solution just stores the current oldest student name and age in a dictionary.  Dictionaries can be viewed sort of like a way to store multiple variables.  

</details>

---

### 20.  Create a function to create a new string with no duplicate consecutive letters from a given string

Examples:

| Input | Output |
| --- | --- |
|  `'PPYYYTTHON'`   |   `'PYTHON'`  |
|   `'PPyyythonnn'`  |  `'Python'`   |
|   `'Java'`  |  `'Java'`   |
|   `'PPPHHHPPP'`  |  `'PHP'`   |

<details>

<summary>Click here for solutions:</summary>

```python
def rem_dup(string: str) -> str:
    """Removes consecutive duplicate letters from a string."""

    result = string[0]
    for letter in string[1:]:
        if letter != result[-1]:
            result += letter

    return result
```

</details>

---

### 21.  Index a matrix

Create a function that checks to see if a number within a matrix of numbers is **even**.

The matrix will be represented by a list of lists, where each list is the same length.

Here's an example:

```python
matrix = [
    [1, 2, 3, 4],
    [2, 3, 4, 5],
    [3, 4, 5, 6],
    [4, 5, 6, 7]
]
```

Your function should accept one argument which will be a point.  This point will be a tuple containing the x and y coordinates: `(1, 2)`

The origin will be the bottom left corner of the grid.  The vertical axis is the Y axis, and the horizontal axis is the X axis. The x and y coordinates start at 1 beginning at the origin.

For this exercise, your function should always reference the following matrix:

```python
[
    [1, 5, 3],
    [4, 6, 5],
    [7, 8, 9]
]
```

Examples:

| Input | Number within the matrix | Output |
| --- | --- | --- |
|  `(1, 2)`   |   `4`  |  `True`   |
|  `(3, 1)`   |   `9`  |   `False`  |
|  `(2, 2)`   |  `6`   |  `True`   |
|  `(3, 3)`   |   `3`  |  `False`   |

<details>

<summary>Click here for solutions:</summary>

```python
matrix = [
    [1, 5, 3],
    [4, 6, 5],
    [7, 8, 9]
]

def is_even(point: tuple) -> bool:
    """Checks to see if a number within a matrix is even."""

    x, y = point
    num = matrix[y - 1][x - 1]

    return num % 2 == 0
```

</details>

---

### 22.  Create a function to find the indices of all occurrences of a given item in a given list

Your function should accept a list of numbers and a target number as parameters, and should return a list of integers where each integer is an index where the target existed in the original list.

If the item is not in the list at all, return an empty list.

Examples:

| Input | Output |
| --- | --- |
|  `[1, 2, 3, 4, 5, 2], 2`   |  `[1, 5]`   |
|  `[3, 1, 2, 3, 4, 5, 6, 3, 3], 3`   |   `[0, 3, 7, 8]`  |
|  `[1, 2, 3, -4, 5, 2, -4], -4`   |  `[3, 6]`   |
|   `[1, 2, 3, 4, 5, 2], 7`  |  `[]`   |

<details>

<summary>Click here for solutions:</summary>

```python
# Solution 1
def get_indices(items: list, target: object) -> list:
    """Returns a list containing all the indices of a list where a target item resides."""

    indices = list()
    for index, item in enumerate(items):
        if item == target:
            indices.append(index)

    return indices

# Solution 2
def get_indices(items: list, target: object) -> list:
    """Returns a list containing all the indices of a list where a target item resides."""

    indices = [ index for index, num in enumerate(items) if num == target ]
    return indices
```

This solution makes good use of the `enumerate()` function.  Note that when we instantiate the `indices` list, as an alternative to using `[]`, we can use the `list()` function like in this solution.  

</details>

---

### 23.  Create a function to check whether the average of the numbers within a string is a whole number or not

As input, your function should take in a string of numbers separated by spaces.

Examples:

| Input | Average | Output |
| --- | --- | --- |
|  `'1 3 5 7 9'`   |  `5.0`  |   `True`  |
|  `'2 4 2 6 4 8'`   |  `4.333`   | `False` |

<details>

<summary>Click here for solutions:</summary>

```python
def is_whole_avg(nums: str) -> bool:
    """Checks to see if the average of a sequence of numbers in a string is a whole number."""

    numbers = [int(number) for number in nums.split()]
    average = sum(numbers) / len(numbers)

    return average % 1 == 0.0

```

</details>

---

### 24.  Create a function to remove all vowels from a given string

Examples:

| Input | Output |
| --- | --- |
|  `'Python'`   |  `'Pythn'`   |
|  `'C Sharp'`   |   `'C Shrp'`  |
|  `'JavaScript'`   |  `'JvScrpt'`   |

<details>

<summary>Click here for solutions:</summary>

```python
# Solution 1
def rem_vowels(string: str) -> str:
    """Removes all vowels from a string."""

    vowels = 'aeiou'
    return ''.join([letter for letter in string if letter not in vowels])

    # Solution 2
def rem_vowels(string: str) -> str:
    """Removes all vowels from a string."""

    vowels = 'aeiou'
    return ''.join(letter for letter in string if letter not in vowels)

print(rem_vowels('Python')) # -> 'Pythn'
print(rem_vowels('C Sharp')) # -> 'C Shrp'
print(rem_vowels('JavaScript')) # -> 'JvScrpt'
```

The only difference between solution 1 and solution 2 is that solution 2 passes a _generator_ object to the `join()` function.

Anytime we use list-comprehension syntax without the brackets `[]`, it will create a generator object.  

Generator objects are special in that they act as an iterable sequence of objects, but you cannot view the contents of a generator object as a whole.  You can only loop, or _iterate_, through them.

</details>

---

### 25.  Create a function to get the index number of all lower case letters in a given string

Examples:

| Input | Output |
| --- | --- |
|  `'Python'`   |  `[1, 2, 3, 4, 5]`   |
|  `'JavaScript'`   |  `[1, 2, 3, 5, 6, 7, 8, 9]`    |
|   `'PHP'`  |   `[]`  |

<details>

<summary>Click here for solutions:</summary>

```python
# Solution 1
def lower_indices(string: str) -> list:
    """Returns a list of indices of all lowercase letters in a string."""
    indices = list()
    for index, letter in enumerate(string):
        if letter.islower():
            indices.append(index)
    return indices

# Solution 2
def lower_indices(string: str) -> list:
    """Returns a list of indices of all lowercase letters in a string."""

    return [index for index, letter in enumerate(string) if letter.islower()]

```

</details>

---

### 26.  Create a function to find all the factors of a given natural number

The factors of a number are the numbers that divide into it exactly.

Examples:

| Input | Output |
| --- | --- |
|  `1`   |   `[1]`  |
|  `12`   |  `[1, 2, 3, 4, 6, 12]`   |
|  `100`   |  `[1, 2, 4, 5, 10, 20, 25, 50, 100]`   |

<details>

<summary>Click here for solutions:</summary>

```python
def get_factors(num: int) -> list:
    """Returns the factors of a number."""

    factors = []
    for possible_factor in range(1, num + 1):
        if num % possible_factor == 0:
            factors.append(possible_factor)

    return factors

```

</details>

---

### 27.  Create a function to alternate the case of each letter in a given string

Given a string, your function should return the string where the case alternates letter by letter.  The first letter should always be uppercase.

Your function should disregard any character that is not a letter.

Examples:

| Input | Output |
| --- | --- |
| `'Hello world.'` | `'HeLlO wOrLd.'` |
|  `'Python Exercises'`   |  `'PyThOn ExErCiSeS'`   |
|  `'C# is used to develop web apps, desktop apps, mobile apps, games and much more'`   |  `'C# iS uSeD tO dEvElOp WeB aPpS, dEsKtOp ApPs, MoBiLe ApPs, GaMeS aNd MuCh MoRe'`   |

<details>

<summary>Click here for solutions:</summary>

```python
def alt_case(string: str) -> str:
    """Alternate the case of every letter in a string."""

    # Set the case to True, which for our function will indicate upper case
    case = True

    # Create an initial empty result string
    result = ''

    for char in string:

        if char.isalpha():
            # If the case variable is set to True, append the uppercased letter to the result string, else append the lowercased version
            result += char.upper() if case else char.lower()

            # Alternate the case between True and False
            case = not case

        # If the character isn't a letter, just append it
        else:
            result += char

    return result

```

</details>

---

### 28.  Create a function to reverse each word of a string

The order of the words themselves should not change.  You are just reversing the letters within each word.

Examples:

| Input | Output |
| --- | --- |
|  `'My Name is Jessa'`   |  `'yM emaN si asseJ'`   |
|  `'One day Michael came in and complained about a speed bump on the highway'`   |  `'enO yad leahciM emac ni dna denialpmoc tuoba a deeps pmub no eht yawhgih'`   |
| `'I wonder who he ran over then'` |  `'I rednow ohw eh nar revo neht'`   |
|   `'now I have eggs in my crocs'`  |  `'won I evah sgge ni ym scorc'`   |

<details>

<summary>Click here for solutions:</summary>

```python
def rev_words(string: str) -> str:
    """Reverses each word within a string."""

    return ' '.join(word[::-1] for word in string.split())

```

</details>

---

### 29.  Arcade Game

In this exercise, you need to implement some rules from Pac-Man, the classic 1980s-era arcade-game.

You have four rules to implement, all related to the game states.

Do not worry about how the arguments are derived, just focus on combining the arguments to return the intended result.

1. Define if Pac-Man eats a ghost

    Define a function called `eat_ghost()` that takes two parameters (if Pac-Man has a power pellet active and if Pac-Man is touching a ghost) and returns a Boolean value if Pac-Man is able to eat the ghost. The function should return True only if Pac-Man has a power pellet active and is touching a ghost.

    Examples:

    | Input | Output |
    | --- | --- |
    | `True, True` | `True` |
    | `False, True` | `False` |
    | `True, False` | `False` |
    | `False, False` | `False` |

2. Define if Pac-Man scores

    Define the `score()` function that takes two parameters (if Pac-Man is touching a power pellet and if Pac-Man is touching a dot) and returns a Boolean value if Pac-Man scored. The function should return True if Pac-Man is touching a power pellet **or** a dot.

    Examples:

    | Input | Output |
    | --- | --- |
    | `True, True` | `True` |
    | `False, True` | `True` |
    | `True, False` | `True` |
    | `False, False` | `False` |

3. Define if Pac-Man loses

    Define the `lose()` function that takes two parameters (if Pac-Man has a power pellet active and if Pac-Man is touching a ghost) and returns a Boolean value if Pac-Man loses. The function should return True if Pac-Man is touching a ghost and does not have a power pellet active.

    Examples:

    | Input | Output |
    | --- | --- |
    | `True, True` | `False` |
    | `False, True` | `True` |
    | `True, False` | `False` |
    | `False, False` | `False` |

4. Define if Pac-Man wins

    Define the `win()` function that takes three parameters (if Pac-Man has eaten all of the dots, if Pac-Man has a power pellet active, and if Pac-Man is touching a ghost) and returns a Boolean value if Pac-Man wins. The function should return True if Pac-Man has eaten all of the dots and has not lost based on the parameters defined in part 3.

    Examples:

    | Input | Output | Reason |
    | --- | --- | --- |
    | `True, True, True` | `True` | Pac-Man has eaten all of the dots, has a power pellet active, and is touching a ghost (negated by power pellet) |
    | `True, True, False` | `True` | Pac-Man has eaten all of the dots, has a power pellet active, and is NOT touching a ghost |
    | `True, False, True` | `False` | Pac-Man has eaten all of the dots, does NOT have a power pellet active, and is touching a ghost (lost the game) |
    | `True, False, False` | `True` | Pac-Man has eaten all of the dots, does NOT have a power pellet active, and is NOT touching a ghost |
    | `False, True, True` | `False` | Pac-Man hasn't eaten all of the dots |
    | `False, True, False` | `False` | Pac-Man hasn't eaten all of the dots |
    | `False, False, True` | `False` | Pac-Man hasn't eaten all of the dots |
    | `False, False, False` | `False` | Pac-Man hasn't eaten all of the dots |

<details>

<summary>Click here for solutions:</summary>

```python
def eat_ghost(pellet_active: bool, touching_ghost: bool) -> bool:
    """Checks to see if you can eat a ghost."""

    return pellet_active and touching_ghost

def score(touching_pellet: bool, touching_dot: bool) -> bool:
    """Checks to see if you are scoring."""

    return touching_pellet or touching_dot

def lose(pellet_active: bool, touching_ghost: bool) -> bool:
    """Checks to see if the game is lost."""

    return not pellet_active and touching_ghost

def win(eaten_all_dots: bool, pellet_active: bool, touching_ghost: bool) -> bool:
    """Tells you if you've won the game."""

    return eaten_all_dots and not lose(pellet_active, touching_ghost)
```

</details>

---

### 30.  Hamming

Create a function to calculate the Hamming Distance between two DNA strands.

When cells divide, their DNA replicates too. Sometimes during this process mistakes happen and single pieces of DNA get encoded with the incorrect information. If we compare two strands of DNA and count the differences between them we can see how many mistakes occurred. This is known as the "Hamming Distance".

We read DNA using the letters C,A,G and T. Two strands might look like this:

```
GAGCCTACTAACGGGAT
CATCGTAATGACGGCCT
^ ^ ^  ^ ^    ^^
```

They have 7 differences, and therefore the Hamming Distance is 7.

The Hamming distance is only defined for sequences of equal length.

Examples:

| Input | Output |
| --- | --- |
| `'CCTAG', 'CCGAT'` | `2` |
| `'TACGTCA', 'CATGTAC'` | `4` |
| `'GAGCCTACTAACGGGAT', 'CATCGTAATGACGGCCT'` | `7` |

<details>

<summary>Click here for solutions:</summary>

```python
# Solution 1
def hamming(strand_a: str, strand_b: str) -> int:
    """Returns the hamming distance of two pieces of DNA."""

    differences = 0
    for char_a, char_b in zip(strand_a, strand_b):
        if char_a != char_b:
            differences += 1

    return differences

# Solution 2
def hamming(strand_a: str, strand_b: str) -> int:
    """Returns the hamming distance of two pieces of DNA."""

    # Create a list of True/False values
    bools = [char_a != char_b for char_a, char_b in zip(strand_a, strand_b)] # -> [True, False, False, True] (as an example)

    # Pass our list of True/False values to the sum function.  It will tally up all the True's.
    return sum(bools)

print(hamming('GAGCCTACTAACGGGAT', 'CATCGTAATGACGGCCT')) # -> 7
```

In the second solution, we can compare the letters of each DNA strand in a list comprehension and then save the resulting booleans to the list.  We then pass our list of True/False values to the `sum()` function, which tallies up the number of True's.  This is because True and False correlate to 1 and 0, respectively.  As an example, the list `[True, False, True]` would evaluate to 2, because True appears twice in the list.

</details>

---

### 31.  Talk to Bob

Bob is a lackadaisical teenager. In conversation, his responses are very limited.

Bob answers `'Sure.'` if you ask him a question, such as "How are you?".

He answers `'Whoa, chill out!'` if you YELL AT HIM (in all capitals).

He answers `'Calm down, I know what I'm doing!'` if you yell a question at him.

He says `'Fine. Be that way!'` if you address him without actually saying anything.

He answers `'Whatever.'` to anything else.

Bob's conversational partner is a purist when it comes to written communication and always follows normal rules regarding sentence punctuation in English.

Solve this problem however you see fit.

Examples:

| Input | Output |
| --- | --- |
| `'WHAT ARE YOU DOING?'` | `'Calm down, I know what I'm doing!'` |
| `'How are you doing?'` | `'Sure.'` |
| `'STOP THAT'` | `'Whoa, chill out!'` |
| `''` | `'Fine. Be that way!'` |
| `'it is a nice day out.'` | `'Whatever.'` |

<details>

<summary>Click here for solutions:</summary>

```python
# Solution 1
class Person:
    def __init__(self, name):
        self.name = name
    def start_convo(self, statement: str) -> str:
        """Returns a response based on the statement provided."""
        if not statement:
            print('Fine. Be that way!')
        elif statement[-1] == '?' and statement.isupper():
            print('Calm down, I know what I\'m doing!')
        elif statement[-1] == '?':
            print('Sure.')
        elif statement.isupper():
            print('Whoa, chill out!')
        else:
            print('Whatever.')

bob = Person('bob')

bob.start_convo('WHAT ARE YOU DOING?')
bob.start_convo('How are you doing?')
bob.start_convo('STOP THAT')
bob.start_convo('')
bob.start_convo('it\'s a nice day out.')

# Solution 2
def bob():
    """Creates a bot that you can talk to."""

    talking = True

    while talking:

        statement = input('\nEnter something to say to bob...\n\nType \'q\' to quit.\n')

        if statement in ['q', 'quit']:
            print('\nRESPONSE: This was nice.  See you next time.\n')
            talking = False
        elif not statement:
            print('\nRESPONSE: Fine. Be that way!\n')
        elif statement[-1] == '?' and statement.isupper():
            print('\nRESPONSE: Calm down, I know what I\'m doing!\n')
        elif statement[-1] == '?':
            print('\nRESPONSE: Sure.\n')
        elif statement.isupper():
            print('\nRESPONSE: Whoa, chill out!\n')
        else:
            print('\nRESPONSE: Whatever.\n')
```

Solution 1 creates a class that has a method that allows you to talk to instances.  After the class definition, we create an instance and call its method to talk to it.

Solution 2 uses a function instead of a class.  It uses a while loop to create a repeating program.  This program returns the right responses using an if-elif-else chain.

</details>

---

### 32.  RNA Transcription

Given a DNA strand, return its RNA complement (per RNA transcription).

Both DNA and RNA strands are a sequence of nucleotides.

The four nucleotides found in DNA are adenine (A), cytosine (C), guanine (G) and thymine (T).

The four nucleotides found in RNA are adenine (A), cytosine (C), guanine (G) and uracil (U).

Given a DNA strand, its transcribed RNA strand is formed by replacing each nucleotide with its complement:

G -> C

C -> G

T -> A

A -> U

Examples:

| Input | Output |
| --- | --- |
| `'CCTAG'` | `'GGAUC'` |
| `'TACGTCA'` | `'AUGCAGU'` |
| `'GAGCCTACTAACGGGAT'` | `'CUCGGAUGAUUGCCCUA'` |

<details>

<summary>Click here for solutions:</summary>

```python
def rna_trans(dna: str) -> str:
    """Returns the RNA of a DNA strand."""

    a = {
        'G': 'C',
        'C': 'G',
        'T': 'A',
        'A': 'U'
    }

    return ''.join(a[letter] for letter in dna.upper())

```

</details>

---

### 33.  Armstrong Number

An Armstrong number is a number that is the sum of its own digits each raised to the power of the number of digits.

For example:

* 9 is an Armstrong number, because 9 = 9<sup>1</sup> = 9

* 10 is not an Armstrong number, because 10 != 1<sup>2</sup> + 0<sup>2</sup> = 1

* 153 is an Armstrong number, because: 153 = 1<sup>3</sup> + 5<sup>3</sup> + 3<sup>3</sup> = 1 + 125 + 27 = 153

* 154 is not an Armstrong number, because: 154 != 1<sup>3</sup> + 5<sup>3</sup> + 4<sup>3</sup> = 1 + 125 + 64 = 190

Write a function to determine whether a number is an Armstrong number.

Examples:

| Input | Output |
| --- | --- |
| `8` | `True` |
| `11` | `False` |
| `370` | `True` |
| `371` | `True` |
| `400` | `False` |
| `407` | `True` |

<details>

<summary>Click here for solutions:</summary>

```python
def armstrong(number: int) -> bool:
    """Checks to see if a number is an armstrong number."""

    string_number = str(number)
    power = len(string_number)
    
    computed_digits = [int(digit) ** power for digit in string_number]

    return sum(computed_digits) == number

```

</details>

---

### 34.  Anagrams

An anagram is a rearrangement of letters to form a new word. Given a word and a list of candidates, select the sublist of anagrams of the given word.

For example, given the word `'listen'` and a list of candidates like `'enlists'` `'google'` `'inlets'` `'banana'` the program should return a list containing `'inlets'`.

<details>

<summary>Click here for solutions:</summary>

```python
def anagram(word: str, candidates: list) -> list:
    """
    Tests a word against a list of words to see which ones are anagrams.
    Anagrams are words with the same letters in a different order.
    """

    anagrams = []
    for candidate in candidates:
        if sorted(word) == sorted(candidate):
            anagrams.append(candidate)

    return anagrams
```

</details>

---

### 35.  Create a Robot class

Create a Robot class to manage robot factory settings.

When a robot comes off the factory floor, it has no name.

The first time you turn on a robot, a random name is generated in the format of two uppercase letters followed by three digits, such as RX837 or BC811.

Every once in a while we need to reset a robot to its factory settings, which means that its name gets wiped. The next time you ask, that robot will respond with a new random name.

The names must be random: they should not follow a predictable sequence. Using random names means a risk of collisions. Your solution must ensure that every existing robot has a unique name.

<details>

<summary>Click here for solutions:</summary>

```python
from string import ascii_uppercase as alphabet
from random import randint
from time import sleep
from termcolor import colored

class Robot:
    """Generic robot class."""

    existing_names = []

    def __init__(self):
        self.name = None
        self.status = 'off'

    def gen_random_name(self) -> str:
        """
        Generates a random name with two letters followed by three digits. 
        Only returns a name if it is not already in the list of existing names. 
        Recursively calls itself if a randomly generated name is already in the list of existing names.
        """

        random_name = '{}{}{}{}{}'.format(
            alphabet[randint(0,25)],
            alphabet[randint(0,25)],
            randint(0,9),
            randint(0,9),
            randint(0,9)
        )

        if random_name not in self.__class__.existing_names:
            self.__class__.existing_names.append(random_name)
            self.name = random_name
        else:
            self.gen_random_name()

    def turn_on(self):
        """Turns the robot on.  Gives it a name and sets its status to 'on'."""

        print(f'Creating new name...\n')
        self.gen_random_name()
        sleep(2)

        print(f'Done. Newly created name: {self.name}\n')
        sleep(1)

        print(f'Turning on robot {self.name}...\n')

        for sound in ['beep','boop', 'beep', 'bop']:
            print(colored(sound, 'green'))
            sleep(1)
        self.status = 'on'

        print(f'Done. Robot {self.name} is now alive.')

    def reset(self):
        """Gives the robot a new random name."""

        print(f'Removing robot name {self.name} from the list of current robots.')

        self.__class__.existing_names.remove(self.name)

        self.gen_random_name()

        print(f'Done. New name: {self.name}')

        

a = Robot()
b = Robot()

a.turn_on()
print(a.name)

b.turn_on()
print(b.name)

print(Robot.existing_names)

b.reset()

print(b.name)
print(Robot.existing_names)
```

</details>

---

### 36.  Simple Cipher

Ciphers are very straight-forward algorithms that allow us to render text less readable while still allowing easy deciphering. They are vulnerable to many forms of cryptanalysis, but we are lucky that generally our little sisters are not cryptanalysts.

The Caesar Cipher was used for some messages from Julius Caesar that were sent afield. Now Caesar knew that the cipher wasn't very good, but he had one ally in that respect: almost nobody could read well. So even being a couple letters off was sufficient so that people couldn't recognize the few words that they did know.

Your task is to create a simple shift cipher like the Caesar Cipher. This image is a great example of the Caesar Cipher:

![caeser cipher](../../Images/Python/caeser_cipher.png)

You will need to create two functions, an encode function and a decode function. Each function will use a specific shift count unknown by the user.

For example, if you chose to use a shift count of 3 in your functions:

Giving `'iamapandabear'` as input to the encode function returns the cipher `'ldpdsdqgdehdu'`. Obscure enough to keep our message secret in transit.

When `'ldpdsdqgdehdu'` is put into the decode function it would return the original `'iamapandabear'` letting your friend read your original message.

Here are more examples where a shift count of 3 is used.

Encoding Function:

| Input | Output |
| --- | --- |
| `'abc'` | `'def'` |
| `'xyz'` | `'abc'` |
| `'hello world'` | `'khoor zruog'` |

Decoding Function:

| Input | Output |
| --- | --- |
| `'def'` | `'abc'` |
| `'abc'` | `'xyz'` |
| `'khoor zruog'` | `hello world` |

<details>

<summary>Click here for solutions:</summary>

```python
from string import ascii_lowercase

def encode(plaintext: str) -> str:
    """
    Takes in a regular string and encodes it using a shift cipher.
    This encode function will shift the letters three spots to the right.
    """

    plaintext = plaintext.lower()
    encoded_string = ''

    # Add three letters to the end of our alphabet to account for letters x, y and z.
    # Since they are at the end of the actual alphabet, with a shift count of three, we need to be able to wrap back around to abc...etc to assign the appropriate new letter.
    alphabet = ascii_lowercase + 'abc'

    for char in plaintext:
        # If the character is a letter, shift it.  Otherwise just add it.
        if char.isalpha():
            alphabet_index = alphabet.index(char)
            shifted_index = alphabet_index + 3
            encoded_string += alphabet[shifted_index]
        else:
            encoded_string += char

    return encoded_string

def decode(ciphertext: str) -> str:
    """
    Takes in cipher text and decodes it.
    Assumes a shift count of +3 was used.
    """

    decoded_string = ''
    alphabet = 'xyz' + ascii_lowercase

    for char in ciphertext:
        if char.isalpha():
            shifted_index = alphabet.index(char)
            original_index = shifted_index - 3
            decoded_string += alphabet[original_index]
        else:
            decoded_string += char

    return decoded_string

```

</details>

---

### 37.  Determine if two nested lists are nested the same way

Create a function that returns `True` when its first argument is a list that has the same nesting structures and same corresponding length of nested lists as the first list.

Examples:

| Input | Output |
| --- | --- |
| `[ 1, 1, 1 ], [ 2, 2, 2 ]` | `True` |
| `[ 1, [ 1, 1 ] ], [ 2, [ 2, 2 ] ]` | `True` |
| `[ 1, [ 1, 1 ] ], [ [ 2, 2 ], 2 ]` | `False` |
| `[ 1, [ 1, 1 ] ], [ [ 2 ], 2 ]` | `False` |
| `[ [ [ ], [ ] ] ], [ [ [ ], [ ] ] ]` | `True` |
| `[ [ [ ], [ ] ] ], [ [ 1, 1 ] ]` | `False` |

<details>

<summary>Click here for solutions:</summary>

```python
def same_nested(l1: list, l2: list) -> bool:
    """Determines if two lists have the same nesting structure."""

    str_l1, str_l2 = str(l1), str(l2)

    TARGET_CHARS = ['[', ']', ',']

    l1_target_chars = [char for char in str_l1 if char in TARGET_CHARS]
    l2_target_chars = [char for char in str_l2 if char in TARGET_CHARS]

    return l1_target_chars == l2_target_chars

```

In this solution we use the flexibility of Python to solve this problem in a simple way.  We simply convert each inputted list to a string, parse each string for the necessary characters, and see if the list of characters in each string matches.  This way we don't have to worry about the actual objects within the lists.

</details>

---

### 38.  Find the survivor

In this exercise you have to correctly return who is the "survivor", ie: the last element of a Josephus permutation.

Basically you have to assume that N people are put into a circle and that they are eliminated in steps of k elements, like this:

```
josephus_survivor(7,3) => means 7 people in a circle;
one every 3 is eliminated until one remains

[1,2,3,4,5,6,7] - initial sequence
[1,2,4,5,6,7] => 3 is counted out
[1,2,4,5,7] => 6 is counted out
[1,4,5,7] => 2 is counted out
[1,4,5] => 7 is counted out
[1,4] => 5 is counted out
[4] => 1 counted out, 4 is the last element - the survivor!
```

Here are more examples:

| Input | Output |
| --- | --- |
| `7, 3` | `[4]` |
| `9, 2` | `[3]` |
| `8, 4` | `[6]` |

<details>

<summary>Click here for solutions:</summary>

```python
# Solution 1
def survivor(circle, interval) -> list:
    """Finds the josephus survivor in a circle of people."""

    # Convert the integer to a list of number
    circle = list(range(1, circle + 1))

    # Initialize a counter
    counter = 1

    # Use while loop to repeatedly loop through circle
    while True:

        # If the circle is down to one person, return the answer.
        if len(circle) == 1:
            return circle

        current_elims = []
        for person in circle:

            # Mark person for elimination
            if counter == interval:
                current_elims.append(person)
                counter = 1
            else:
                counter += 1

        # Create a new circle excluding the people marked for elimination
        circle = [person for person in circle if person not in current_elims]

# Solution 2
def survivor(circle, interval, counter=1) -> list:
    """Finds the josephus survivor in a circle of people."""

    # Convert the integer to a list of number
    if type(circle) == int:
        circle = list(range(1, circle + 1))

    # If the circle is down to one person, return the answer.
    if len(circle) == 1:
        return circle

    current_elims = []
    for person in circle:

        # Mark person for elimination
        if counter == interval:
            current_elims.append(person)
            counter = 1
        else:
            counter += 1

    # Create a new circle excluding the people marked for elimination
    circle = [person for person in circle if person not in current_elims]

    return survivor(circle, interval, counter)
```

If you were able to solve this one on your own, congrats!

The first solution uses a while-loop to repeatedly loop through the circle which has been converted to a list of integers.  On each loop through the circle, a counter is used to mark certain people for elimination.  After the loop through the circle, a new circle is made excluding the eliminations.  Then, the while-loop executes again, running through a new round of eliminations.  In each iteration of the while-loop, we check to see if the circle is down to one person.  If it is, we return the answer.

The second solution an advanced solution that uses _recursion_.  Recursion is when we call on a function within itself.  It uses the same logic as the first solution, but instead of using a while-loop to repeatedly loop through the circle, we simply make a round of eliminations, then pass the new circle, interval, and counter value to the same function, which will make another round of eliminations.  This will occur recursively until the circle is down to one person, which will trigger the `return` statement, thus ending the chain of recursion.

>Note: Some type hints weren't used in this solution so that it would be easier to read.

</details>

---

### 39.  Find all permutations of a string

In this exercise you have to write a function to create all permutations of a non empty input string and remove duplicates, if present. This means, you have to shuffle all letters from the input in all possible orders.

The order of the permutations doesn't matter.

Examples:

| Input | Output |
| --- | --- |
| `'a'` | `['a']` |
| `'ab'` | `['ab', 'ba']` |
| `'aabb'` | `['aabb', 'abab', 'abba', 'baab', 'baba', 'bbaa']` |

<details>

<summary>Click here for solutions:</summary>

```python
from itertools import permutations

def perms(string: str) -> list:
    """Returns a list containing all the permutations of a string."""

    result = set()

    for p in permutations(string):
        result.add(''.join(letter for letter in p))

    return list(result)
```

Here we make handy use of a module that can do all the logic for us.  If you did this manually, that's great, but always consider leveraging pre-written code when possible.

First, we loop through all of the string's permutations.  Unfortunaly, the `permutations` function from the `itertools` package returns a lot of duplicates.  To account for this, we put each permutation in the `result` set.  

Then, we cast the set to a list using the `list()` function, and return it.

</details>

---

### 40.  Create a function that converts a CIDR notation to dotted decimal notation

Your function should take in an integer as input and return the subnet mask in dotted decimal notation.

Examples:

| Input | Output |
| --- | --- |
| `29` | `'255.255.255.248'` |
| `24` | `'255.255.255.0'` |
| `12` | `'255.240.0.0'` |
| `25` | `'255.255.255.128'` |

<details>

<summary>Click here for solutions:</summary>

```python
def ddn(cidr: int) -> str:
    """Converts a CIDR to dotted decimal notation."""

    binary = '1' * cidr + '0' * (32 - cidr)

    bytes = []
    for index in range(0, 32, 8):
        bytes.append(binary[index:index + 8])
    
    octets = [int(byte, base=2) for byte in bytes]

    return '.'.join(str(octet) for octet in octets)
```

In this solution we first create a binary string from the CIDR.

Then, we seperate the binary string into individual bytes.

After that, we convert each byte into a decimal by casting it with the `int()` function, specifying that the input is in base 2.

Lastly, we return the string version of each integer joined with a period.

</details>

---

### 41.  Find a subnet ID

Create a function that, given an IP address and a subnet mask, find the IP address's subnet ID.

Examples:

| Input | Output |
| --- | --- |
|  `'192.168.8.1', '255.255.255.0'`   | `'192.168.8.0'`    |
|  `'172.16.1.100', '255.255.255.192'`   |  `'172.16.1.64'`   |
| `'10.0.2.150', '255.255.255.248'` | `'10.0.2.144'` |

<details>

<summary>Click here for solutions:</summary>

```python
# Solution 1
def subnet(ip: str, mask: str) -> str:
    """Finds an IP address's subnet ID."""

    # Separate each into octets
    ip_octets = [int(octet) for octet in ip.split('.')]
    mask_octets = [int(octet) for octet in mask.split('.')]

    # Perform AND bitwise operation on each octet in order
    subnet_id_octets = [o1 & o2 for o1, o2 in zip(ip_octets, mask_octets)]

    return '.'.join(str(octet) for octet in subnet_id_octets)

# Solution 2
import ipaddress

def subnet(ip: str, mask: str) -> str:
    """Finds an IP address's subnet ID."""

    # Convert mask to CIDR
    CIDR = ''.join(f'{int(octet):08b}' for octet in mask.split('.')).count('1')

    # Create an ipaddress network object
    ip_network = ipaddress.IPv4Network(f'{ip}/{CIDR}', strict=False)

    return str(ip_network.network_address)
```

---

The first solution uses a really cool tool called [bitwise operators](https://www.tutorialspoint.com/python/bitwise_operators_example.htm#:~:text=Python%20Bitwise%20Operators%20Example%20%20%20%20Operator,2%27s%20comp%20...%20%202%20more%20rows%20).  They allow you to perform operations on numbers using their binary form.

For example, the `&` bitwise operator performs an AND operation on two numbers.  An easy way of converting an IP and mask into a subnet ID is by simply performing this AND operation on each octet.  

So, in this solution, what we are doing is creating a list of octets for both the IP and mask, and then going through each octet at the same time and performing the AND operation using the `&` operator.

Given an IP and mask of 172.16.1.100 and 255.255.255.192, respectively, this is how the AND operation would work for each octet:

| IP Octet | Mask Octet | Syntax of AND operation | Result |
| --- | --- | --- | --- |
| 172 | 255 | 172 & 255 | 172 |
| 16 | 255 | 16 & 255 | 16 |
| 1 | 255 | 1 & 255 | 1 |
| 100 | 192 | 100 & 192 | 64 |

---

The second solution uses the built-in `ipaddress` module.  First we convert the dotted decimal mask to CIDR by converting each octet to binary and then counting the number of 1's.  We then use the builtin `ipaddress` module to create a network object.  When we do this, we have to use `strict=False` since the address has host bits set.  Once we create the network object, we can reference its attributes, such as the `network_address`.

</details>

---

### 42.  Create a function to check if an IP address is within a subnet

The function should take an IP address and a subnet ID with a mask in CIDR notation.

Examples:

| Input | Output |
| --- | --- |
| `'192.168.2.1', '192.168.2.0/24'` | `True` |
| `'192.168.1.1', '192.168.1.128/25'` | `False` |
| `'192.168.1.9', '192.168.1.0/29'` | `False` |
| `'192.168.10.129', '192.168.10.128/25'` | `True` |

<details>

<summary>Click here for solutions:</summary>

```python
# Solution 1
def is_in_subnet(ip: str, mask: str) -> bool:
    """
    Checks to see if an IP address is in a subnet.
    This solution converts the IP and mask to dotted decimal notation and then performs a bitwise AND operation between the two.  This produces a subnet ID.  If this subnet ID is equal to the subnet ID that is supplied to the function, we know that the IP is in the subnet.  
    """

    subnet, cidr = subnet.split('/')

    ip_octets = [ int(octet) for octet in address.split('.') ]
    subnet_octets = [ int(octet) for octet in subnet.split('.') ]

    # Turn the cidr into a list of 1's and 0's
    mask = [ '1' if i + 1 <= int(cidr) else '0' for i in range(32) ]

    mask_octets = [ int(''.join(mask[i:i+8]), base=2) for i in range(0, 32, 8) ]

    # For each octet in the ip and mask, perform a bitwise AND operation
    # to make sure the result equals the subnet octet
    for a, b, c in zip(ip_octets, mask_octets, subnet_octets):
        if a & b != c:
            return False

    return True

# Solution 2
from ipaddress import ip_network

def is_in_subnet(ip: str, mask: str) -> bool:
    """
    Checks to see if an IP address is in a subnet.
    This solution uses the built-in ipaddress package.
    We separate the CIDR from the mask argument and then use the CIDR along with the supplied IP to create an ip network object.  If this network object has the same value as the inputted mask, we know the IP is in the subnet.
    """

    subnet_id, cidr = mask.split('/')

    # Create a subnet object by using the ip address along with the CIDR notation mask
    network_from_ip = ip_network(f'{ip}/{cidr}', strict=False)

    return str(network_from_ip) == mask
```

Solution 1 is the hard way.  Solution 2 is the easy way.  Work smarter not harder.  Anytime you are doing something that you imagine has been coded before, do some googling to see if there is a ready-made solution.

</details>

---

### 43.  Fibonacci Sequence

The fibonacci sequence is a sequence of numbers starting with 1, 1, where each successive number is equal to the previous two numbers added together.

First 10 numbers in the fibonacci sequence:

`1, 1, 2, 3, 5, 8, 13, 21, 34, 55`

Create a function that returns the N<sup>th</sup> number of the fibonacci sequence.

Examples:

| Input | Output |
| --- | --- |
| `4` | `3` |
| `7` | `13` |
| `9` | `34` |

<details>

<summary>Click here for solutions:</summary>

```python
# Solution 1
def fib(n: int) -> int:
    """Returns the Nth number of the fibonacci sequence."""

    # Account for a one-off case
    if n <= 2:
        return 1

    # Set the initial sequence
    sequence = [1]

    # Execute some code n - 1 times
    for _ in range(n - 1):
        
        # Calculate the sum of the last two numbers in our working sequence
        new_sum = sum(sequence[-2:])

        # Create a new list that only includes the last number from the original sequence and the sum we just calculated
        # Do this so that our sequence doesn't grow to a massive size
        sequence = [sequence[-1], new_sum]
        
    # Once the loop is done, we know that the last number in the sequence will be our desired value
    return sequence[-1]

# Solution 2
def fib(n: int, last_two=[1]) -> int:
    """Returns the Nth number of the fibonacci sequence."""

    # We will turn N in to a countdown timer that will be decremented with each recursive function call
    # Once n has been reduced to 1, we know the answer is the last item in the last_two list
    if n == 1:
        return last_two[-1]
        
    # Calculate the sum of the last two numbers
    new_sum = sum(last_two[-2:])

    # Create a new last_two list containing the last item from the original list as well as the sum we just calculated
    new_last_two = [last_two[-1], new_sum]

    # Decrement the counter by 1
    n -= 1

    # Call the function recursively, passing in the new countdown and new last_two list
    return fib(n, new_last_two)
```

In the first solution, we first use an if-statement to account for a one-off.  This one-off case is when the number N is either `1` or `2`.  In this case, the answer would always be `1`, because the first and second numbers in the fibonacci sequence are `1`.  We create a list that will represent our fibonacci sequence, and we go ahead and give it the first value.  

We then initiate a for-loop that will execute N - 1 times.  We use an underscore as our loop variable because we aren't actually using the loop variable in our code.  

During each iteration of the for-loop, we create a `new_sum` variable that is equal to the sum of the last two items in the current working sequence.  Due to Python's flexibility, even though the sequence initially only has a single value, the `sequence[-2:]` will still work, it will just return `[1]`.  

After the sum of the last two numbers is calculated, the sum is simply appended to the end of the sequence, and the for-loop executes again.  Once the for-loop is done executing, we know that the last item in the working sequence will contain our answer.

The second solution uses the same logic, but the function calls itself recursively.  One difference, though, is that N is turned into a countdown, and is decremented with each recursive function call.

</details>

---

### 44.  Create a text file

Using Python, create a text file in your current directory with the following contents:

```
The Zen of Python, by Tim Peters

Beautiful is better than ugly.
Explicit is better than implicit.
Simple is better than complex.
Complex is better than complicated.
Flat is better than nested.
Sparse is better than dense.
Readability counts.
Special cases aren't special enough to break the rules.
Although practicality beats purity.
Errors should never pass silently.
Unless explicitly silenced.
In the face of ambiguity, refuse the temptation to guess.
There should be one-- and preferably only one --obvious way to do it.
Although that way may not be obvious at first unless you're Dutch.
Now is better than never.
Although never is often better than *right* now.
If the implementation is hard to explain, it's a bad idea.
If the implementation is easy to explain, it may be a good idea.
Namespaces are one honking great idea -- let's do more of those!
```

**This may require some googling.**

<details>

<summary>Click here for solutions:</summary>

```python
principles = """
The Zen of Python, by Tim Peters

Beautiful is better than ugly.
Explicit is better than implicit.
Simple is better than complex.
Complex is better than complicated.
Flat is better than nested.
Sparse is better than dense.
Readability counts.
Special cases aren't special enough to break the rules.
Although practicality beats purity.
Errors should never pass silently.
Unless explicitly silenced.
In the face of ambiguity, refuse the temptation to guess.
There should be one-- and preferably only one --obvious way to do it.
Although that way may not be obvious at first unless you're Dutch.
Now is better than never.
Although never is often better than *right* now.
If the implementation is hard to explain, it's a bad idea.
If the implementation is easy to explain, it may be a good idea.
Namespaces are one honking great idea -- let's do more of those!
"""

with open('principles.txt', 'w') as f:
    f.write(principles)

```

In this example solution, we create/open a file called `principles.txt` with write privileges, and write the previously defined `principles` variable to the file using the `.write()` method for file objects.

</details>

---

### 45.  Create a function to count the number of each character of a given text of a text file

Using the text file you created in the last exercise, create a function that can count the number of occurrences of a certain character within the file's contents.

<details>

<summary>Click here for solutions:</summary>

```python
def how_many(char: str) -> int:
    """Returns the number of occurrences of a particular letter in the zen of python."""

    with open('principles.txt', 'r') as f:
        count = f.read().count(char)
    return count

print(how_many('e'))

```

</details>

---

### 46.  Create a function that uses regex

Create a function that uses regex to verify if a phone number is a valid format.

Do some research and learn a little regex.  Regex is a powerful tool for parsing text.

The format you are checking against should be 3 digits, a hyphen, 3 more digits, another hypen, and then 4 more digits.

Any other formats or non-numeric characters should cause your function to return False.

Examples:

| Input | Output |
| --- | --- |
| `'999-699-6969'` | `True` |
| `'9999-699-6969'` | `False` |
| `'999-6999999'` | `False` |

<details>

<summary>Click here for solutions:</summary>

```python
import re

def is_phone_number(number: str) -> bool:
    """Checks a phone number for formatting."""

    phone_number_pattern = re.compile('\d{3}-\d{3}-\d{4}')
    
    if phone_number_pattern.match(number):
        return True
    else:
        return False
```

</details>

---

### 47.  Create a function that given a year, returns every month that had/has a Friday the 13th  

Your function should return a list of month names.

Examples:

| Input | Output |
| --- | --- |
| `2019` | `['September', 'December']` |
| `1995` | `['January', 'October']` |
| `1980` | `['June']` |

<details>

<summary>Click here for solutions:</summary>

```python
from calendar import Calendar

def fridays(year: int) -> list:
    """Returns every month in a year that has a friday the 13th."""

    # Create a list of month names.  This will come in handy later.
    months = [
        'January',
        'February',
        'March',
        'April',
        'May',
        'June',
        'July',
        'August',
        'September',
        'October',
        'November',
        'December'
    ]

    # Create a generic Calendar object instance
    all_time = Calendar()

    
    # Use a class method to grab all the days of a particular year.  
    # For some reason this method returns a list where the entire year's months are kept in the first item, 
    # so we go ahead and set the year variable to the first index of the result of the function call.
    year = all_time.yeardays2calendar(year=year, width=12)[0]

    # Create empty result list
    result = []

    # Loop through each month in the year.  We use enumerate so that we will have the month's index number.  
    # This is what we will use to pull the month's name from the above list.
    for index, month in enumerate(year):
        for week in month:
            for day in week:

                # The day is a tuple containing the day number (out of the month) and weekday number, so we unpack it into two variables.
                day_number, weekday_number = day

                # If the day number is 13 and the weekday number is 4 (friday), then we use the index to pull the correct month name from the months list.
                if day_number == 13 and weekday_number == 4:
                    result.append(months[index])

    return result
```

</details>

---
```