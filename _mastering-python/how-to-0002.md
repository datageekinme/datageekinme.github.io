---
title: "Mastering Python"
permalink: /mastering-python/how-to-0002/
header:
  overlay_image: "/assets/images/logo/overlay-image.png"
  overlay_filter: rgba(0, 0, 255, 0.5)
  teaser: "/assets/images/misc/how-to-1.jpg"
value: "b"
excerpt: "A collection of How-To's for Mastering Python"
---

## How-To #1: Formatting Strings

There are 3 options for formatting strings in python:

1. Using  `F-Strings` (applicable from Python v3.6 onwards):

      ```python
      name = "John  Smith"
      age = 52
      print(f"{name}, is {age} years old")
      ```

      By using `f`, we can add variables into the string by putting them within curly braces `{}`

2. Using the `.format` method:

      ```python
      name = "John  Smith"
      age = 52
      print("{}, is {} years old".format(name,age))
      ```

3. Using the `%` operator:

      ```python
      name = "John  Smith"
      age = 52
      print("%s, is %d years old" % (name,age))
      ```

      `John Smith` being a string type is represented as `%s`, whereas `age` being an integer type is represented as `%d`


**NOTE:** The position of the variables you supply into `format` or `%` is important. For example:

![Sequence of variables](/assets/images/courses/mastering-python/how-to-0005-ss-001.JPG){: .align-center}

## How-To #2: Converting Data Types

In string interpolation, data types are implicitly converted into string form.

Explicitly variables can be converted using the name of the builtin type as a function. For example:

```Python
avg_score = 64.3333
avg_score_rounded = int(avg_score)
```
![Type casting](/assets/images/courses/mastering-python/how-to-0006-ss-001.JPG){: .align-center}

[Mastering Python - Home](/mastering-python/){: .btn .btn--primary .btn--large}{: .align-center}
