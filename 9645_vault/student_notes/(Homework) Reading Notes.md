
## Object-Oriented coding
30/08/2025 (p353 - p359)
### notes

**Inheritance** is a relationship between two classes. **Association** is loosely based on definition of **Inheritance**.

In **Inheritance**, the new class (child/subclass) inherits properties and behaviors from an existing class (parent/superclass). In **Association**, two distinct classes are linked together: they can exist independently.

Etc. A car and its engine vs a customer and his credit card.

**Aggregation** is a special type of more specific **Association.** It can occur when a class is a collection or container of other classes, BUT the contained classes can exist outside of the container. Etc. a team and its players.

**Composition** is a stronger form of **Association**. If the container (NOT a parent/superclass) is destroyed every instance of the contained class is also destroyed. Etc. a hotel and its rooms.

*an example of a container would be a list or a dictionary*

###### Polymorphism

Allows objects of different types to be treated as objects of a common type.

*Etc. Superclass Animal can have subclasses, like Cat and Rodent. All objects in the superclass Animal can execute the methods moveLeft and moveRight.*

###### Overriding

Defining a method (inherited from a superclass) with the same name and formal argument types is called overriding. Etc. Animal (superclass)'s method is "move one space", while the method in the subclass Cat is "move three spaces", and the method in the subclass Rodent is "move two spaces".

###### Public/Private/Protected access modifiers

"information hiding": An object's instance variables are hidden so that other objects must use messages to interact with that object's state.

Private: only code within the class itself can access it
Public: code within any class can access it
Protected: varies between programming languages

An **interface** is a collection of abstract methods that a group of unrelated classes may implement


###### Advantages of object-oriented code

1. Forces programmers to plan extensively, leads to better coding designs
2. Source code for an object can be maintained and tested independently of the code for other objects
3. Easily reusable: easier to maintain

### Answers

Q1: Specify whether each of the following describe aggregation or composition

a) Zoo and Zooanimal: aggregation
b) RaceTrack and TrackSection: composition
c) Department and Teacher: aggregation


Q2: Suppose that tom is an instance of the Cat class, and jerry is an instance of the Mouse class. What will happen when each of these statements is executed?

tom.moveRight() = will move right three spaces
jerry.moveRight() = will move right two spaces


Q3: Beaver class inherits from rodent class but the beaver method is overridden by the animal method. (so only moves one space instead of two)

![[Screenshot 2025-09-04 at 7.49.14 PM.png]]
##### Exercises

1. a) inheritance is when a subclass (child) adopts behaviors from another class (parent)
b) ![[Screenshot 2025-09-01 at 6.19.35 PM.png]]

c) overriding is the ability of a child class to provide a specific implementation of a method that is in the parent class, allowing the child class to modify the method's behavior. 

d) MusicFile is a subclass for the class MediaFile.

MusicFile adds attributes such as Artist, SampleRate and BitDepth to the method of MediaFile while inheriting the method from MediaFile. This creates a specialised functionality for MusicFile. 


2. a) allows objects of different types to be treated as objects of a common type
 
b) i) The object bird1 is an instance of the bird class. When bird1 is called, it uses the procedure move method in the bird class and then prints "Birds can fly".

ii) The object bird2 is an instance of the class seabird, which is a subclass of the bird class. Since there is another move method defined in the subclass seabird, it will override the move method present in the class bird. So "Seabirds can fly and swim" will be printed.

3. A) two seperate classes can be linked together, but they can exist independently.
b) Class Furniture(self, tabletype, chairtype, numberofchairs):
self.tabletype = tabletype
self.chairtype = chairtype
self.numberofchairs = numberofchairs

c) It is common to make instance variables private so not every part of the program can alter the instance variables accidentally, allowing for modular testing.

It is common to make methods public so other parts of the program can call the methods, making code more reusable.