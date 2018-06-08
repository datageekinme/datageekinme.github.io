---
title: "Python: Functions"
permalink: /mastering-python/0005/
header:
  overlay_image: "/assets/images/logo/overlay-image.png"
  overlay_filter: rgba(0, 0, 255, 0.5)
  teaser: "/assets/images/misc/notes-1.png"
excerpt: "Lamdas and Built-In Functions"
toc: true
---

## Lambda Functions


```python
>>> def square(num):
...   return num * num
...
>>> print(square(9))
81
```

The above piece of code can be written in a single line using lambda (also called as anonymous functions), as follows:

```python
>>> square2 = lambda x: x * x
>>> print(square2(9))
81
```

## Map

A standard function that accepts atleast 2 arguments, a function and an iterable (something that can be iterated over i.e. lists, dictionaries, tuples, sets, strings).

The function runs the lambda for each value in the iterable and returns a map object which can be converted into another data structure.

```python
>>> doubles = list(map(lambda x : x * 2, nums))
>>> doubles
[4, 8, 12, 16, 20]
```
```python
>>> people = ['Darcy', 'Christina', 'Dana', 'Annabel']
>>> peeps = list(map(lambda name: name.upper(), people))
>>> peeps
['DARCY', 'CHRISTINA', 'DANA', 'ANNABEL']
```

## Filter

There is a lambda for each value in the iterable. Returns filter object which can be converted into other iterables.

The object contains only values that return true to the lambda.

```python
>>> nums = [1,2,3,4]
>>> evens = list(filter(lambda x: x % 2 == 0, nums))
>>> evens
[2, 4]
```

```python
>>> names = ['austin', 'penny', 'anthony', 'angel', 'billy']
>>> namesStartWithA = list(filter(lambda x: x.startswith('a'), names))
>>> namesStartWithA
['austin', 'anthony', 'angel']
```

```python
>>> users = [
...     {'username': 'samuel', 'tweets': ['I love cake', 'I love pie']},
...     {'username': 'katie', 'tweets': ['I love my cat']},
...     {'username': 'jeff', 'tweets': []},
...     {'username': 'bob123', 'tweets': []},
...     {'username': 'doggo_luvr', 'tweets': ['dogs are the best', "I'm hungry"]},
...     {'username': 'guitar_gal', 'tweets': []}
... ]
>>> inactiveUsers = list(filter(lambda u: len(u['tweets']) == 0, users))
>>> inactiveUsers
[{'username': 'jeff', 'tweets': []},
{'username': 'bob123', 'tweets': []},
{'username': 'guitar_gal', 'tweets': []}]
>>> #  alternate way of doing the same thing
...
>>> inactiveUsers2 = list(filter(lambda u: not u['tweets'], users))
>>> inactiveUsers2
[{'username': 'jeff', 'tweets': []},
{'username': 'bob123', 'tweets': []},
{'username': 'guitar_gal', 'tweets': []}]
>>> # only picking the usernames
...
>>> list(map(lambda user: user['username'].upper(),
          filter(lambda user: not user['tweets'], users)))
['JEFF', 'BOB123', 'GUITAR_GAL']
```

## All

Returns **True** if **all** elements of the iterable are truthy (or if the iterable is empty).

```python
>>> all([0, 1, 2, 3]) # 0 is falsy
False

>>> all([char for char in 'eio' if char in 'aeiou'])
True

>>> all([num for num in [4, 2, 10, 6, 8] if num % 2 == 0])
True

>>> people = ['Charlie', 'Casey', 'Kristy', 'Cody', 'Carla', 'Cristina']
>>> all([name[0] == 'C' for name in people])
False
```

## Any

Returns **True** if **any** element of the iterable is truthy. If the iterable is empty, returns **False**

```python
>>> any([0, 1, 2, 3])
True

>>> any([num for num in [4, 2, 10, 6, 8] if num % 2 == 0])
True

>>> people = ['Charlie', 'Casey', 'Kristy', 'Cody', 'Carla', 'Cristina']
>>> any([name[0] == 'C' for name in people])
True
```

## Sorted

Returns a new sorted list from the items in iterable.

