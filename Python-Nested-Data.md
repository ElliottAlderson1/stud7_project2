**Useful Files**

[nested_data.py.txt](uploads/a1b7073f77a36afd73608fa89b9560c4/nested_data.py.txt)

[if_else_user_input.py.txt](uploads/5f8a0e54af8223c0d1a32c8e4929190a/if_else_user_input.py.txt)

[loops_and_ranges.py.txt](uploads/79a9180901a93b4102cd12eca4e9946c/loops_and_ranges.py.txt)

**Procedures/Commands**

Nested lists and dictionaries example below:
```
nested_data = [
     {
          'name': 'Alice',
          'age': 30,
          'email': alice@example.com
     },
     {
          'name': 'Bob'
          'age': 25
          'email': 'bob@example.com'
     }
]

print("Nested Data Example:")
for person in nested_data:
     print(f"Name: {person['name']}")
     print(f"Age: {person['age']}")
     print(f"Email: {person['email']}")
     print()
```