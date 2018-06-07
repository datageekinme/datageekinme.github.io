---
title: "Python: Data Structures"
permalink: /mastering-python/0003/
header:
  overlay_image: "/assets/images/logo/overlay-image.png"
  overlay_filter: rgba(0, 0, 255, 0.5)
  teaser: "/assets/images/misc/notes-1.jpg"
toc: true
excerpt: "Dictionary Explained"
---

## Accessing a individual value in a dictionary
```python
>>> person = {"id": 1, "first_name": "Keith", "last_name": "Mascarenhas", "salary": 80000.00}
>>> person["id"]
1
>>> person["designation"]
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
KeyError: 'designation'
```
In the above example, if a key does not exist in the dictionary we get a key error.

To check if a key is in a dictionary:
```python
>>> "id" in person
True
>>> "designation" in person
False
```

To check if a value exists in a dictionary:
```python
>>> "keith" in person.values()
False
>>> "Keith" in person.values()
True
```

## Iterating a dictionary

To access and print values: Use `.values()`
```python
>>> person = {"id": 1, "first_name": "Keith", "last_name": "Mascarenhas", "salary": 80000.00}
>>> for value in person.values():
...     print(value)
...
1
Keith
Mascarenhas
80000.0
```

To access and print keys: Use `.keys()`
```python
>>> person = {"id": 1, "first_name": "Keith", "last_name": "Mascarenhas", "salary": 80000.00}
>>> for key in person.keys():
...     print(key)
...
id
first_name
last_name
salary
```

To access and print both key and values: Use `.items()`
```python
>>> person = {"id": 1, "first_name": "Keith", "last_name": "Mascarenhas", "salary": 80000.00}
```
Option 1 (prints a tuple of each key-value pair):
```python
>>> for item in person.items():
...     print(item)
...
('id', 1)
('first_name', 'Keith')
('last_name', 'Mascarenhas')
('salary', 80000.0)
```

Option 2:
```python
>>> for key, value in person.items():
...     print(f"{key} : {value}")
...
id : 1
first_name : Keith
last_name : Mascarenhas
salary : 80000.0
```

## Dictionary Methods

### `clear`

Clears all the key-value pairs in a dictionary.
```python
>>> person = {"id": 1, "first_name": "Keith", "last_name": "Mascarenhas", "salary": 80000.00}
>>> person
{'id': 1, 'first_name': 'Keith', 'last_name': 'Mascarenhas', 'salary': 80000.0}
>>> person.clear()
>>> person
{}
```

### `copy`

Makes a copy of a dictionary
```python
>>> person1 = {"id": 1, "first_name": "Keith", "last_name": "Mascarenhas", "salary": 80000.00}
>>> person2 = person1.copy()
>>> person2
{'id': 1, 'first_name': 'Keith', 'last_name': 'Mascarenhas', 'salary': 80000.0}
>>> person1 is person2
False
>>> person1 == person2
True
```

### `fromkeys`

Creates key-value pairs from comma-separated values. The first parameter is as an iterable object.
```python
>>> {}.fromkeys('fName', 'Keith')
{'f': 'Keith', 'N': 'Keith', 'a': 'Keith', 'm': 'Keith', 'e': 'Keith'}
>>> {}.fromkeys(['fName'], 'Keith')
{'fName': 'Keith'}
```

### `get`

If a key is in a dictionary, gets the value. If key does not exist then returns `None`, does not return a `KeyError`
```python
>>> person = {"id": 1, "first_name": "Keith", "last_name": "Mascarenhas", "salary": 80000.00}
>>> id = person.get('id')
>>> id
1
>>> designation = person.get('designation')
>>> designation
>>>
```

### `pop`

Removes the key-value pair from the dictionary corresponding to the specified key. If key does not exist, returns a `KeyError`
```python
>>> person = {"id": 1, "first_name": "Keith", "last_name": "Mascarenhas", "salary": 80000.00}
>>> person.pop("salary")
80000.0
>>> person
{'id': 1, 'first_name': 'Keith', 'last_name': 'Mascarenhas'}
>>> person.pop("designation")
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
KeyError: 'designation'
```

### `popitem`

Removes a random key from the dictionary.
```python
>>> person = {"id": 1, "first_name": "Keith", "last_name": "Mascarenhas", "salary": 80000.00}
>>> person.popitem()
('salary', 80000.0)
>>> person.popitem()
('last_name', 'Mascarenhas')
>>> person
{'id': 1, 'first_name': 'Keith'}
```

