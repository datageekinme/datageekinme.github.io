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

### Introduction to `**kwargs`

* A special operator we can pass to functions
* Gathers remaining keyword arguments as a dictionary

Example:

```python
>>> def fav_sports(**kwargs):
...     for person, sport in kwargs.items():
...             print(f"{person}'s favorite sport is {sport}")
...
>>> fav_sports(john="baseball", jane="softball", jim="basketball", jack="football")
john's favorite sport is baseball
jane's favorite sport is softball
jim's favorite sport is basketball
jack's favorite sport is football
>>> fav_sports(john="baseball", jane="softball", jim="basketball")
john's favorite sport is baseball
jane's favorite sport is softball
jim's favorite sport is basketball
>>> fav_sports(john="baseball")
john's favorite sport is baseball
```

```python
>>> def combine_words(word, **kwargs):
...     if "prefix" in kwargs:
...         return kwargs.get("prefix") + word
...     elif "suffix" in kwargs:
...         return word + kwargs.get("suffix")
...     return word
...
>>> combine_words('child')
'child'
>>> combine_words('child', prefix='man')
'manchild'
>>> combine_words('child', suffix='ish')
'childish'
>>> combine_words('work', suffix='er')
'worker'
>>> combine_words('work', prefix='home')
'homework'
```

```python
>>> def calculate(**kwargs):
...     result = 0
...     first = kwargs['first']
...     second = kwargs['second']
...     if kwargs['operation'] == 'add':
...         result = first + second
...     elif kwargs['operation'] == 'subtract':
...         result = first - second
...     elif kwargs['operation'] == 'multiply':
...         result = first * second
...     elif kwargs['operation'] == 'divide':
...         result = first / second
...
...     if kwargs['make_float']:
...         result = float(result)
...     else:
...         result = int(result)
...
...     if kwargs.get('message'):
...         message = kwargs['message']
...         return '{} {}'.format(message, result)
...     else:
...         return 'The result is {}'.format(result)
...
>>> calculate(make_float=False, operation='add', message='You just added', first=2, second=4)
'You just added 6'
>>>
>>> calculate(make_float=True, operation='divide', first=3.5, second=5)
'The result is 0.7'
```

### Parameter Ordering

Ordering of parameters matters as it can break the code.

Following is the order:
1. parameters
2. `*args`
3. default parameters
4. `**kwargs`

### List / Tuple Unpacking:

Passing a collection as below to `*args` results in `unsupported operand type` error as seen below.

In order to handle collections, use `*` before argument like `sumAll(*nums)`
```python
>>> def sumAll(*args):
...     print(args)
...     total = 0
...     for num in args:
...         total += num
...     print(total)
...
>>>
>>> nums = [1,2,3,4,5,6]
>>> sumAll(nums)
([1, 2, 3, 4, 5, 6],)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "<stdin>", line 5, in sumAll
TypeError: unsupported operand type(s) for +=: 'int' and 'list'
>>>
>>> sumAll(*nums)
(1, 2, 3, 4, 5, 6)
21
```

### Dictionary Unpacking:

`**` will unpack a dictionary to keyword arguments, like `*` unpacks a list or a tuple.

```python
>>> def display_names(first, second):
...     print(f"{first} says hello to {second}")
...
>>> names = {'first': 'John', 'second': 'Smith'}
>>> display_names(**names)
John says hello to Smith
>>>
```

```python
>>> def add_and_multiply(a,b,c,**kwargs):
...     print(a+b*c)
...     print("OTHER STUFF.....")
...     print(kwargs)
...
>>> data=dict(a=1,b=2,c=3)
>>> add_and_multiply(**data)
7
OTHER STUFF.....
{}
>>> data=dict(a=1,b=2,c=3,d=55,name='John')
>>> add_and_multiply(**data)
7
OTHER STUFF.....
{'d': 55, 'name': 'John'}
>>> add_and_multiply(**data,cat='blue')
7
OTHER STUFF.....
{'d': 55, 'name': 'John', 'cat': 'blue'}
```

[Mastering Python - Home](/mastering-python/){: .btn .btn--primary .btn--large}{: .align-center}
