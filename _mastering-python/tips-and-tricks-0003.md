---
title: "Tips & Tricks"
permalink: /mastering-python/tips-and-tricks-0003/
header:
  overlay_image: "/assets/images/logo/overlay-image.png"
  overlay_filter: rgba(255, 0, 255, 0.5)
  teaser: "/assets/images/misc/tips-tricks-1.png"
classes: wide
excerpt: "Tip # 3: Tricks with slices"
---

## Tip # 3: Tricks with slices:

### Reversing lists / strings:

**Strings:**
```python
>>> string = "I am a Data Geek!"
>>> string[::-1]
'!keeG ataD a ma I'
```

**Lists:**
```python
>>> myList = ['I', 'am', 'a', 'Data', 'Geek']
>>> myList[::-1]
['Geek', 'Data', 'a', 'am', 'I']
```

### Modifying portions of a list:

```python
>>> nums = [1, 2, 3, 4, 5, 6]
>>> nums[1:3] = ['x', 'y', 'z']
>>> nums
[1, 'x', 'y', 'z', 4, 5, 6]
```

### [Mastering Python - Home](/mastering-python/){: .btn .btn--primary}
