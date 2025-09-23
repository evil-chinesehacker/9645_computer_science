
21/09/2025 
## Enum and @dataclass 
```python

from dataclasses import dataclass
from enum import Enum

  
# Enum defines a group of names bound to unique, constant values.

class Player(Enum):
	BLANK = " "
	PLAYER1 = "x"
	PLAYER2 = "o"

print(Player.PLAYER1.name) # = PLAYER1
print(Player.PLAYER1.value)# = 'x'

# Board state record implemented as a dataclass

@dataclass
class BoardState:
	grid: list[list[str]]
	turn: Player

#Dataclass generates the constructor (__init__), the method __repr__ 
#(which creates a printable, string representation of an object)
#and __eq__ (EXPLAINED BELOW. SUPERRR COMPLICATED!)


# Board related functions - it is now clear that they all require the board state
def print_board(board : BoardState) -> None:
#Function to print the board
	for row in board.grid:
		print("|".join(row))
		print("-" * 5)
		
```

In short, the method 'eq' in python lets you decide what it means for two objects in your code to be the same.  

By default, the == operator in python checks if two variables point to the same object. Eq allows you to change the behaviour (of the == operator) to compare the objects' **contents** (*like the assigned values*) instead of their **identity** (*unique identifier*)

### Whats an identity..?

it is NOT the variable an object is assigned to. (example shown below)

```python
#example

class Coordinates(x, y)
	def __init__(self, x, y)
		self.x = x
		self.y = y #look, they're public! hah!

p1 = Coordiantes(6, 7) #p1 and p2 are variable names
p2 = Coordinates(6, 7) #did unc snap
p3 = p1

#p1 and p2 are variable names, not identity
#identity can be represented/shown through the function id()

#the id of p1 and p2 will be different, even though they have the same values (contents), showing that they are different objects

#BUT the variable p3 will have the same id because it is referring to the variable p1, which has an object assigned to it

print(id(p1))
print(id(p2))
print(id(p3))

```

### Where the hell am i getting at?

Without the eq method, two objects will never be 'equal', even if their data is the same.

so like if i do print(p1 == p2), the output will be false.


but WITH the eq method, two objects can be 'equal', as long as their data is the same.

so if i did print(p1 == p2), the output will be true.


## Encapsulation, Abstraction, Inheritance, Polymorphism

Encapsulation is the practice of grouping methods and related attributes within a class. Through this, it ensures data remains secured and not accidentally modified.

Encapsulation also uses a concept called 'Abstraction', which reduces the complexity of the program by bundling data and the methods that operate on it into a single class. 

An example of this is.. 

```python

class Board:
	def print_board(board : BoardState) -> None:
#Function to print the board
		for row in board.grid:
			print("|".join(row))
			print("-" * 5)
```
All the user does is call the method "print_board()" within the Board class. The user doesn't have to understand how the board is constructed: a simple interface is provided instead.

Inheritance involves defining a class that inherits all the methods and attributes from its parent class, which promotes reusability.

Overriding is when a child class provides its own unique implementation that is present in its parent class, so when the method is called within the child, the child version is executed instead of the parent's.

```python
class MrGreedy:
	def Consumption(self):
		print("waffles")

class Biggie(MrGreedy):
	def Consumption(self):
		print("hamburburger")
	
class CoolBoy(MrGreedy):
	def one(self):
		print("this is a different method")

```

When Consumption is called within CoolBoy, waffles is printed. But when Consumption is called within Biggie, it will print hamburburger.


The concept polymorphism enables using a singular interface with the input of different data types. For example, the function len() is polymorphic:

```python

x = len("string")
y = len([6, 7, 4, 1]) #67 but i got 67 goons

print(x)
print(y)

```

It is polymorphic because it can take string input and list input. (different types of data)

In OOP, polymorphism is a way to make a method accept objects of different classes.