In case of the list method `sort`, the sorting happens in place. However, `sorted` creates a sorted new list.

```python
>>> nums = [6, 1, 8, 2]

>>> sorted(nums)
[1, 2, 6, 8]

>>> sorted(nums, reverse=True)
[8, 6, 2, 1]

# original list is not changed
>>> nums
[6, 1, 8, 2]

# also works on a tuple
>>> sorted((2, 1, 45, 23, 99))
[1, 2, 23, 45, 99]

>>> sorted((2, 1, 45, 23, 99), reverse=True)
[99, 45, 23, 2, 1]

>>> users = [
...     {'username': 'samuel', 'tweets': ['I love cake', 'I love pie']},
...     {'username': 'katie', 'tweets': ['I love my cat']},
...     {'username': 'jeff', 'tweets': [], 'color': 'purple'},
...     {'username': 'bob123', 'tweets': [], 'num': 10, 'color': 'teal'},
...     {'username': 'doggo_luvr', 'tweets': ['dogs are the best', "I'm hungry"]},
...     {'username': 'guitar_gal', 'tweets': []}
... ]

# sort by number of keys in each dictionary
>>> sorted(users, key=len)
[{'username': 'samuel', 'tweets': ['I love cake', 'I love pie']},
{'username': 'katie', 'tweets': ['I love my cat']},
{'username': 'doggo_luvr', 'tweets': ['dogs are the best', "I'm hungry"]},
{'username': 'guitar_gal', 'tweets': []},
{'username': 'jeff', 'tweets': [], 'color': 'purple'},
{'username': 'bob123', 'tweets': [], 'num': 10, 'color': 'teal'}]

# sort by keys in descending order
>>> sorted(users, key=len, reverse=True)
[{'username': 'bob123', 'tweets': [], 'num': 10, 'color': 'teal'},
{'username': 'jeff', 'tweets': [], 'color': 'purple'},
{'username': 'samuel', 'tweets': ['I love cake', 'I love pie']},
{'username': 'katie', 'tweets': ['I love my cat']},
{'username': 'doggo_luvr', 'tweets': ['dogs are the best', "I'm hungry"]},
{'username': 'guitar_gal', 'tweets': []}]

# sort by username
>>> sorted(users, key=lambda user : user['username'])
[{'username': 'bob123', 'tweets': [], 'num': 10, 'color': 'teal'},
{'username': 'doggo_luvr', 'tweets': ['dogs are the best', "I'm hungry"]},
{'username': 'guitar_gal', 'tweets': []},
{'username': 'jeff', 'tweets': [], 'color': 'purple'},
{'username': 'katie', 'tweets': ['I love my cat']},
{'username': 'samuel', 'tweets': ['I love cake', 'I love pie']}]

# sort by number of tweets by each user
>>> sorted(users, key=lambda user : len(user['tweets']))
[{'username': 'jeff', 'tweets': [], 'color': 'purple'},
{'username': 'bob123', 'tweets': [], 'num': 10, 'color': 'teal'},
{'username': 'guitar_gal', 'tweets': []},
{'username': 'katie', 'tweets': ['I love my cat']},
{'username': 'samuel', 'tweets': ['I love cake', 'I love pie']},
{'username': 'doggo_luvr', 'tweets': ['dogs are the best', "I'm hungry"]}]
```

## Max

Returns the largest item in an iterable or the largest of two or more arguments

```python
>>> max(3, 23, 66, 99)
99

>>> max('c', 'd', 'a')
'd'

>>> nums = [40, 32, 6, 5, 10]
>>> max(nums)
40

>>> names = ['Arya', 'Simon', 'Dora', 'Tim', 'Ollivander']
>>> max(len(name) for name in names)
10
>>> max(names, key=lambda n: len(n))
'Ollivander'
```

## Min

Returns the smallest item in an iterable or the smallest of two or more arguments

```python
>>> min(3, 23, 66, 99)
3

>>> min('c', 'd', 'a')
'a'

>>> nums = [40, 32, 6, 5, 10]
>>> min(nums)
5

>>> names = ['Arya', 'Simon', 'Dora', 'Tim', 'Ollivander']
>>> min(len(name) for name in names)
3
>>> min(names, key=lambda n: len(n))
'Tim'
```

