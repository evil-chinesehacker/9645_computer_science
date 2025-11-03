



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

class Coordinates():
	def __init__(self, x, y):
		self.x = x
		self.y = y #look, they're public! hah!

p1 = Coordinates(6, 7) #p1 and p2 are variable names
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


### 2D arrays and slicing

A (very) important/simple way to create a 2d array is 

```python

board = [["" for _ in range(6)] for _ in range(5)]
for row in board:
	print(row)


```

"row" is the x axis (horizontal), "column" is the y axis (vertical)

Here is a way to iterate through columns, not rows.
```python

board = [
['1','2','3'],
['4','5','6'],
['7','8','9']
]
for col in range(len(board[0])): #iterate through columns
	for row in range(len(board) - 1, -1, -1): 
		print(board[row][col])
	#iterate through the characters in a column in a reverse order

```

iterate through columns in a normal.. order... (top to bottom)

```python

board = [
['1','2','3'],
['4','5','6'],
['7','8','9']
]

for col in range(len(board[0])):
	for row in range(len(board)):
		print(board[row][col])

```


### how do i slice????

Basic slicing:

```python

#basic slicing syntax
list = [0, 1, 2, 3, 4, 5]
print(list[0:3]) #[start:stop:step] stop is exclusive, while start is inclusive


```

```python

#negative slicing syntax: reverse an ENTIRE list

list = [0, 1, 2, 3, 4, 5]
print(list[::-1])

#reverse last 3 elements of a list
print(list[-1:-4:-1])

#last (number of) elements
print(list[-3:])

#everythign except last 2 elements
print(list[:-2])
```


for OOP refer back to the code things you wrote about.. (library thing)


13/10/2025
### Important Definitions

Algorithm: A sequence of steps that can be followed to complete a task and that always terminates.

Encapsulation: bundling data and methods within a class, hiding its internal condition from outside access (there MUST be a better definition for this)



### Recursion 
#### the different cases

base case: condition to stop recursion

general case: condition that continues recursion

recursive case: the part where the function calls itself with a modified input

#### recursion program example

```python

def Unknown(x):
    if x < 10: #--Base Case--#
        return x
    else: #--General Case--#
        a = x % 10         #get the last digit of x with modulo
        b = x // 10        #remove last digit using FLOOR (not true) division
        return a + Unknown(b)  #--Recursive Case--#
#add the last digit to the sum of the digits of the remaining number

answer = Unknown(7339)
print(answer)

```

recursion error: occurs when the maximum recursion depth is exceeded, and the program will crash, outputting a message similarly to this: 

"RecursionError: maximum recursion depth exceeded in comparison"

An example of this may be switching the **base case** from 'x < 10' to 'x < x'. As no integer can be bigger than itself so the condition x < x will always be False.  
  
Therefore, as x < x (base case) is never fulfilled, the program will keep recursively calling itself until it reaches a RecursionError/Stack overflow...

#### the concept of stacks ("hw")
 *im stacking it im stacking im stacking im stacking im stacking uim stacking im stacking*

Every time a function is called, a new frame (or instance) is added to the call stack. 
A **frame** is a data structure that holds information about a function call. For example, lets take a look at this SIMPLER recursive program..

```python

def repeater(n, x):
  if x > 0: #base case
    x -= 1
    return repeater(n, x) + n #recursive case
  return "" #general case
  
gubby = repeater("weby", 4)
print(gubby)

```

| Call level (stack) | n    | x   | Return Value       | Description                                                                                            |
| ------------------ | ---- | --- | ------------------ | ------------------------------------------------------------------------------------------------------ |
| 1                  | weby | 4   | ?                  | n value never changes                                                                                  |
| 2                  | weby | 3   | ?                  | return value isnt known until stack is unwinded                                                        |
| 3                  | weby | 2   | ?                  |                                                                                                        |
| 4                  | weby | 1   | ?                  |                                                                                                        |
| 5                  | weby | 0   | ""                 | Base Case is met/fulfilled, stack starts to unwind... Ordered by the last recursive call to the first. |
| 4                  | weby | 1   | "weby"             |                                                                                                        |
| 3                  | weby | 2   | "webyweby"         |                                                                                                        |
| 2                  | weby | 3   | "webywebyweby"     |                                                                                                        |
| 1                  | weby | 4   | "webywebywebyweby" |                                                                                                        |
In short: (for unwinding)

 **`repeater("weby", 0)`** returns `""`.
 **`repeater("weby", 1)`** returns `"weby"`.
 **`repeater("weby", 2)`** returns `"webyweby"`.
 **`repeater("weby", 3)`** returns `"webywebyweby"`.
 **`repeater("weby", 4)`** returns `"webywebywebyweby"`.


(IMPORTANT) when unwinding, recursive calls are not being made: **so only return values are being modified.**

#### queues (hw)

A queue is a data structure similar to a stack, BUT we add values at one end and remove values from the other end. (a literal queue) Also known as a 'FIFO' structure:

**F** - First
**I** - In
**F** - First
**O** - Out

