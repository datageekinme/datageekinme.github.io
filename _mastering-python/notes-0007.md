---
title: "Data Structures"
permalink: /mastering-python/notes-0007/
header:
  overlay_image: "/assets/images/logo/overlay-image.png"
  overlay_filter: rgba(255, 0, 255, 0.5)
  teaser: "/assets/images/misc/notes-1.jpg"
classes: wide
excerpt: "Note #7: Accessing a individual value in a dictionary"
---

## Accessing a individual value in a dictionary:
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

### [Mastering Python - Home](/mastering-python/){: .btn .btn--primary}
