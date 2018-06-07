---
title: "Data Structures"
permalink: /mastering-python/notes-0010/
header:
  overlay_image: "/assets/images/logo/overlay-image.png"
  overlay_filter: rgba(255, 0, 255, 0.5)
  teaser: "/assets/images/misc/notes-1.jpg"
classes: wide
excerpt: "Note #10: Dictionary Comprehensions"
---

## Dictionary Comprehensions:

**Syntax:**
```python
{ <key>:<value> for <key, value> in <dictionary.items()> }
```

Examples:

Using items from a dictionary:
```python
>>> nums = dict(first=1, second=2, third=3)
>>> squared_nums = {key: value ** 2 for key, value in nums.items() }
>>> squared_nums
{'first': 1, 'second': 4, 'third': 9}
```
Using a list from a range function:
```python
>>> { num : num ** 2 for num in range(1, 10) }
{1: 1, 2: 4, 3: 9, 4: 16, 5: 25, 6: 36, 7: 49, 8: 64, 9: 81}
```
Using strings:
```python
>>> string1 = "ABC"
>>> string2 = "123"
>>> combo = { string1[i]: string2[i] for i in range(0, len(string1)) }
>>> combo
{'A': '1', 'B': '2', 'C': '3'}
```
Using conditional logic for value:
```python
>>> nums = [1, 2, 3, 4, 5]
>>> { num : ('even' if num % 2 == 0 else 'odd') for num in nums }
{1: 'odd', 2: 'even', 3: 'odd', 4: 'even', 5: 'odd'}
```
Using conditional logic for key:
```python
>>> nums = dict(first=1, second=2, third=3)
>>> caps_nums = { (k.upper() if k is 'second' else k) : v for k, v in nums.items() }
>>> caps_nums
{'first': 1, 'SECOND': 2, 'third': 3}
```

### [Mastering Python - Home](/mastering-python/){: .btn .btn--primary}
