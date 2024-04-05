**Procedures and Commands**

- Put output followed by collection with a condition following it. 

- Creating a list with comprehension example below (sets use the same method but use { } instead):
```
numbers = [1,2,3,4,5]
square_numbers = [num * num for num in numbers]
print(square_numbers)
[1,4,9,16,25]
```

- Dictionaries using comprehension example below:
```
# Creates a dictionary full of only the odd numbers present in a list as keys and their cubes as values
input_list = [1,2,3,4,5,6,7]
dict_using_comp = {var:var ** 3 for var in input_list if var % 2 != 0}
print("Output Dictionary using dictionary comprehensions:", dict_using_comp)
```

- To avoid printing on new lines use ``end = ' '``, example below:
```
input_list = [1,2,3,4,4,5,6,7,7]
output_gen = (var for var in input_list if var % 2 == 0)
print("Output values using generator comprehensions.")
for var in output_gen:
     print(var, end = ' ')
```

- Syntax example for having a list of numbers making the variable equal to (num for num) in numbers if num is greater than the sum of all numbers, divided by how many numbers there are.
```
numbers = [1,2,3,4,5,6,7,8,9,10]
print(f'The sum is {sum(numbers)} divided by {len(numbers)} so if > 5 print it.')
result = [num for num in numbers if number > sum(numbers)/len(numbers)]
print(result)
```

**Examples**

![comprehensions](uploads/99c1f8a0e9617402c50d70bde52fcf53/comprehensions.png)

[comprehensions.py.txt](uploads/314254a14724f74721a2b5d3aea34e30/comprehensions.py.txt)