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

## Dynamic Typing
**Python is highly flexible about reassigning variables to different types. This is called as dynamic typing as variables can change types readily.**

Languages such C++ and Java are **statically-typed** and variables are stuck with their original assigned data type.

![Dynamic Typing](/assets/images/courses/mastering-python/notes-0000-ss-001.JPG){: .align-center}

## Parameters vs. Arguments

With respect to functions in Python, a parameter is a variable in a method definition whereas arguments are the data you pass into the method's parameters.

**Parameter** is variable in the declaration of function and **Argument** is the actual value of this variable that gets passed to a function.

## Encapsulation vs. Abstraction

Encapsultaion: Grouping of public and private attributes and methods into a programmatic class, making abstraction possible

Abstraction: Exposing only relevant data in a class interface, hiding private attributes and methods from users

## `self` keyword

The `self` keyword refers to the current class instance. `self` must always be the first parameter to `__init__` and any methods or properties on class instances.

## `__repr__` method in a class

By default, the representation of a class will show the type of the object instance and the address of the object. To override this with a meaningful representation, we can use the `__repr__ ` method.

## Inheritance

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

## Introduction to `super()`

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

## Multiple Inheritance

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

## Method Resolution Order (MRO)

Whenever you create a class, Python automatically sets a **Method Resolution Order** or **MRO** for that class, which is the order in which Python will look for methods on instances of that class.

Link to [Python Documentation](https://www.python.org/download/releases/2.3/mro/)

Programmatically MRO can be referenced in 3 ways:
* `_mro_` attribute on the class
* use the `mro()` method on the class
* use the built-in `help(cls)` method

![MRO references](/assets/images/courses/mastering-python/notes-0000-ss-002.JPG){: .align-center}

## Properties in a class

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

## Polymorphism

A key principle of object oriented programming is the idea of polymorphism i.e. an object can take on many (poly) forms (morph).

Following are 2 important practical applications:
1. The same class method works in a similar way for different classes - **Method Overriding**

![Method](/assets/images/courses/mastering-python/notes-0000-ss-003.JPG){: .align-center}

2. The same operation works for different kinds of objects - **Magic Methods** (also called dunder i.e. double underscore methods)

![Operation](/assets/images/courses/mastering-python/notes-0000-ss-004.JPG){: .align-center}

Example of a magic method is 'len' ==> `__len__` or '+' ==> `__add__`

## Iterator vs. Iterable

* Iterator - an object that can be iterated upon. An object which returns data, one element at a time when the `next()` method is called on it.

* Iterable - An object which will return an `Iterator` when `iter()` method is called on it.

`iter()` returns an **iterator** on a **iterable** object.

Example:

`"HELLO"` is an iterable, but it is not an iterator. `iter("HELLO")` returns an iterator.

```python
>>> name = "Curry"

>>> next(name)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: 'str' object is not an iterator

>>> it = iter(name)
>>> it
<str_iterator object at 0x03375650>

>>> next(it)
'C'
>>> next(it)
'u'
>>> next(it)
'r'
>>> next(it)
'r'
>>> next(it)
'y'
```

```python
>>> nums = [1, 2, 3, 4, 5]

>>> next(nums)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: 'list' object is not an iterator

>>> it = iter(nums)
>>> it
<list_iterator object at 0x03375610>

>>> next(it)
1
>>> next(it)
2
>>> next(it)
3
>>> next(it)
4
>>> next(it)
5
>>> next(it)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
StopIteration
```

## Generators

* Generators are iterators
* Generators can be created with generator functions
* Generator functions use the yield keyword
* Generators can be created with generator expressions


### Functions vs. Generator Functions

| Functions | Generator Functions |
|---|---|
| Uses `return` | Uses `yield` |
| returns once | can yield multiple times |
| when invoked, returns the return value | When invoked, returns a generator |

Example:

If you write a function and put `yield` in it, it returns a generator object. It keeps track of the state. It pauses after the `yield` is called until the `next()` is called. It takes up less memory as a result.

```python
>>> def count_up_to(max):
...   count = 1
...   while count <= max:
...     yield count
...     count += 1
...

>>> counter = count_up_to(5)
>>> counter
<generator object count_up_to at 0x0362B2D0>

>>> next(counter)
1
>>> next(counter)
2
>>> next(counter)
3
>>> next(counter)
4
>>> next(counter)
5
>>> next(counter)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
StopIteration
```

The `__iter__` and `__next__` functions are already defined. This can be checked by using the `help` method.

```python
>>> help(counter)
Help on generator object:

count_up_to = class generator(object)
 |  Methods defined here:
 |
 |  __del__(...)
 |
 |  __getattribute__(self, name, /)
 |      Return getattr(self, name).
 |
 |  __iter__(self, /)
 |      Implement iter(self).
 |
 |  __next__(self, /)
 |      Implement next(self).
 |
 |  __repr__(self, /)
 |      Return repr(self).
 |
 |  close(...)
 |      close() -> raise GeneratorExit inside generator.
 |
 |  send(...)
 |      send(arg) -> send 'arg' into generator,
 |      return next yielded value or raise StopIteration.
 |
 |  throw(...)
 |      throw(typ[,val[,tb]]) -> raise exception in generator,
 |      return next yielded value or raise StopIteration.
 |
 |  ----------------------------------------------------------------------
 |  Data descriptors defined here:
 |
 |  gi_code
 |
 |  gi_frame
 |
 |  gi_running
 |
 |  gi_yieldfrom
 |      object being iterated by yield from, or None
```

Another example:

```python
>>> def yes_or_no():
...     answer = "yes"
...     while True:
...         yield answer
...         answer = "no" if answer == "yes" else "yes"
...
>>> gen = yes_or_no()
>>> next(gen)
'yes'
>>> next(gen)
'no'
>>> next(gen)
'yes'
>>> next(gen)
'no'
>>> next(gen)
'yes'
>>> next(gen)
'no'
>>> next(gen)
'yes'
```

Another example of using generators to save memory usage:

```python
>>> def fib_gen(max):
...     x = 0
...     y = 1
...     count = 0
...     while count < max:
...         yield x
...         x, y = y, x + y
...         count+=1
...

>>> fib = fib_gen(1000000)
>>> next(fib)
0
>>> next(fib)
1
>>> next(fib)
1
>>> next(fib)
2
>>> next(fib)
3
>>> next(fib)
5
>>> next(fib)
8
>>> next(fib)
13
>>> next(fib)
21
>>> next(fib)
34
>>> next(fib)
55

# to continuously print 1000000 fibonacci numbers:
>>> for n in fib_gen(1000000):
...    print(n)
...

# numbers .......................
```
## Decorators

* Decorators are Functions
* Decorators wrap other functions and enhance their behavior
* Decorators are examples of higher order Functions
* Decorators have their own syntax, using `@`
* Higher Order functions:
  * Functions that take in another function as a parameter
  * Functions that return another function

Example:
Below are 2 ways of using decorators:
1. Without the `@` syntax:

```python
def be_polite(func):
  def wrapper():
    print("What a pleasure to meet you!")
    func()
    print("Have a great day!")
  return wrapper

def greet():
  print("I am a Data Geek")

# below is decorating a function without using the `@` syntax
greet = be_polite(greet)
greet()
```

2. Using the `@` syntax:

```python
def be_polite(func):
  def wrapper():
    print("What a pleasure to meet you!")
    func()
    print("Have a great day!")
  return wrapper

@be_polite
def greet():
  print("I am a Data Geek")

greet()
```



[Mastering Python - Home](/mastering-python/){: .btn .btn--primary .btn--large}{: .align-center}
