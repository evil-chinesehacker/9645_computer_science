

#### to push notes:


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



28/09/2025

## Dictionaries and Objects: Example

I made this set of notes because i was unsure on how to complete all the tests for python challenges VIIc.  An example of something similar to the question thing is on here, with annotations to help me better understand.

```python

class Book:
	def __init__(self, title, author):
		self.__title = title
		self.__author = author

	def get_title(self):
		return self.__title

  
	def get_author(self):
		return self.__author

	def __repr__(self): 
		return f"{self.__title}, {self.__author}"
	
#when the variable which has an object assigned to it is printed, repr is automatically called

#returns a readable string representation of attributes in an object. especially needed if they are private.

#if you try to print an object directly without repr, will look like "<__main__.Book object at 0x7f8c2c0b0f70>"

#etc. like print(book1)

class Library: #to store the books
	def __init__(self):
		self.__books = {} #dictionary

	def add_book(self, book):
		self.__books[book.get_title()] = book #retrieves title of book (as it is a private attribute) which acts as the key in the dictionary.
		
	#'book' (WHICH IS AN OBJECT) will be the value of that key
	
#because of __repr__, it will be automatically formatted as a string
# -> (return f"{self.__title}, {self.__author}")

	def save_to_file(self, filename):
		with open(filename, 'w') as f:
		for book in self.__books.values(): 
		#.values() creates a view object. more info on it below.
			f.write(f"{book}\n")
		#book represents one object in the dictionary.
		
#(again..) python calls the '__repr__' method of the 'Book' class to get a string representation of the 'book' object

#so what is being written to the file is: f"{self.__title}, {self.__author}"
  

	def load_from_file(self, filename):
		books = []
		with open(filename, 'r') as f: 
		for line in f: 
#each line variable contains a single string, representing a line in books.txt
			title, author = line.strip().split(", ") 
#split.() splits the string into two parts: first part being 'title', and the second part being 'author'
			
#so the string "'weby book', 'weby'" -> title: 'weby book', author: 'weby'
			books.append((title, author)) #a tuple
		return books

	def display_books(self, books):
		for title, author in books: #prints out every book title and every author
		print(f"Title: {title}, Author: {author}")


#instantiate
library = Library()
bookfile = "books.txt"

book1 = Book("weby book", "weby")
book2 = Book("fubble book", "fubble")

#add books to library and save to file
library.add_book(book1)
library.add_book(book2)
library.save_to_file(bookfile)

#load objects from file and format them into printable strings
books = library.load_from_file(bookfile)
library.display_books(books)

```

View object: "a dynamic representation" of the contents in a dictionary. It provides a way to access keys and values (or other item pairs) of a dictionary without having to **create a separate copy of that data.**

for example...

### with a view object
```python

dict = {'six': 6, 'seven': 7}

#getting a view object of the values
view_values = dict.values()

#modifying original dictionary
dict['eight'] = 8

print(view_values)
#output will be dict.values([6, 7, 8])

```

### without a view object
```python

dict = {'six': 6, 'seven', 7}

copied_values = list(dict.values()) 

#list() converts an iterable, such as a view object into a list. When you apply list to a view object, it creates a seperate copy of data contained in the dictionary. 

#note: it will not update even if dictionary is updated. it is static.

dict['eight'] = 8

print(copied_values)

```

In short, a view object reflects the current state of a dictionary. 