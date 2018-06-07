---
title: "Functions"
permalink: /mastering-python/notes-0012/
header:
  overlay_image: "/assets/images/logo/overlay-image.png"
  overlay_filter: rgba(255, 0, 255, 0.5)
  teaser: "/assets/images/misc/notes-1.jpg"
classes: wide
excerpt: "Note #12: Scope"
---

## Scope:

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


### [Mastering Python - Home](/mastering-python/){: .btn .btn--primary}
