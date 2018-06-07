---
title: "Tips & Tricks"
permalink: /mastering-python/tips-and-tricks-0006/
header:
  overlay_image: "/assets/images/logo/overlay-image.png"
  overlay_filter: rgba(255, 0, 255, 0.5)
  teaser: "/assets/images/misc/tips-tricks-1.png"
classes: wide
excerpt: "Tip # 6: Getting a sum of all values in a dictionary"
---

## Tip # 6: Getting a sum of all values in a dictionary:

The below example shows a simple way of being able to calculate the total sum of all donations without using a for loop to iterate through the dictionary.

```python
>>> donations = dict(sam=25.0, lena=88.99, chuck=13.0, linus=99.5, stan=150.0, lisa=50.25, harrison=10.0)
>>> donations.values()
dict_values([25.0, 88.99, 13.0, 99.5, 150.0, 50.25, 10.0])
>>> sum(donations.values())
436.74
```

### [Mastering Python - Home](/mastering-python/){: .btn .btn--primary}
