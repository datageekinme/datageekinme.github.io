---
title: "Data Structures"
permalink: /mastering-python/notes-0001/
header:
  overlay_image: "/assets/images/logo/overlay-image.png"
  overlay_filter: rgba(255, 0, 255, 0.5)
  teaser: "/assets/images/misc/notes-1.jpg"
classes: wide
excerpt: "Notes #2: Playing rock, paper, scissors with a computer player using the random module"
---

## Playing rock, paper, scissors with a computer player using the `random` module:

**Option 1:**
```python
print("...Rock")
print("...Paper")
print("...Scissors")

from random import randint
player1 = input("Player 1, make your move: ")
# using choice to pick a value from a list of options
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

**Option 2:**
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

### [Mastering Python - Home](/mastering-python/){: .btn .btn--primary}
