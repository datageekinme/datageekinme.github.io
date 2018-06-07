---
title: "Python: Functions"
permalink: /mastering-python/0004/
header:
  overlay_image: "/assets/images/logo/overlay-image.png"
  overlay_filter: rgba(0, 0, 255, 0.5)
  teaser: "/assets/images/misc/notes-1.png"
excerpt: "Functions Explained"
toc: true
---

## Introduction to Functions

* A process for executing a task
* It can accept input and return an output
* Useful for executing similar procedures over and over

### Why use functions

* To stay **DRY** - Don't Repeat Yourself! (Opp. of **WET** - Write Everything Twice)
* Clean up and prevent code duplication
* Abstract away code for other users. Also can be used for reusability. For example, specific type of logging.
* Helps in organizing the code

### Structure of a function

```python
def <function-name> () :
  # block of code
```

### Documenting functions

You can use `""" <text> """` in the first line of the function code block to document the functionality of a function. It's essential when writing complex functions.

Can be leveraged using the `__doc__` method as follows:

```python
>>> def greeting():
...     """A simple function to greet a person"""
...     return "Hello!"
...
>>> greeting.__doc__
'A simple function to greet a person'
>>> greeting()
'Hello!'
```

### Returning a value from a function

`return` keyword can be used to do so. Using this keyword, exits the function. Pops the function off of the call stack.

```python
>>> def squareOf7():
...     7 ** 2
...
>>> squareOf7()
>>>
>>> def squareOf7():
...     return 7 ** 2
...
>>> squareOf7()
49
```
#### Common `return` mistake

`return` is not placed in the correct block.
```python
>>> def sumOddNums(nums):
...     total = 0
...     for num in nums:
...             if num % 2 != 0:
...                     total += num
...             return total # `return` placed in the wrong block
...
>>> print(sumOddNums([1,2,3,4,5,6,7]))
1
>>> def sumOddNums(nums):
...     total = 0
...     for num in nums:
...             if num % 2 != 0:
...                     total += num
...     return total
...
>>> print(sumOddNums([1,2,3,4,5,6,7]))
16
```

### Default Parameters

Specifying default arguments for a parameter. (see [Glossary](/mastering-python/notes-0000) to understand difference between parameter and argument)

```python
>>> def exponent(num, power = 2):
...   return num ** power
...
>>> print(exponent(2,3))
8
>>> print(exponent(3))
9
>>> print(exponent(7))
49
```

Why have default parameter values?
* Allows you to be more defensive
* Avoids errors with incorrect Parameters

Default parameters can be anything! - functions, lists, dictionaries, strings, booleans, etc.

```python
>>> def add(a, b):
...   return a + b
...
>>> def sub(a, b):
...   return a - b
...
>>> def math(a, b, fn=add):
...   return fn(a, b)
...
>>> print(math(2, 2))
4
>>> print(math(2, 2, add))
4
>>> print(math(2, 2, sub))
0
```

#### Keyword arguments

If you know the parameter name, you can provide arguments using the parameter name and then the order of the arguments doesn't matter.

It's very useful when passing a dictionary to a function and unpacking it's values.

```python
>>> def fullName(first, last):
...     return f"Your name is {first} {last}!"
...
>>> fullName(first='John', last='Smith')
'Your name is John Smith!'
>>> fullName(last='Smith',first='John')
'Your name is John Smith!'
```

**Note:**
* When you define a function and use an `=`, you are setting a default parameter
* when you invoke a function and use an `=`, you are making a keyword argument

### Scope:

Variables created in a function are scoped in that function. Meaning, the variable is available only within the code block of that function.


```python
>>> name1 = 'John'
>>> def greeting():
...   return f"Hello {name1}"
...
>>> greeting()
'Hello John'
>>> print(name1)
John
```
```python
>>> def greeting():
...   name = 'John'
...   return f"Hello {name}"
...
>>> greeting()
'Hello John'
>>> print(name)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: name 'name' is not defined
```

Using global variables:

```python
>>> total = 0
>>> def increment():
...     total += 1
...     return total
...
>>> increment()
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "<stdin>", line 2, in increment
UnboundLocalError: local variable 'total' referenced before assignment
```

```python
>>> total = 0
>>> def increment():
...     global total
...     total += 1
...     return total
...
>>> increment()
1
```

### Introduction to `*args`

* A special operator that we can pass to Functions
* Gathers remaining arguments as a tuple

Examples:

```python
>>> def sumNums(*args):
...     total = 0
...     for num in args:
...             total += num
...     return total
...
>>> print(sumNums(4, 6, 9, 4, 10))
33
>>> print(sumNums(4, 6))
10
```

```python
>>> def sumNums(num1, *args):
...     print(num1)
...     total = 0
...     for num in args:
...             total += num
...     return total
...
>>>
>>> print(sumNums(4, 6, 9, 4, 10))
4
29
>>> print(sumNums(4, 6))
4
6
```

[Mastering Python - Home](/mastering-python/){: .btn .btn--primary .btn--large}{: .align-center}
