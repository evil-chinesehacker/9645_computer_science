
---

## Instructions

For this worksheet you should:

- Make a copy of this `.md` file and place it into your `student_work` directory of your fork of the 9645 vault.

- Run all code examples and make sure you understand the results.
      
- Add your own code examples to complete the tasks.

---

## Objects and Entities

In software design, an **object** is a representation of an **entity**.

**Example:

> A program is designed to help a company hire out cars.

> Each car in the company is represented as an object.

In the object-oriented programming paradigm a problem is decomposed into separate entities, each entity then becoming an object.

**Example:** 

> The program also contains objects representing customers, employees and managers.

---

## TASK 1

Give another example program and suggest what might be represented as an object in this program.

---

**A:**

---

*To save, share and backup your work:*


```bash
git stage *this file*
git commit -m "task 1 completed"
git push
```

---

## Classes, Constructors and Instantiation

The *class* keyword is used to start the definition of the template for an object. A class allows you to implement a "user-defined type".

**Example:** 

```python
class Car:
    ## definition of what it means to be a car starts here
```
  

The `__init__()` procedure is a special subroutine that is executed when an object is first created. This is known as the object's **constructor**. The `self` keyword is a special parameter that allows an object instance to refer to itself. 

**Example:** 

```python

class Car:
	def __init__(self):
		print("I'm a car!")
```
  

One class can be **instantiated** multiple times, creating multiple objects that are all of the same type. In Python, calling the class constructor and assigning the result to a variable represents the process of creating an instance of an object and storing it in memory.

  **Example:** 

```python
class Car:
	def __init__(self):
		print("I'm a car!")

ferrari = Car()
taxi = Car()
red_bull_promo_vehicle = Car()
```
  
> In this implementation, a ferrari, a taxi and a Red Bull promo vehicle are all now examples of cars.

---

## TASK 2

Write a class definition for an employee.

Each time a new employee is created, make them ask "How much am I getting paid?" and store the answer in a variable named `salary`.

Instantiate three employees inside variables named `bill`, `bob` and `ben`.

---

**A:**

---

*To save, share and back up your work:*


```bash
git stage *this file*
git commit -m "task 2 completed"
git push
```

---

## Attributes, Private Properties, Instance Params

Objects contain **attributes** (properties). These are the facts about the object: the data stored within it. Because each instance of an object is only based on a class, these properties are independent of other objects.

**Example:** 

```python
class Car:
	def __init__(self):
		self.__manufacturer = "Audi"
		self.__num_wheels = 4
```
  

This means every car is made by Audi and has 4 wheels. The string "Audi" and integer 4 are stored inside the private properties of each Car instance.
  
For the purpose of your course, you should name most properties using `__` as this makes them **private properties**. Private properties allow for **encapsulation**: making sure data is contained within the specific section of program code that is concerned with it.

It may be helpful to allow **instantiation parameters** to decide the data that gets assigned each time an object is instantiated.

```python
class Car:
	def __init__(self, manufacturer):
		self.__manufacturer = manufacturer
		self.__num_wheels = 4

ferrari = Car("ferrari")
taxi = Car("honda")
red_bull_promo_vehicle = Car("vauxhall")

# Demonstration of private properties
print(ferrari.manufacturer, "made your car")
# AttributeError: 'Car' object has no attribute 'manufacturer'
```


---

## TASK 3

Write a new class definition for a student at a school.
  
Each student has a date of birth, this is known when the object is first created.

Each student has a class, but this is not known when the object is first created.

Create an instance of a `Student` - using yourself as an example.  

---

**A:**

```python

class Student:
	def __init__(self, name, birthday, classroom, eca):
		self.name = name
		self.birthday = birthday
		self.classroom = classroom
		self.eca = eca

student1 = Student("Bob", "19/09/2008", "12M", 0)

```

---

*To save, share and back up your work:*


```bash
git stage *this file*
git commit -m "task 3 completed"
git push
```

---

## Methods, Getters, Setters, Interfaces & Type Hints

An object differs from a **record** because alongside properties, it also contains its own functions and procedures - known as **methods**. These are the actions the object can perform on data stored in its properties, and any data that is passed into its **scope**.

Because you will be making all data inside objects private, you should create a **getter** and a **setter** method for each property. Often the code for this will be simply resetting / returning the value of the property, but you may need to do something more - e.g. validate the data being passed in (although it may make sense to call a separate method to do this!)

Some data stored within an object will never change after the object is instantiated, so this will not need a setter. Any data such as this should be defined as a class constant, and this does NOT need to be placed inside the constructor method.

Some data stored within an object will never need to be accessed outside of the object, so a getter will not be needed.

Note: you are expected to annotate the interface of each method you create using the syntax:

`def method_name(param1: <type>, param2: <type>) -> return_type:`

  ```python
class Car:
	NUM_WHEELS = 4 
	
	def __init__(self, manufacturer: str, colour: str):
		self.__MANUFACTURER = manufacturer
		self.__current_driver = ""
		self.__colour = colour

	def get_current_driver(self) -> str:
		return self.__current_driver

	def set_current_driver(self, new_driver: str):
		self.__current_driver = new_driver

	def get_colour(self) -> str:
		return self.__colour

	def set_colour(self, new_colour: str):
		if new_colour in VALID_COLOURS:
			self.__colour = new_colour
		else:
			print("Colour not allowed: unchanged.")

if __name__ == "__main__":
	VALID_COLOURS = ["white", "red", "yellow"]
	ferrari = Car("ferrari", "white")
	name = input("Driver, what's your name? ")
	ferrari.set_current_driver(name)
	colour = input("What colour do you want to paint your Ferrari? ")
	ferrari.set_colour(colour)
	print(f"Thanks for hiring your car from us, {ferrari.get_current_driver()}!")
  ```

---

## TASK 4

Extend your `Student` class to contain properties representing: their favourite subject, the number of ECAs they participate in, a list of their grades (max 10), and their GPA.

Each student's favourite subject is not known when the instance is first created, but can be set via a setter method. The subject name should be rejected if its length is less than 3 characters.

A student does not have any grades when the instance is first created, but new grades can be added via the `add_grade()` method.

The student's GPA is initialised to 0.0.

The number of ECAs is initialised to 0. This number can be incremented by one using the setter method `add_eca()` . This method does not need any parameters except for the `self` keyword.

Create getter methods so that every property contained within a given student can be accessed from outside of the class.

---

**A:**

```python

class Student:
	def __init__(self, birthday, classroom, eca, gpa, grades, favsubjct):
		self.__birthday = birthday
		self.__classroom = classroom
		self.__eca = eca
		self.__gpa = gpa
		self.__grades = grades
		self.__favsubjct = favsubjct
		
	def add_eca(self):
		self.__eca += 1
	
	def get_eca(self):
		return(self.__eca)
	
	def add_grade(self, grade: str):
		self.__grades.append(grade)
	
	def get_grades(self):
		return(self.__grades)

student1 = Student("2008", "12M", 0, 0.0, ["A", "A*", "B"], "Computer Science")
student1.add_eca()
print(Student.get_eca(student1))

student1.add_grade("C")
print(Student.get_grades(student1))

```

---

*To save, share and back up your work:*


```bash
git stage *this file*
git commit -m "task 4 completed"
git push
```


---

## TASK 5  

Write a new method named `calculate_gpa()` according to the following rules:

- A* - 4
- A - 3.2
- B - 2.6
- C - 1.8
- D - 1.0
- E - 0.2
- U - 0
    
The GPA can be calculated by finding the point score for each grade the student has, then returning the average.

---

**A:**

```python

class Student:
	def __init__(self, birthday, classroom, eca, gpa, grades, favsubjct):
		self.__birthday = birthday
		self.__classroom = classroom
		self.__eca = eca
		self.__gpa = gpa
		self.__grades = grades
		self.__favsubjct = favsubjct
		
	def add_eca(self):
		self.__eca += 1
	
	def get_eca(self):
		return(self.__eca)
	
	def add_grade(self, grade: str):
		self.__grades.append(grade)
	
	def get_grades(self):
		return(self.__grades)

	def calculate_grades(self):
		
	
student1 = Student("2008", "12M", 0, 0.0, ["A", "A*", "B"], "Computer Science")
student1.add_eca()
print(Student.get_eca(student1))

student1.add_grade("C")
print(Student.get_grades(student1))

```

---

*To save, share and back up your work:*


```bash
git stage *this file*
git commit -m "task 5 completed"
git push
```


---

## Private, Public, Protected Modifiers

As well as private properties and **public** properties, your exam board requires you to have an understanding of **protected** properties.

Whilst none of these concepts truly exist in Python (you can still access protected properties, and you can even access and modify private properties if you try hard enough), you should be aware of the following conventions for labelling different object property types:

| Example                   | Modifier  | Explanation                                           |
| ------------------------- | --------- | ----------------------------------------------------- |
| `self.dinner_tonight`     | public    | Can be accessed and modified directly from anywhere   |
| `self._my_favourite_food` | protected | Can be accessed from child classes only.              |
| `self.__midnight_snack`   | private   | Cannot be accessed from outside of the current class. |

---
## TASK 6

Come up with 3 further properties for your `Student` class - one public, one private, one protected.

Implement getters / setters for the new properties as required.

---

**A:**

---

*To save, share and backup your work:*


```bash
git stage *this file*
git commit -m "task 6 completed"
git push
```


---
## Pythonic Getters & Setters (Extension)

Creating explicit getter and setter methods `set_property` and `get_property` aligns with other programming language paradigms e.g. Java and this is mostly likely what your examiners will be looking for.

However, [PEP 549](https://peps.python.org/pep-0549/) introduced a more Pythonic way of implementing this using the `@property` decorator syntax.

---
## EXTENSION

Re-write your `Student` class from this worksheet using the Pythonic getter / setter syntax as outlined in PEP 549.

---

**A:**

---

*To save, share and backup your work:*


```bash
git stage *this file*
git commit -m "extension task completed"
git push
```


---
