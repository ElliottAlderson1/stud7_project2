**Commands/Procedures**

- Add a new entry to the end of a list with ``.append()``
- Remove all entries from a list with ``.clear()``
- Create a copy of current list and place in new one with ``.copy()``
- Add items from existing list to current list with ``.extend()``
- Add a new entry to the position specified in a list with ``.insert()``
- Remove an entry and return value with ``.pop()``
- Remove the first matching entry in a list with ``.remove()``
- Count how many times an element appears in a list with ``.count()``
- sort elements in list with ``.sort()``
- Create a list that contains a certain amount of numbers using syntax like the below example:
```
numbers = list(range(101))
print(numbers[-3:])
```
- You can slice a certain range of the numbers inside a list using ``print(listname[x:y])`` where x and y are starting and ending values
- Print numbers by a certain interval from a list using ``print(listname[::x])`` where x is the interval
- Print every even number from a list using ``print(listname[1::2])`` starting from the beginning

Sorting with .reverse:
```
names1=["Alex", "Blake", "Cody“]
names1.reverse()
Print(names1)
["Cody", "Blake", "Alex"]

my_list = [1, 2, 4, 3, 5]
print(list(reversed(my_list)))
[5, 4, 3, 2, 1]
```

Sorting with .sort()
```
my_numbers = [3, 4, 2, 5, 1]
my_numbers.sort(reverse=True) or False
print(my_numbers)  output = [5, 4, 3, 2, 1]

sorted(my_numbers, reverse=True)  or False
output = [5, 4, 3, 2, 1]
```

![List_Modification](uploads/c453ebb11b5fe05f5668832565c6e80d/List_Modification.png)
