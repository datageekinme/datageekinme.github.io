---
title: "Data Structures"
permalink: /mastering-python/notes-0008/
header:
  overlay_image: "/assets/images/logo/overlay-image.png"
  overlay_filter: rgba(255, 0, 255, 0.5)
  teaser: "/assets/images/misc/notes-1.jpg"
classes: wide
excerpt: "Note #8: Iterating a dictionary"
---

## Iterating a dictionary:

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

### [Mastering Python - Home](/mastering-python/){: .btn .btn--primary}
