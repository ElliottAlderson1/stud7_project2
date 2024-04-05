## Virtual Environments
- ```python3 -m pip install --upgrade pip --user``` - install and upgrade pip
   - ```-m``` - specifies module
- ```python3 -m venv <name>``` - creates a new virtual environment
- ```source <path to bin/activate>``` - Activates a virtual environment
- After creating a new virtual environment it is important to update pip.
   - ```pip install --upgrade pip``` - upgrade pip
- ```pip list``` - list installed packages
- ```pip install <module>``` - install listed module/s
- ```pip show <module>``` - show information about the module
- ```pip uninstall <module> -y``` - uninstall module
   - ```-r``` - used to specify a requirements file.
- ```pip freeze > <file>``` saves installed modules to specified file
- ```deactivate``` - deactivates the virtual environment
- There are global and local environments. When you are calling ```pip3/python3``` you are referring to the global environment. When you call ```pip/python``` you are referring to the local environment.


## Operators
- Arithmetic Operators
   - + - add
   - - - subtract
   - * - multiply
   - / - divide
   - % - modulo
   - // - integer division
   - ** - exponent
- Comparison Operators
   - == - __eq__ - equal to
   - != - __ne__ - not equal to
   - \> - __gt__ - greater than
   - < - __lt__ - less than
   - \>= - __ge__ - greater than or equal to
   - <= - __le__ - less than or equal to
   - Able to overload comparison operators by defining the respective function in a class.
- Logical Operators
   - and - only true if both are true
   - not - opposite of input
   - or - true if both are not false
   - There is a priority NOT > AND > OR
- Bitwise Operators
   - & - AND
   - | - OR
   - ^ - XOR
   - ~ - NOT
   - \>> - BINARY RIGHT SHIFT
   - << - BINARY LEFT SHIFT
- Order of Operations
   - ```(), **, ~, *, /, //, %, +, -, <<, >>, &, ^, |, ==, !=, >, >=, <, <=, is, is not, in, not in, not, and, or```


## Strings
- ```+``` - concatenates strings
- string interpolation
  - operator - ```sayHi = "hello, %s!" %s
     - %s - string
     - %c - character
     - %i/d - integer
     - %f - float
     - %e - exponent
     - %x - hexadecimal
     - %o - octal
  - .format - ```str1 = "{} uses {}.".format("New York", "EST")
  - f-strings - ```str = f'1 {unit}'
  - template - t1 = Template("Destination: $place.")
  - Slicing - returns string at the provided indexes
>>```python
>>s = 'foobar'
>>s[2:5]
>>'oba'
>>```
- Methods:
  - ```capitalize()``` - Capitalize beginning of sentences.
  - ```casefold()``` - More aggressive lower method.
  - ```count(ch)``` - return the number of chars in the string.
  - ```find(pattern)``` - returns lowest index found at the beginning of the pattern.
  - ```index(pattern)``` - Like find but raises an error if not found.
  - ```isalnum()``` - returns true if all characters in string are alphanumeric
  - ```isalpha()``` - returns true if all characters are alphabetic.
  - ```isascii()``` - returns true if all characters are ASCII
  - ```isdecimal()``` - returns true if all characters are decimal characters.
  - ```isdigit()``` - returns true if all characters are digits
  - ```islower()``` - returns true if all characters are lowercase
  - ```isupper()``` - returns true if all characters are uppercase
  - ```upper()``` - returns string in uppercase
  - ```lower()``` - returns string in lowercase
  - ```replace(pattern, pattern)``` - replaces the first pattern with the second.
  - ```lstrip(<chars>)``` - removes leading characters from the string
  - ```partition(pattern)``` - breaks apart the string at the first occurrence of pattern returns as a 3 part tuple. The portion before will be in the first part, the pattern in the middle, and the rest afterwards.
  - ```title()``` - return string with every first letter of all words capitalized.
  - ```swapcase()``` - upper to lower, lower to upper.
  - ```split(delimiter)``` - returns list with string broken up based on delimiter
  - ```"".join(<list/strings>)``` - used to join elements with the supplied string.

## Tuples
- Tuples are ordered, duplicates are allowed, and they are immutable.
- Tuples are created by calling the ```tuple()``` constructor or using ```( )```

## Lists
- Lists are ordered, mutable, and may contain duplicate values.
- Lists are created by calling the ```list()``` constructor or using ```[]```
- Methods:
   - ```append(x)``` - Appends item to the end of the list.
   - ```count(x)``` - Counts how many time and element appears in the list.
   - ```index(x)``` - Returns the first index at which the given element occurs.
   - ```pop()``` - Removes and returns the last element.
   - ```reverse()``` - Reverses the order of the elements.
   - ```sort()``` - Sorts the elements of a list. Numerical.
      - ```sorted()``` - Sorts string elements in a list in ascending order.
   - ```extend()``` - Adds contents of List2 to the end of List1.
   - ```clear()``` - This function is used to erase all the elements in the list. After this operation, the list will be empty.


## Dictionaries
- Ordered, Key Value Pair, Mutable, No Duplicates.
- Able to add or remove items.
- Dictionaries cannot have two items with the same key.
   - Duplicate values will overwrite existing values.
- Can be initialized by the constructor ```dict()``` or ```{ }```
- ```keys()``` - returns all keys in the dictionary.
- ```values()``` - Returns all the values in the dictionary.
- ```items()``` - Returns all key/value pairs in the dictionary.
- ```sorted()``` - takes the keys from the dictionary and sorts them. Returns a list of the keys in sorted order.
- You can sort values in a dictionary by using a lambda function.
>```python
>sorted_people = sorted(people.items(), key = lambda item: item[1])
>dict(sorted_people)
>```
- ```update()``` - Add to dictionary from another list, set, or dictionary.
- ```setdefault()``` - Create a variable and assign a copy of the dictionary keys to it.
   - Changes to copy do not affect original.
- ```pop(), del, popitem(), clear()``` - These methods can all be used to remove an item from a dictionary.