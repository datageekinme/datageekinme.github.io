---
title: "Data Structures"
permalink: /mastering-python/notes-0005/
header:
  overlay_image: "/assets/images/logo/overlay-image.png"
  overlay_filter: rgba(255, 0, 255, 0.5)
  teaser: "/assets/images/misc/notes-1.jpg"
classes: wide
excerpt: "Note #5: Slicing Lists"
---

## Slicing Lists:

### Generic Syntax:
Following is a generic syntax for slicing a list:
```python
myList[start:end:step]
```

### First Parameter: `start`:
This is the index to copy from.
```python
>>> myList = [1, 2, 3, 4]
>>> myList[1:]
[2, 3, 4]
>>> myList[3:]
[4]
>>> myList[-1:]
[4]
>>> myList[-3:]
[2, 3, 4]
```

### Second Parameter: `end`:
This is the index to copy up to, excluding the index specified.
```python
>>> myList = [1, 2, 3, 4]
>>> myList[:2]
[1, 2]
>>> myList[:4]
[1, 2, 3, 4]
>>> myList[1:3]
[2, 3]
>>> myList[:-1]
[1, 2, 3]
>>> myList[1:-1]
[2, 3]
```

### Third Parameter: `step`:
Basically the number to count at a  time. Similar to step in range
```python
>>> myList = [1, 2, 3, 4, 5, 6]
>>> myList[::2]
[1, 3, 5]
>>> myList[1::2]
[2, 4, 6]
>>> myList[::3]
[1, 4]
>>> myList[::-1]
[6, 5, 4, 3, 2, 1]
>>> myList[:1:-1]
[6, 5, 4, 3]
>>> myList[2::-1]
```

### [Mastering Python - Home](/mastering-python/){: .btn .btn--primary}
