---
title: "Tips & Tricks"
permalink: /mastering-python/tips-and-tricks-0001/
header:
  overlay_image: "/assets/images/logo/overlay-image.png"
  overlay_filter: rgba(255, 0, 255, 0.5)
  teaser: "/assets/images/misc/tips-tricks-1.png"
toc: true
excerpt: "A collection of tips and tricks for Mastering Python"
---

## Tip # 1: Difference between `is` and `==` operators

**Example 1:**
```python
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

## Tip # 2: Data entered through `input` is always of string type

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

## Tip # 3: Tricks with slices

### Reversing lists / strings

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

### Modifying portions of a list

```python
>>> nums = [1, 2, 3, 4, 5, 6]
>>> nums[1:3] = ['x', 'y', 'z']
>>> nums
[1, 'x', 'y', 'z', 4, 5, 6]
```

## Tip # 4: Swapping Values in a list

```python
>>> myList = ["Data", "Geek"]
>>> myList[0], myList[1] = myList[1], myList[0]
>>> myList
['Geek', 'Data']
```

## Tip # 5: Difference between `capitalize` and `title` string functions

The difference between string.capitalize() vs string.title() is:

'hello world'.capitalize() gives back 'Hello world' which only capitalizes the first letter of the phrase 'hello world'

```python
>>> 'hello world'.capitalize()
'Hello world'
```
'hello world'.title() gives back 'Hello World', which capitalize all the first letter of words in a sentence.

```python
>>> 'hello world'.title()
'Hello World'
```

## Tip # 6: Getting a sum of all values in a dictionary

The below example shows a simple way of being able to calculate the total sum of all donations without using a for loop to iterate through the dictionary.

```python
>>> donations = dict(sam=25.0, lena=88.99, chuck=13.0, linus=99.5, stan=150.0, lisa=50.25, harrison=10.0)
>>> donations.values()
dict_values([25.0, 88.99, 13.0, 99.5, 150.0, 50.25, 10.0])
>>> sum(donations.values())
436.74
```

## Tip # 7: `range` vs. `xrange`

### `range`
The `range` type represents an immutable sequence of numbers and is commonly used for looping a specific number of times in `for` loops.

**Syntax:**
```python
range(stop)
range(start, stop[, step])
```
`step` argument defaults to 1. Can be negative or positive.

`range` returns a `list` object

### `xrange`

Similar to `range` i.e. generates a sequence of numbers. `xrange` does not actually generate a static list at run-time like range does. Creates the values as needed with a techinque called `yielding`. This techinque is used with a type of object called `generators`.

`xrange` returns a `xrange` object

NOTE: `xrange` does not exist in Python 3. `range` does what `xrange` used to do in Python 2.

## Tip # 8: Rock paper scissors using the `random` module

### Option 1 - Using `randint`:
```python
print("...Rock")
print("...Paper")
print("...Scissors")

from random import randint
player1 = input("Player 1, make your move: ")
# using randint to pick a value from a list of options
player2 = None
player2_choice = randint(0,2)
if player2_choice == 0:
  player2 = "rock"
elif player2_choice == 1:
  player2 = "paper"
else:
  player2 = 'scissors'
print("Computer player selected: " + player2)

if player1 == player2:
    print("It's a tie!")
elif player1 == "rock" and player2 == "scissors":
    print("player1 wins!")
elif player1 == "paper" and player2 == "rock":
    print("player1 wins!")
elif player1 == "scissors" and player2 == "paper":
    print("player1 wins!")
else:
    print("player2 wins!")
```

### Option 2 - Using `choice`:
```python
print("...Rock")
print("...Paper")
print("...Scissors")

from random import choice
player1 = input("Player 1, make your move: ")
# using choice to pick a value from a list of options
player2 = choice(['rock', 'paper', 'scissors'])
print("Computer player selected: " + player2)

if player1 == player2:
    print("It's a tie!")
elif player1 == "rock" and player2 == "scissors":
    print("player1 wins!")
elif player1 == "paper" and player2 == "rock":
    print("player1 wins!")
elif player1 == "scissors" and player2 == "paper":
    print("player1 wins!")
else:
    print("player2 wins!")
```

![Sample Output](/assets/images/courses/mastering-python/notes-0002-ss-001.JPG){: .align-center}

**NOTE:** Not handling invalid values to keep it simple

[Mastering Python - Home](/mastering-python/){: .btn .btn--primary .btn--large}{: .align-center}
