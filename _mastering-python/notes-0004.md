---
title: "Data Structures"
permalink: /mastering-python/notes-0004/
header:
  overlay_image: "/assets/images/logo/overlay-image.png"
  overlay_filter: rgba(255, 0, 255, 0.5)
  teaser: "/assets/images/misc/notes-1.jpg"
classes: wide
excerpt: "Note #4: Lists Methods"
---

## List Methods:

### `append`:
Adds an element to the end of the list.
```python
>>> nums = [1, 2, 3, 4]
>>> nums.append(5)
>>> nums
[1, 2, 3, 4, 5]
```

### `extend`:
Adds multiple elements to the end of the list.
```python
>>> nums = [1, 2, 3, 4]
>>> nums.extend([5, 6, 7, 8])
>>> nums
[1, 2, 3, 4, 5, 6, 7, 8]
```

### `insert`:
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

### `clear`:
Wipes out the contents of the entire list.
```python
>>> nums = [1, 2, 3, 4]
>>> nums.clear()
>>> nums
[]
```

### `pop`:
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

### `remove`:
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

### `index`:
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

### `count`:
Returns the number of times a element appears in the list.
```python
>>> nums = [1, 2, 3, 4, 5, 6, 5, 6, 7, 8, 7, 8, 9, 0, 8, 7, 8, 9, 0]
>>> nums.count(8)
4
```

### `sort`:
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

### `reverse`:
Reverses the elements of a list in-place.
```python
>>> nums = [1, 2, 3, 4, 5, 6]
>>> nums.reverse()
>>> nums
[6, 5, 4, 3, 2, 1]
```

### `join`:
Not a list method, but a string method. Very commonly used to convert list to strings
```python
>>> words = ['I', 'am', 'a', 'data', 'geek']
>>> ' '.join(words)
'I am a data geek'
```

### [Mastering Python - Home](/mastering-python/){: .btn .btn--primary}
