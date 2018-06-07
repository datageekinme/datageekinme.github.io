---
title: "Python: Data Structures"
permalink: /mastering-python/0002/
header:
  overlay_image: "/assets/images/logo/overlay-image.png"
  overlay_filter: rgba(0, 0, 255, 0.5)
  teaser: "/assets/images/misc/notes-1.png"
toc: true
excerpt: "Lists Explained"
---

## Slicing Lists

### Generic Syntax
Following is a generic syntax for slicing a list:
```python
myList[start:end:step]
```

#### First Parameter: `start`
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

#### Second Parameter: `end`
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

#### Third Parameter: `step`
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

## List Methods

### `append`
Adds an element to the end of the list.
```python
>>> nums = [1, 2, 3, 4]
>>> nums.append(5)
>>> nums
[1, 2, 3, 4, 5]
```

### `extend`
Adds multiple elements to the end of the list.
```python
>>> nums = [1, 2, 3, 4]
>>> nums.extend([5, 6, 7, 8])
>>> nums
[1, 2, 3, 4, 5, 6, 7, 8]
```

### `insert`
Add an element at the position of the index specified.
```python
>>> nums = [1, 2, 3, 4]
>>> nums.insert(2, 6)
>>> nums
[1, 2, 6, 3, 4]
```
To insert to the end of the list, index `-1` does not work. Please see below:
```python
>>> nums = [1, 2, 3, 4]
>>> nums.insert(-1, 6)
>>> nums
[1, 2, 3, 6, 4]
```
To insert to the end of the list, following can be done. However, using `append` would be a better choice.
```python
>>> nums = [1, 2, 3, 4]
>>> nums.insert(len(nums), 6)
>>> nums
[1, 2, 3, 4, 6]
```

### `clear`
Wipes out the contents of the entire list.
```python
>>> nums = [1, 2, 3, 4]
>>> nums.clear()
>>> nums
[]
```

### `pop`
Removes the element from the list at the position defined in the argument of the method. Also returns the value removed from the list.
```python
>>> nums = [1, 2, 3, 4]
>>> nums.pop(2)
3
>>> nums
[1, 2, 4]
```
When no index specified, `pop` removes the last element from the list.
```python
>>> nums = [1, 2, 3, 4]
>>> nums.pop()
4
>>> nums
[1, 2, 3]
```

### `remove`
Removes the said value from the list.
```python
>>> nums = [1, 2, 3, 4]
>>> nums.remove(3)
>>> nums
[1, 2, 4]
```
In case of multiple values, removes the first occurring instance.
```python
>>> nums = [1, 2, 3, 4, 5, 4, 6]
>>> nums.remove(4)
>>> nums
[1, 2, 3, 5, 4, 6]
```

### `index`
Returns the index for a given item in the list.
```python
>>> nums = [1, 2, 3, 4, 5, 6]
>>> nums.index(4)
3
```
We can specify the range using a `start` and `end` index positions to search the value.
```python
>>> nums = [1, 2, 3, 4, 5, 6, 5, 6, 7, 8, 7, 8, 9, 0, 8, 7, 8, 9, 0]
>>> nums.index(5) # search first occurance
4
>>> nums.index(5, 5) # search first occurance starting from the specified index
6
>>> nums.index(8, 8, 13) # search first occurance in the specified range
9
```

### `count`
Returns the number of times a element appears in the list.
```python
>>> nums = [1, 2, 3, 4, 5, 6, 5, 6, 7, 8, 7, 8, 9, 0, 8, 7, 8, 9, 0]
>>> nums.count(8)
4
```

### `sort`
Sorts the elements of a list in-place. By default, sorts in ascending order.
```python
>>> nums = [1, 3, 2, 6, 4, 5]
>>> nums.sort()
>>> nums
[1, 2, 3, 4, 5, 6]
```
To sort in descending order:
```python
>>> nums = [1, 3, 2, 6, 4, 5]
>>> nums.sort(reverse=True)
>>> nums
[6, 5, 4, 3, 2, 1]
```

### `reverse`
Reverses the elements of a list in-place.
```python
>>> nums = [1, 2, 3, 4, 5, 6]
>>> nums.reverse()
>>> nums
[6, 5, 4, 3, 2, 1]
```

### `join`
Not a list method, but a string method. Very commonly used to convert list to strings
```python
>>> words = ['I', 'am', 'a', 'data', 'geek']
>>> ' '.join(words)
'I am a data geek'
```

## List Comprehension

List comprehension is a shorthand syntax that creates a copy of a list based on the logic applied.

**Syntax:**
```python
[ <first-var> for <second-var> in <list/range> ]
```

### Iterating through the list

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

### With conditional logic

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

### Course Problems

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

[Mastering Python - Home](/mastering-python/){: .btn .btn--primary .btn--large}{: .align-center}