## Reversed

Returns a reverse iterator. Creates a list_reverseiterator object. Does not reverse in-place like the `reverse` list method

```python
>>> nums = [40, 32, 6, 5, 10]
>>> reversed(nums)
<list_reverseiterator object at 0x030C5EB0>
>>> list(reversed(nums))
[10, 5, 6, 32, 40]

>>> names = ['Arya', 'Simon', 'Dora', 'Tim', 'Ollivander']
>>> list(reversed(names))
['Ollivander', 'Tim', 'Dora', 'Simon', 'Arya']
```

## Zip

Makes an iterator that aggregates elements from each of the iterables. Returns an iterator of tuples, where the i-th tuple contains the i-th element from each of the argument sequences or iterables. The iterator stops when the shortest input iterable is exhausted.

```python
>>> first_zip = zip([1,2,3], [4,5,6])
>>> list(first_zip)
[(1, 4), (2, 5), (3, 6)]

# creating the zip again, as iterator object can only be used once.
>>> first_zip = zip([1,2,3], [4,5,6])
>>> dict(first_zip)
{1: 4, 2: 5, 3: 6}

# for example, if we again run the same dict conversion on
# the zip iterables, you get an empty dictionary
>>> dict(first_zip)
{}

# if iterables of not same length
>>> first_zip = zip([1,2,3], [4,5])
>>> list(first_zip)
[(1, 4), (2, 5)]
```

More complex examples:

```python
>>> midterms = [80, 91, 78]
>>> finals = [98, 89, 53]
>>> students = ['dan', 'ang', 'kate']

# get the highest marks between finals and midterms for each student
>>> dict(zip(students, (max(pair) for pair in zip(midterms, finals))))
{'dan': 98, 'ang': 91, 'kate': 78}

# another way to get the same output
>>> {t[0]: max(t[1], t[2]) for t in zip(students, midterms, finals)}
{'dan': 98, 'ang': 91, 'kate': 78}

# using map and zip to get the same
>>> dict(zip(students, map(lambda  pair: max(pair), zip(midterms, finals))))
{'dan': 98, 'ang': 91, 'kate': 78}
```

```python
# interleaving Strings
# interleave('hi', 'ha') ==> 'hhia'
>>> def interleave(str1, str2):
...     return ''.join([''.join(item) for item in zip(str1,str2)])
...
>>> interleave('hi', 'ha')
'hhia'
>>> interleave('lzr', 'iad')
'lizard'
```

```python
# triple and filter
>>> def triple_and_filter(l):
...     return list(map(lambda y: y * 3, filter(lambda x: x % 4 ==  0, l)))
...
>>> triple_and_filter([1,2,3,4])
[12]
>>> triple_and_filter([6,8,10,12])
[24, 36]
```

```python
# extract full name from list of dictionaries
>>> def extract_full_name(names):
...     return list(map(lambda names : names['first'] + ' ' + names['last'], names))
...
>>> names = [{'first': 'John', 'last': 'Smith'}, {'first': 'Jane', 'last': 'Doe'}]
>>> extract_full_name(names)
['John Smith', 'Jane Doe']
```

## Miscellaneous

### len

Returns the length of an object. Can write custom methods by overloading the `__len__` method.

### abs

Returns the absolute value of a number. The argument may be an integer or a floating point number. There's also an `fabs` in the math module.

### sum

Takes an iterable and an optional `start`. Returns the sum of start and the items of an iterable from left to right and returns the total. `start` by default is 0 (zero).

For strings, `join` is the preferred method and for floating point numbers, `fsum` from the math module.

```python
>>> sum([1,2,3])
6

>>> sum([1,2,3], 10)
16

>>> sum([1,2,3], -6)
0
```

### round

Return number rounded to n digits precision after the decimal point. if n digits is omitted or is `None`, it returns the nearest integer to its input.


[Mastering Python - Home](/mastering-python/){: .btn .btn--primary .btn--large}{: .align-center}
