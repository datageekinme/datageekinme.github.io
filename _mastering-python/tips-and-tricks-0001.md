---
title: "Tips & Tricks"
permalink: /mastering-python/tips-and-tricks-0001/
header:
  overlay_image: "/assets/images/logo/overlay-image.png"
  overlay_filter: rgba(255, 0, 255, 0.5)
  teaser: "/assets/images/misc/tips-tricks-1.png"
classes: wide
excerpt: "Tip # 1: Difference between `is` and `==` operators"
---

## Tip # 1: Difference between `is` and `==` operators:

**Example 1:**
```Python
a = 1
a == 1 # True
a is 1 # True
```
**Example 2:**
```python
a = [1, 2, 3]
b = [1, 2, 3]
a == b # True
a is b # False ==>
```
`is` operator checks if the reference to the object the same, not the value.

### [Mastering Python - Home](/mastering-python/){: .btn .btn--primary}
