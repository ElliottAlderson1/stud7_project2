**Useful Files**

[dictionaries.py](uploads/40c2e4c4e3f61ce37840b13474e5faa5/dictionaries.py)

**Procedures/Commands**

Dictionaries are created like so below. _There are no duplicates in dictionaries_

```
dict1={101:'ram',
       102:'sham',
       103:'ravi'}
print(dict1)
dict1[103]
```
Access data using ``.keys()``, ``.values()``, and ``.items()``
```
print(dog4.keys()) -> returns all keys
dict_values(['name', 'breed', 'temperament'])

print(dog4.values()) -> returns all values
dict_values(['Rex', 'Newfoundland', 'amiable'])

print(dog4.items()) -> returns all the (key,value) pairs in the dictionary
dict_values(['name', 'Rex']), (['breed', 'Newfoundland]), (['temperament', 'amiable'])
```

Sort by key example below:

```
incomes = {'apple': 5600.00, 'orange': 3500.00, 'banana': 5000.00}
for key in sorted(incomes):
     print(key, '->', incomes[key])

apple -> 5600.0
banana -> 5000.0
orange -> 3500.0
```

Sort by values example below:

```
people = {3: 'Jim', 2: 'Jack', 4: 'Jane', 1: 'Jill'}
sorted(people)
[1, 2, 3, 4]

sorted_people = sorted(people.items(), key=lambda item: item[1])
dict(sorted_people)
{2: 'Jack', 4: 'Jane', 1: 'Jill', 3: 'Jim'}
```

- Add to a dictionary from an existing list, set, or another dictionary using ``.update()``
     - Example is ``dict1.update({'name': 'mike'})``
- Create a variable and assign a copy of the dictionary keys to it **(copy's changes don't affect original)** using ``.setdefault()``

**Delete key pairs using the following functions:**

- ``.pop()``
- ``del``
- ``.popitem()``
- ``.clear()``