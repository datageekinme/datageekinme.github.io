---
title: "Data Structures"
permalink: /mastering-python/notes-0001/
header:
  overlay_image: "/assets/images/logo/overlay-image.png"
  overlay_filter: rgba(255, 0, 255, 0.5)
  teaser: "/assets/images/misc/notes-1.jpg"
classes: wide
excerpt: "Note #1: A summary of the data structures in Python"
---

## Data Structures in Python:

### Lists:
**Ordered sequence of values of other data types like int, boolean or string**

```python
# Example:
[1,2,3] or ['a','b','c']
```

Other Articles:
* [Notes: List Methods](/mastering-python/notes-0004/)
* [Notes: Slicing Lists](/mastering-python/notes-0005/)
* [Notes: List Comprehensions](/mastering-python/notes-0006/)
* [Tips: Tricks with Slices](/mastering-python/tips-and-tricks-0003/)
* [Tips: Swapping values in a list](/mastering-python/tips-and-tricks-0004/)

### Dictionaries:
**A collection of key: value pairs**

We use keys to describe our data and values to represent the data.

2 ways of creating a dictionary:
```python
# one way of creating a dictionary:
person = {"id": 1, "first_name": "Keith", "last_name": "Mascarenhas", "salary": 80000.00}
# another way of creating a dictionary:
person = dict('id' = 1, 'first_name' = 'Keith', 'last_name' = 'Mascarenhas', 'salary' = 80000.0)
```

Other Articles:
* [Notes: Accessing data from a dictionary](/mastering-python/notes-0007/)
* [Notes: Iterating a dictionary](/mastering-python/notes-0008/)
* [Notes: Dictionary methods](/mastering-python/notes-0009/)
* [Notes: Dictionary Comprehensions](/mastering-python/notes-0010/)
* [Tips: Getting a sum of all values in a dictionary](/mastering-python/tips-and-tricks-0006/)

### Tuples:

An ordered collection or grouping of items, but is immutable i.e. cannot update or delete a value in a tuple.

Example:
```python
numbers = (1, 2, 3, 4)
```
```python
>>> months = ('Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 'Jul', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec')
```
```python
>>> locations = {
...     (35.6895, 39.6917) : "Tokyo Office",
...     (40.7128, 74.0060) : "New York Office",
...     (37.7749, 122.4194) : "San Francisco Office"
... }
```

Why use a tuple?
* Tuples are faster than lists
* It makes your code safer as they are immutable
* Can use tuples as valid keys in a Dictionary

Methods available for a tuple are:
* `count`: Returns the number of times a value appears in a tuple
* `index`: Returns the index at which a value is found

Tuples can be nested. Also, slices work with tuples.

### Sets:

Sets are like formal mathematical sets. They are a collection of data that do not have duplicate values and aren't ordered. You cannot access items in a set by index.

Examples of creating sets:

```python
>>> s = set({1, 2, 3, 4, 5, 5, 5})
>>> s
{1, 2, 3, 4, 5}
>>> s = {1, 4, 5}
>>> s
{1, 4, 5}
>>> type(s)
<class 'set'>
>>> 4 in s
True
>>> 8 in s
False
```

Methods available for a set are:
* **`add`:** Adds an element to a set. If the element is already in the set, the set doesn't change.
* **`remove` and `discard`:** Removes a value from the set. `remove` returns a KeyError if the value is not found. To avoid KeyErrors, we can use `discard` method that works the same way as `remove`
* **`copy`:** Makes a copy of the set. Makes a duplicate of the data, not the same object in memory
* **`clear`:** Removes all the contents of the set

Set Math:

* `union` ==> `|` ==> `set1 | set2`
* `intersecction` ==> `&` ==> `set1 & set2`
* `symmetric-difference` ==> `-` ==> `set1 - set2`

Set Comprehension:

Similar to list and/or dictionary comprehensions.

Example:
```python
>>> { x ** 2 for x in range(1,11) } # creates a set
{64, 1, 4, 36, 100, 9, 16, 49, 81, 25}
>>> { x: x ** 2 for x in range(1,11) } # creates a dictionary, as key is also specified
{1: 1, 2: 4, 3: 9, 4: 16, 5: 25, 6: 36, 7: 49, 8: 64, 9: 81, 10: 100}
```

### [Mastering Python - Home](/mastering-python/){: .btn .btn--primary}