It (typically) has these operations:

Enqueue: add an element to the end of the queue
Dequeue: remove AND return the element from the front of the queue

Peek: return the element from the front of the queue (without removing)

It consists of two points: the 'end' and the 'front'. End is where items and enqueued, front is where items are dequeued.

![[Pasted image 20251103174225.png]]

##### Differences between stack and queue

|                       | Queue                     | Stack                                                                                            |
| --------------------- | ------------------------- | ------------------------------------------------------------------------------------------------ |
| Order of<br>Operation | FIFO (First in first out) | FILO (First in last out)                                                                         |
| Operations            | Enqueue, dequeue          | Push (add an element to the top of the stack)<br>Pop (remove and return an element from the top) |


#### The different types of algorithms 

#### Relationships in OOP

Association: A general relationship in which one class uses or is associated with another
(don't really have to know about aggregation and composition)

Inheritance: A relationship where a class derives from an existing class, inherieting its attributes and methods: promoting code reusability

**Example:** a car and vehicle (car is a type of vehicle), and a calculator and a pencil case (a calculator is NOT a type of pencil case)

**Explanation**: Calculator and Pencil case are seperate entities, although they might be related because a calculator can be in a pencil case, they dont have a parent-child hierachy/relationship. So the relationship shown is association.


#### Dictionaries Extended

so you know the code i wrote (as a correction because i forgot syntax) for the mock exam (Q6)

```python

#QUESTION 6

#also yeah i didnt use a fixed dictionary withj like the numbers 0 to 9 because im cool

class Number:
	def __init__(self, number):
		self.__number = number
		self.__count = 1

	def return_number(self):
		return self.__number

	def return_count(self):
		return self.__count
	
	def add_count(self):
		self.__count += 1

	def __repr__(self):
		return(f"Number: {self.__number}, Count: {self.__count}")


class Numbers():
	def __init__(self):
		self.__dict = {} #tuples

	def check_objects(self, list):
		for num in list:
			if num in self.__dict:
				self.__dict[num].add_count() #add
				
			else: #create the number object
				temp = Number(num)
				self.__dict[num] = temp #STORES THE ACTUAL OBJECT ITSELF (unlike what i did on the test). NOT STATIC UNLIKE = temp.return_count()
	def return_highest_frequency(self):
		for value in self.__dict.values():
			print(value) #calls repr

numbers = Numbers()


def list(list):
	numbers.check_objects(list)
	numbers.return_highest_frequency() #aslo where'd the none come from.. update: nevermind

list([5,3,4,5,4,5]) #testing
#list([1,4,8,2,4,2,1,4,4,8,1])

```

The code i wrote (as a correction because i forgot syntax) for the mock exam (Q6) could be a lot simpler...

There is a subclass of dict called 'collections.Counter' (from collections import Counter) that is able to count hashable objects within an iterable. 

(translation: keep track of the amount of occurrences of each element in an iterable)

In short, for every new occurence in the iterable, i would make an object to store its count as the value, and the name of the element (a hashable) as the key. collections.Counter makes it so i dont have to create a new object for every new occurence in an iterable, it does it for me.

(im too lazy to port the code ive written utilizing 'Counter' into here. Check "mock exam.py" last Q for more details.)

#### yeah whats a hashable???
*i love hash browns*

An object is considered hashable if it has a constant hash value throughout its lifetime. A **hash value** is an integer used to quickly compare dictionary keys while looking at a dictionary. It's **state** cannot be changed after creation: they are immutable. 

Hashable objects are, in VERY simple terms, something that can be used as a dictionary key (as it's "hash" value will never change)

| Hashable Objects                                                                                          | Unhashable Objects            |
| --------------------------------------------------------------------------------------------------------- | ----------------------------- |
| - Strings<br>- Numbers<br>- Tuples<br>- Frozensets <br><br>*(^^ may come back to <br>this in the future)* | - Arrays<br>- Lists<br>- Sets |
In summary, 'unhashable' cannot be used as a dictionary key because..

- No stable hash value
- Data issues: key may not point to the right value anymore












It is 3/11/2025 (dd/mm/yy) and ive decided to drop CS. **It never clicked for me since i took it, unlike other unfamiliar subjects. I've talked to my parents already, but not teacher yet. From 8 ish (i think) people in my class to 4, I think I see why others dropped cs. I think ill be the last. Just for clarification, i think both my teachers are good teachers. For the one that teaches practical coding, I think he tries his best to explain it and gives loads of examples but the concepts are just really tricky, and a lot of things in practical CS are just "figure it out yourself" and arent really straightforward. Theory CS is well, alright. I know that all A-level subjects are hard but other subjects just feel like they make more sense to me.**

*If i get into game development someday (which i plan to in a few weeks), because i need new hobbies (for uni and for myself in general) ill use obsidian to make notes on it, or do something like a really inconsistent sloppy devlog/an amalgamation of texts and images representing something like a diary/scrapbook. Also i think i might get into drawing and video editing. (drawing as in by hand, not digital)*

