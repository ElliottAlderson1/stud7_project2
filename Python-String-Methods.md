**Relevant Files**

[string_splicing.py.txt](uploads/b7955745ae2ced2384f1f8edc5bb7c26/string_splicing.py.txt)

[string_exercises.py.txt](uploads/00cc0c5f065bd16e3bf994bc8bbd5f17/string_exercises.py.txt)

[integers_and_floats.py.txt](uploads/1fd066ea8c7a377ae579abb1eb93d8d7/integers_and_floats.py.txt)

**Procedures/Commands**

- Most common way of building strings are with **f-strings** which have placeholders 
```
a = 5
b = 10
string = f'Five plus ten is {a + b} and not {2 * (a + b)}.’
print(string)
'Five plus ten is 15 and not 30.’
```

See method examples below:
```
"Hello World".captialized() -> Hello world
"Hello World".casefold() -> hello world
"Hello World".count("o") -> 2
"Hello World".find("World") -> 6
"Hello World".index("Hello") -> 0
"Hello World".isalnum() -> False
"Hello World".isalpha() -> False
"Hello World".isascii() -> True
"Hello World".isdecimal() -> False
"Hello World".isdigit() -> False
"Hello World".isidentifier() -> False
"Hello World".islower() -> True
"Hello World".isnumeric() -> False
"Hello World".isprintable() -> True
```

See change case examples below:
```
string.lower() -> Converts all letters to lowercase
string.upper() -> Converts all letters to uppercase
string.title() -> Converts all letters to titlecase
string.capitalize() -> Converts first letter to uppercase
string.swapcase() -> Swaps the case of all letters
string.casefold() -> The string in lowercase letters
```

See find examples below:
```
string.find () -> The position of the specified value in the string
string.index() -> The position of the specified value in the string
string.rfind() -> The position of the specified value in the string searching from the end
string.rindex() -> The position of the specified value in the string searching from the end
string.replace() -> Replace occurance with another
```

See layout examples below:
```
string.center() -> A centered string
string.format_map() -> String formatted as specified
string.format() -> String formatted as specified
string.ljust() -> Left-justified version of the string
string.rjust() -> Right-justified version of the string
string.lstrip() -> Trims leading characters from a string
```

See transform examples below:
```
string.encode() -> String encoded in the specified way
string.expandtabs() -> Sets tab size to specified number of white spaces (default 8)
string.join() -> String containing an iterable's elements joined together
string.maketrans() -> A translation table
string.partition() -> Three-element tuple with text before string, the string, and the text after
string.replace() -> String with specified value replaced with replacement value
string.rpartition() -> Three-element tuple with text before string, the string, and the text after
string.split() -> String separated into different lists
```

**Interpolation Operators:**
     - ``%s`` for strings
     - ``%c`` for single characters
     - ``%i or %d`` for integers
     - ``%f`` for floats
     - ``%e`` for exponentials
     - ``%x`` for hexadecimals
     - ``%o`` for octals

Example of Interpolation Operators:
```
myMsg = "%s, you have %i fingers and %d thumbs." %("Sam", 8, 2)
print(myMsg) 
Sam, you have 8 fingers and 2 thumbs.
```

See template string examples below:
```
from string import Template  
t1 = Template("Destination: $place.") 
t1.substitute(place=input("Enter the destination: "))
Enter the destination: Tampa
'Destination: Tampa.’

\\OR\\

from string import Template
s = Template('$who likes $what’)
print(s.safe_substitute(who='Mike', what='free hotdogs!'))
'Mike likes free hotdogs!'
```