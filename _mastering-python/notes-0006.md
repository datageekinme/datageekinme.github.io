---
title: "Python: Error Handling"
permalink: /mastering-python/0006/
header:
  overlay_image: "/assets/images/logo/overlay-image.png"
  overlay_filter: rgba(0, 0, 255, 0.5)
  teaser: "/assets/images/misc/notes-1.png"
excerpt: "Debugging and Error Handling"
toc: true
---

## Common Error Types

### SyntaxError
Occurs when Python encounters incorrect syntax (something it cannot parse). Usually due to typos or not knowing Python well enough

```python
>>> def test ((:
  File "<stdin>", line 1
    def test ((:
              ^
SyntaxError: invalid syntax
```

### NameError
Occurs when a variable is not defined i.e. it hasn't been assigned

```python
>>> test
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: name 'test' is not defined
```

### TypeError
Occurs when an operation or function is applied to the wrong type. Python cannot interpret an operation on two data types.

```python
>>> len(10)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: object of type 'int' has no len()

>>> "awesome" + []
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: must be str, not list
```

### IndexError
Occurs when we access an element in a list using an invalid index i.e. an index that is outside the range of the list or string

```python
>>> a = [1,2,3]
>>> a[3]
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
IndexError: list index out of range
```

### ValueError
Occurs when a built-in operation or function receives an argument that has the right type but inappropriate value

```python
>>> int('awesome')
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ValueError: invalid literal for int() with base 10: 'awesome'
```

### KeyError
Occurs when a dictionary does not have a specific key

```python
>>> d = {}
>>> d['geek']
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
KeyError: 'geek'
```

### AttributeError
Occurs when a variable does not have an attribute

```python
>>> 'geek'.data
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
AttributeError: 'str' object has no attribute 'data'
```

### ZeroDivisionError
Occurs when a number is being divided by 0 (zero)

```python
>>> 5/0
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ZeroDivisionError: division by zero
```

## Raising Own Exceptions

We can also throw errors using the `raise` keyword. This is helpful when creating your own kinds of exceptions and error messages

Example: `raise ValueError('invalid value')`

```python
>>> def colorize(text, color):
...     colors = ('cyan','yellow','blue','green','magenta','red')
...     if type(text) is not str:
...         raise TypeError("text must be instance of str")
...     if type(color) is not str:
...         raise TypeError("color must be instance of str")
...     if color not in colors:
...         raise ValueError("color is invalid color")
...     print(f"Printed {text} in {color}")
...

>>> colorize("hello", "red")
Printed hello in red

>>> colorize(34, "red")
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "<stdin>", line 4, in colorize
TypeError: text must be instance of str

>>> colorize("34", 34)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "<stdin>", line 6, in colorize
TypeError: color must be instance of str

>>> colorize("34", "maroon")
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "<stdin>", line 8, in colorize
ValueError: color is invalid color

>>> colorize("34", "green")
Printed 34 in green
```

## Handling errors

Errors can be handles using the `try.. except..` blocks.

**Sample:**
```python
try:
  datageek
except:
  print("PROBLEM!")
print("after the try")
```

Example:

```python
>>> def get(d, key):
...     try:
...         return  d[key]
...     except KeyError:
...         return None
...

>>> d = {'name': 'Ricky'}

>>> print(get(d, 'name'))
Ricky

>>> print(get(d, 'city'))
None
 ```

 `try.. except.. else.. finally..`

 ```python
 >>> try:
 ...     num = int(input("please enter a number: "))
 ... except:
 ...     print("That's not a number!")
 ... else:
 ...     print("I'm in the else!!")
 ... finally:
 ...     print("Runs no matter what!")
 ...
 please enter a number: 10
 I'm in the else!!
 Runs no matter what!
 
 >>> try:
 ...     num = int(input("please enter a number: "))
 ... except:
 ...     print("That's not a number!")
 ... else:
 ...     print("I'm in the else!!")
 ... finally:
 ...     print("Runs no matter what!")
 ...
 please enter a number: abc
 That's not a number!
 Runs no matter what!
 ```

## Debugging with pdb

We can debug a python program step-by-step by placing the following code within the program.

NOTE: Be careful with the variables you declare. For example if `c` is a variable defined, typing `c` in pdb will consider the action as `c ==> continue`. You should then use `p` to print the variable "c", as follows: `p c`

 `import pdb; pdb.set_trace()`

 For example:

 ```python
 # debug.py
 import pdb
 first = 'First'
 second = 'Second'
 pdb.set_trace()
 result = first + second
 third = 'Third'
 result += third
 print(result)
 ```

 ```shell
 PS C:\Users\datag\Desktop\python-practice-code> python debug.py
> c:\users\datag\desktop\python-practice-code\debug.py(6)<module>()
-> result = first + second
(Pdb) first
'First'
(Pdb) second
'Second'
(Pdb) l
  1     # debug.py
  2     import pdb
  3     first = 'First'
  4     second = 'Second'
  5     pdb.set_trace()
  6  -> result = first + second
  7     third = 'Third'
  8     result += third
  9     print(result)
[EOF]
(Pdb) result
*** NameError: name 'result' is not defined
(Pdb) n
> c:\users\datag\desktop\python-practice-code\debug.py(7)<module>()
-> third = 'Third'
(Pdb) result
'FirstSecond'
(Pdb) third
*** NameError: name 'third' is not defined
(Pdb) n
> c:\users\datag\desktop\python-practice-code\debug.py(8)<module>()
-> result += third
(Pdb) third
'Third'
(Pdb) c
FirstSecondThird
PS C:\Users\datag\Desktop\python-practice-code>
```


[Mastering Python - Home](/mastering-python/){: .btn .btn--primary .btn--large}{: .align-center}
