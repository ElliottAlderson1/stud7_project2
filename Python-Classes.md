**Procedures/Commands**

- Use two functions to list attributes of an instance/object:
     - ``vars()`` which displays the attribute of an instance in directory form
     - ``dir()`` which displays is not limited to instance, displays the class attributes and attributes of its ancestor classes

- ``Class Attributes`` are values that apply to the whole class, defined right above the ``__init__``
- ``Instance Attributes`` are values that apply to each instance individually and no affect other instances
- ``Class / Instance Methods`` are functions that call upon the specific variables. Example below:
```
class Student():
     name = 'unknown' # class attribute
     def __init__(self, age=0, sex='?'):
          self.age = 25 # instance attribute

     def speak(self):
          print("Hello, I'm", self.age)
     
     @classmethod
     def tostring(cls): #cls since we don't want to use class
          print('Student Class Attributes: name=', cls.name)

Student.tostring() # Student Class Attributes: name=unknown
student1 = Student("Guest")
student1.speak()
```
**Examples**

[class_inheritance.py.txt](uploads/80bbadae8a0c595aed37ea6fac2dbbcf/class_inheritance.py.txt)

[class_instances.py.txt](uploads/ad5497bfc0a850cac40a24447bdab344/class_instances.py.txt)

[class_variables.py.txt](uploads/8a69d0211bc225ccdb7400c9d01f404b/class_variables.py.txt)