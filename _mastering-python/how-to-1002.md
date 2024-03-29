---
title: "Mastering Python"
permalink: /mastering-python/1002/
header:
  overlay_image: "/assets/images/logo/overlay-image.png"
  overlay_filter: rgba(0, 0, 255, 0.5)
  teaser: "/assets/images/misc/how-to-1.jpg"
toc: true
excerpt: "A collection of How-To's for Mastering Python"
---

## How-To #1: Formatting Strings

There are 3 options for formatting strings in python:

1. Using  `F-Strings` (applicable from Python v3.6 onwards):

      ```python
      name = "John  Smith"
      age = 52
      print(f"{name}, is {age} years old")
      ```

      By using `f`, we can add variables into the string by putting them within curly braces `{}`

2. Using the `.format` method:

      ```python
      name = "John  Smith"
      age = 52
      print("{}, is {} years old".format(name,age))
      ```

3. Using the `%` operator:

      ```python
      name = "John  Smith"
      age = 52
      print("%s, is %d years old" % (name,age))
      ```

      `John Smith` being a string type is represented as `%s`, whereas `age` being an integer type is represented as `%d`


**NOTE:** The position of the variables you supply into `format` or `%` is important. For example:

![Sequence of variables](/assets/images/courses/mastering-python/how-to-0005-ss-001.JPG){: .align-center}

## How-To #2: Converting Data Types

In string interpolation, data types are implicitly converted into string form.

Explicitly variables can be converted using the name of the builtin type as a function. For example:

```Python
avg_score = 64.3333
avg_score_rounded = int(avg_score)
```
![Type casting](/assets/images/courses/mastering-python/how-to-0006-ss-001.JPG){: .align-center}

## How-To #3: Create custom modules

You can import from your own code. Syntax to import a custom module is the same as importing a built-in module. A custom module is nothing but a file name. To import the custom module, import the name of the python file.

For example, let's say you have 2 python files:
1. `bananas.py`
      * with the methods `peel()` and `dip_in_chocolate()`
2. `apples.py`
      * with the methods `offer()` and `bake()`

Now, if you want to use these methods in a 3rd file called `fruits.py`, you can import `bananas.py` and `apples.py` as follows:

```python
from bananas import dip_in_chocolate as dip
import apples
print(apples.offer())
print(dip())
```

## How-To #4: Make HTTP requests

Following is an example of making an API call to a website:

```python
import requests
from pyfiglet import figlet_format
from termcolor import colored
from random import choice

header = figlet_format("Dad Joke 3000")
header = colored(header, color="magenta")
print(header)

term = input("Let me tell you a joke! Give me a topic: ")
response_json = requests.get(
    "https://icanhazdadjoke.com/search",
    headers={"Accept": "application/json"},
    params={"term": term}
).json()

results = response_json["results"]
total_jokes = response_json["total_jokes"]

if total_jokes > 1:
    print(
        f"I've got {total_jokes} jokes about {term}. Here's one:\n",
        choice(results)['joke']
    )
elif total_jokes == 1:
    print(
        f"I've got one joke about {term}. Here it is:\n",
        results[0]['joke']
    )
else:
    print(f"Sorry, I don't have any jokes about {term}! Please try again.")
```

![sample output](/assets/images/courses/mastering-python/how-to-0004-ss-03.JPG){: .align-center}

## How-To #5: Leveraging documentation of the decorated function

Running the following code does not print the help of the function we are actually calling.
```python
def be_polite(func):
  def wrapper():
    """I am a wrapper function"""
    print("What a pleasure to meet you!")
    func()
    print("Have a great day!")
  return wrapper

@be_polite
def greet():
  """This function is used to greet a person"""
  print("I am a Data Geek")

help(greet)
```
Output:

```powershell
PS C:\Users\datag\Desktop\python-practice-code> python .\decorators.py
Help on function wrapper in module __main__:

wrapper()
    I am a wrapper function

PS C:\Users\datag\Desktop\python-practice-code>
```

In order to fix this, we can use the `wraps` method from the `functools` module as follows:

```python
from functools import wraps
def be_polite(func):
  @wraps(func)
  def wrapper():
    """I am a wrapper function"""
    print("What a pleasure to meet you!")
    func()
    print("Have a great day!")
  return wrapper

@be_polite
def greet():
  """This function is used to greet a person"""
  print("I am a Data Geek")

help(greet)
```
Output:

```powershell
PS C:\Users\datag\Desktop\python-practice-code> python .\decorators.py
Help on function greet in module __main__:

greet()
    This function is used to greet a person

PS C:\Users\datag\Desktop\python-practice-code>
```

## How-To #5: Speed testing a function using decorators

The following is a basic way of speed testing a function using decorators and `time` module.

NOTE: There are better ways of estimating the time taken, this is just a basic sample. Also, this test was run on my windows desktop PC. 

```python
from time import time
from functools import wraps

def speed_test(func):
  @wraps(func)
  def wrapper(*args, **kwargs):
    start_time = time()
    result = func(*args, **kwargs)
    end_time = time()
    print("Time elapsed: {0}".format(end_time-start_time))
    return result
  return wrapper

@speed_test
def sum_nums_gen(max):
  return sum(x for x in range(max)) # using generator

@speed_test
def sum_nums_list(max):
  return sum([x for x in range(max)]) # using list comprehension

print(sum_nums_gen(10000000)) # 10 Million
print(sum_nums_list(10000000)) # 10 Million

print(sum_nums_gen(100000000)) # 100 Million
print(sum_nums_list(100000000)) # 100 Million
```
Output for sum of numbers from 1 to 10 Million:
```powershell
PS C:\Users\datag\Desktop\python-practice-code> python .\speed_test.py
Time elapsed: 0.9465005397796631
49999995000000
Time elapsed: 0.9793457984924316
49999995000000
```
Output for sum of numbers from 1 to 100 Million:

Failed on my computer with MemoryError when using list comprehension. However, completed in around 10 seconds with a generator.

```powershell
Time elapsed: 9.8843355178833
4999999950000000
Traceback (most recent call last):
  File ".\speed_test.py", line 23, in <module>
    print(sum_nums_list(100000000)) # 100 Million
  File ".\speed_test.py", line 8, in wrapper
    result = func(*args, **kwargs)
  File ".\speed_test.py", line 20, in sum_nums_list
    return sum([x for x in range(max)]) # using list comprehension
  File ".\speed_test.py", line 20, in <listcomp>
    return sum([x for x in range(max)]) # using list comprehension
MemoryError
```


[Mastering Python - Home](/mastering-python/){: .btn .btn--primary .btn--large}{: .align-center}
