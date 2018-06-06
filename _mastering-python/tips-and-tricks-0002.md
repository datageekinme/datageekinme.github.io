---
title: "Tips & Tricks"
permalink: /mastering-python/tips-and-tricks-0002/
header:
  overlay_image: "/assets/images/logo/overlay-image.png"
  overlay_filter: rgba(255, 0, 255, 0.5)
  teaser: "/assets/images/misc/tips-tricks-1.png"
classes: wide
excerpt: "Tip # 2: Data entered through `input` is always of string type"
---

## Tip # 2: Data entered through `input` is always of string type:

The data entered through console `input` command is in string type. Always remember to type cast to the data type that the evaluation happens on.

**For Example:**
```python
age = input("Enter age: ")
if age >= 21:
  print("You are an Adult!")
```
In the above example, if the age entered, let's say is 26, the condition check will evaluate into an error as "26" >= 21 i.e evaluating a string to an int results in an error.

To make sure it evaluates, always remember to type cast to the data type that you are evaluating it to. Also have base checks, for example in the above case, couple of checks that could be done are:
1. Entered age is an integer
2. Age is entered and not an empty string

### [Mastering Python - Home](/mastering-python/){: .btn .btn--primary}
