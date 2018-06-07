---
title: "Data Structures"
permalink: /mastering-python/notes-0006/
header:
  overlay_image: "/assets/images/logo/overlay-image.png"
  overlay_filter: rgba(255, 0, 255, 0.5)
  teaser: "/assets/images/misc/notes-1.jpg"
classes: wide
excerpt: "Note #6: List Comprehension"
---

## List Comprehension:

List comprehension is a shorthand syntax that creates a copy of a list based on the logic applied.

**Syntax:**
```python
[ <first-var> for <second-var> in <list/range> ]
```

**Examples:**

Get the square of numbers in a list:
```python
>>> nums = [1, 2, 3, 4, 5]
>>> [x * x for x in nums]
[1, 4, 9, 16, 25]
```

Get the square root of numbers in a list:
```python
>>> nums = [1, 4, 9, 16, 25]
>>> [x ** 0.5 for x in nums]
[1.0, 2.0, 3.0, 4.0, 5.0]
```

Converting a string to a list and changing case:
```python
>>> word = 'geek'
>>> [char.upper() for char in word]
['G', 'E', 'E', 'K']
```

Converting first letter in a string to uppercase for a bunch of words in a list:
```python
>>> names = ['john', 'jane', 'mike', 'molly', 'derek']
>>> [name.capitalize() for name in names]
['John', 'Jane', 'Mike', 'Molly', 'Derek']
```

Other sample examples:
```python
>>> [num * 10 for num in range(1, 6)]
[10, 20, 30, 40, 50]
>>>
>>> [bool(val) for val in [0, [], '']]
[False, False, False]
>>>
>>> nums = [1, 2, 3, 4, 5]
>>> strings = [str(num) for num in nums]
>>> strings
['1', '2', '3', '4', '5']
```

### With conditional logic:

Split a list into 2 lists of evens and odds:
```python
>>> nums = [1, 2, 3, 4, 5, 6, 7, 8, 9]
>>>
>>> evens = [num for num in nums if num % 2 == 0]
>>> evens
[2, 4, 6, 8]
>>>
>>> odds = [num for num in nums if num % 2 != 0]
>>> odds
[1, 3, 5, 7, 9]
```

List comprehension with `if.. else..`:
```python
>>> nums = [1, 2, 3, 4, 5, 6, 7, 8, 9]
>>> ['EVEN' if num % 2 == 0 else 'ODD' for num in nums]
['ODD', 'EVEN', 'ODD', 'EVEN', 'ODD', 'EVEN', 'ODD', 'EVEN', 'ODD']
>>>
```

List comprehension with `if.. elif..  else..`:
```python
>>> nums = [1, 2, 3, 4, 5, 6, 7, 8, 9, 0]
>>> ['ZERO' if num == 0 else 'EVEN' if num % 2 == 0 else 'ODD' for num in nums]
['ODD', 'EVEN', 'ODD', 'EVEN', 'ODD', 'EVEN', 'ODD', 'EVEN', 'ODD', 'ZERO']
```

List comprehension with nested lists:
```python
>>> answer = [[num for num in range(3)] for val in range(3)]
>>> answer
[[0, 1, 2], [0, 1, 2], [0, 1, 2]]
```

### Course Problems:

Given two lists [1, 2, 3, 4] and [3, 4, 5, 6], create a variable `answer`, which is a new list that is the intersection of the two.
```python
>>> answer = [num for num in [1, 2, 3, 4] if num in [3, 4, 5, 6]]
>>> answer
[3, 4]
```

Given a list of words ["Elie", "Tim", "Matt"], create a variable `answer2`, which is a new list with each word reversed and in lower case.
```python
>>> answer2 = [ word.lower()[::-1] for word in ["Elie", "Tim", "Matt"]]
>>> answer2
['eile', 'mit', 'ttam']
```

For all the numbers between 1 and 100, create a variable `answer`, which contains a list with all the numbers that are divisible by 12.
```python
>>> answer = [num for num in range(1, 101) if num % 12 == 0]
>>> answer
[12, 24, 36, 48, 60, 72, 84, 96]
```

Given the string "amazing", create a variable `answer`, which is a list containing all the letters from amazing but not vowels.
```python
>>> answer = [char for char in "amazing" if char not in "aeiou"]
>>> answer
['m', 'z', 'n', 'g']
```

### [Mastering Python - Home](/mastering-python/){: .btn .btn--primary}