**NOTE:** So I was playing with this, and I noticed another difference. DICT.POP() returns the value, whereas DICT.POPITEM() returns the key value pair.

I made a dictionary of 100  key value pairs; and it always picks the last element, even though it's supposed to be random.

```python
>>> d = dict.fromkeys(range(1,101), 0)
>>> d
{1: 0, 2: 0, 3: 0, 4: 0, 5: 0, 6: 0, 7: 0, 8: 0, 9: 0, 10: 0, 11: 0, 12: 0, 13: 0, 14: 0, 15: 0, 16: 0, 17: 0, 18: 0, 19: 0, 20: 0, 21: 0, 22: 0, 23: 0, 24: 0, 25: 0, 26: 0, 27: 0, 28: 0, 29: 0, 30: 0, 31: 0, 32: 0, 33: 0, 34: 0, 35: 0, 36: 0, 37: 0, 38: 0, 39: 0, 40: 0, 41: 0, 42: 0, 43: 0, 44: 0, 45: 0, 46: 0, 47: 0, 48: 0, 49: 0, 50: 0, 51: 0, 52: 0, 53: 0, 54: 0, 55: 0, 56: 0, 57: 0, 58: 0, 59: 0, 60: 0, 61: 0, 62: 0, 63: 0, 64: 0, 65: 0, 66: 0, 67: 0, 68: 0, 69: 0, 70: 0, 71: 0, 72: 0, 73: 0, 74: 0, 75: 0, 76: 0, 77: 0, 78: 0, 79: 0, 80: 0, 81: 0, 82: 0, 83: 0, 84: 0, 85: 0, 86: 0, 87: 0, 88: 0, 89: 0, 90: 0, 91: 0, 92: 0, 93: 0, 94: 0, 95: 0, 96: 0, 97: 0, 98: 0, 99: 0, 100: 0}
>>> d.popitem()
(100, 0)
>>> d.popitem()
(99, 0)
>>> d.popitem()
(98, 0)
>>> d.popitem()
(97, 0)
>>> d.popitem()
(96, 0)
>>> d.popitem()
(95, 0)
```

### `update`

Update keys and values in a dictionary with another set of key-value pairs.
```python
>>> d1 = dict.fromkeys(range(1,11), 0)
>>> d1
{1: 0, 2: 0, 3: 0, 4: 0, 5: 0, 6: 0, 7: 0, 8: 0, 9: 0, 10: 0}
>>> d2 = dict()
>>> d2
{}
>>> d2.update(d1)
>>> d2
{1: 0, 2: 0, 3: 0, 4: 0, 5: 0, 6: 0, 7: 0, 8: 0, 9: 0, 10: 0}
>>> d2[1] = 1
>>> d2
{1: 1, 2: 0, 3: 0, 4: 0, 5: 0, 6: 0, 7: 0, 8: 0, 9: 0, 10: 0}
>>> d2.update(d1)
>>> d2
{1: 0, 2: 0, 3: 0, 4: 0, 5: 0, 6: 0, 7: 0, 8: 0, 9: 0, 10: 0}
```

## Dictionary Comprehensions

**Syntax:**
```python
{ <key>:<value> for <key, value> in <dictionary.items()> }
```

### Using items from a dictionary
```python
>>> nums = dict(first=1, second=2, third=3)
>>> squared_nums = {key: value ** 2 for key, value in nums.items() }
>>> squared_nums
{'first': 1, 'second': 4, 'third': 9}
```

### Using a list from a range function
```python
>>> { num : num ** 2 for num in range(1, 10) }
{1: 1, 2: 4, 3: 9, 4: 16, 5: 25, 6: 36, 7: 49, 8: 64, 9: 81}
```

### Using strings
```python
>>> string1 = "ABC"
>>> string2 = "123"
>>> combo = { string1[i]: string2[i] for i in range(0, len(string1)) }
>>> combo
{'A': '1', 'B': '2', 'C': '3'}
```
### Using conditional logic for value
```python
>>> nums = [1, 2, 3, 4, 5]
>>> { num : ('even' if num % 2 == 0 else 'odd') for num in nums }
{1: 'odd', 2: 'even', 3: 'odd', 4: 'even', 5: 'odd'}
```
### Using conditional logic for key
```python
>>> nums = dict(first=1, second=2, third=3)
>>> caps_nums = { (k.upper() if k is 'second' else k) : v for k, v in nums.items() }
>>> caps_nums
{'first': 1, 'SECOND': 2, 'third': 3}
```

[Mastering Python - Home](/mastering-python/){: .btn .btn--primary .btn--large}{: .align-center}
