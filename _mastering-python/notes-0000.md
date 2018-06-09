---
title: "Mastering Python"
permalink: /mastering-python/0000/
header:
  overlay_image: "/assets/images/logo/overlay-image.png"
  overlay_filter: rgba(0, 0, 255, 0.5)
  teaser: "/assets/images/misc/notes-1.png"
toc: true
excerpt: "Glossary of terms in Python"
---

## Glossary

### Dynamic Typing
**Python is highly flexible about reassigning variables to different types. This is called as dynamic typing as variables can change types readily.**

Languages such C++ and Java are **statically-typed** and variables are stuck with their original assigned data type.

![Dynamic Typing](/assets/images/courses/mastering-python/notes-0000-ss-001.JPG){: .align-center}

### Parameters vs. Arguments

With respect to functions in Python, a parameter is a variable in a method definition whereas arguments are the data you pass into the method's parameters.

**Parameter** is variable in the declaration of function and **Argument** is the actual value of this variable that gets passed to a function.

### Encapsulation vs. Abstraction

Encapsultaion: Grouping of public and private attributes and methods into a programmatic class, making abstraction possible

Abstraction: Exposing only relevant data in a class interface, hiding private attributes and methods from users

### `self` keyword

The `self` keyword refers to the current class instance. `self` must always be the first parameter to `__init__` and any methods or properties on class instances.

### `__repr__` method in a class

By default, the representation of a class will show the type of the object instance and the address of the object. To override this with a meaningful representation, we can use the `__repr__ ` method.

### Inheritance

A key feature of object oriented programming is the ability to define a class which inherits from another class i.e. a "base" or "parent" class. Example, a base class could be 'User' with classes like specific roles i.e. 'Administrator', 'Developer', 'Analyst' inheriting attributes and methods of the 'User' class.

In Python, inheritance works by passing the parent class as an argument to the definition of a child class.

```python
class User:
  # class attributes and methods
  pass

class Administrator(User):
  # admin class attributes and methods
  pass
```

### Introduction to `super()`

Inheritance Example Using Super()

It calls the `__init__` of the parent class which is 'Animal' in the example below:

```python
class Animal:
	def __init__(self, name, species):
		self.name = name
		self.species = species

	def __repr__(self):
		return f"{self.name} is a {self.species}"

	def make_sound(self, sound):
		print(f"this animal says {sound}")

class Cat(Animal):
	def __init__(self, name, breed, toy):
		super().__init__(name, species="Cat") # Call init on parent class
		self.breed = breed
		self.toy = toy

	def play(self):
		print(f"{self.name} plays with {self.toy}")

blue = Cat("Blue","Scottish Fold", "String")
blue.play()
```

### Multiple Inheritance

In case of multiple inheritance, if using the keyword `super()` to run the `__init__`, it will pick the first class that is passed in the arguments. In the below example, 'Penguin' class's super will refer to 'Ambulatory' class. But, Penguin will have access to all the methods and attributes of both 'Ambulatory' and 'Aquatic' classes.

```python
class Animal:
  pass

class Aquatic(Animal):
  pass

class Ambulatory(Animal):
  pass

class Penguin(Ambulatory, Aquatic):
  pass
```

### Method Resolution Order (MRO)

Whenever you create a class, Python automatically sets a **Method Resolution Order** or **MRO** for that class, which is the order in which Python will look for methods on instances of that class.

Link to [Python Documentation](https://www.python.org/download/releases/2.3/mro/)

Programmatically MRO can be referenced in 3 ways:
* `_mro_` attribute on the class
* use the `mro()` method on the class
* use the built-in `help(cls)` method

![MRO references](/assets/images/courses/mastering-python/notes-0000-ss-002.JPG){: .align-center}

### Properties in a class

Example:

```python
class Human:

  def __init__(self, first, last, age):
    self.first = first
    self.last = last
    if age >= 0:
      self._age = age
    else:
      self._age = 0

  @property # creates a property that can be used as a getter and setter
  def age(self):
    return self._age

  @age.setter
  def age(self, value)
    if value >= 0:
      self._age = value
    else:
      raise ValueError("Age cannot be negative!")

  @property
  def full_name(self):
    return "{} {}".format(self.first, self.last)

  @full_name.setter
  def full_name(self, name):
    self.first, self.last = name.split(" ")

jane = Human("Jane", "Smith", 34)
print(jane.age)
jane.age = -100 # will raise a ValueError
print(jane.age)
print(jane.full_name)
jane.full_name = "Jane Doe"
print(jane.full_name)
print(jane.__dict__)
```

### Polymorphism

A key principle of object oriented programming is the idea of polymorphism i.e. an object can take on many (poly) forms (morph).

Following are 2 important practical applications:
1. The same class method works in a similar way for different classes - **Method Overriding**

![Method](/assets/images/courses/mastering-python/notes-0000-ss-003.JPG){: .align-center}

2. The same operation works for different kinds of objects - **Magic Methods** (also called dunder i.e. double underscore methods)

![Operation](/assets/images/courses/mastering-python/notes-0000-ss-004.JPG){: .align-center}

Example of a magic method is 'len' ==> `__len__` or '+' ==> `__add__`



[Mastering Python - Home](/mastering-python/){: .btn .btn--primary .btn--large}{: .align-center}
