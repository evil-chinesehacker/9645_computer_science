

## Inheritance

**Inheritance** allows classes to inherit properties and behaviours from other classes, creating a hierarchy of relationships. It promotes code reusability and enables the creation of more specialised classes by extending and enhancing the functionality of existing ones. A **superclass** is a class that is extended or inherited by other classes, providing a common set of attributes and methods, while a **subclass** is a class that inherits from a superclass. A superclass is also sometimes referred to as a **base class** or a **parent class**, and a subclass can be referred to as a **child class**.

**Example:**

The car company starts hiring out motorbikes as well as cars. They create a class template named `Vehicle`, which is the base class for two other child classes: `Car` and `Motorbike`.

```python
class Vehicle:
	def __init__(self, make, model, year):
		self.__make = make
		self.__model = model
		self.__year = year

	# Getters
	def get_make(self):
		return self.__make

	def get_model(self):
		return self.__model

	def get_year(self):
		return self.__year

	# Setters
	def set_make(self, make):
		self.__make = make

	def set_model(self, model):
		self.__model = model

	def set_year(self, year):
		self.__year = year

class Motorbike(Vehicle):
	def __init__(self, make, model, year, engine_displacement):
		super().__init__(make, model, year)
		self.__engine_displacement = engine_displacement

	def get_engine_displacement(self):
		return self.__engine_displacement

	def set_engine_displacement(self, engine_displacement):
		self.__engine_displacement = engine_displacement

class Car(Vehicle):
	def __init__(self, make, model, year, num_doors):
		super().__init__(make, model, year)
		self.__num_doors = num_doors

	def get_num_doors(self):
		return self.__num_doors

	def set_num_doors(self, num_doors):
		self.__num_doors = num_doors
````

## TASK 1

Instantiate an object of each class from the example and show examples of accessing the objects’ properties and running their methods.

---

**A:**
```python

class Vehicle:
	def __init__(self, make, model, year):
		self.__make = make
		self.__model = model
		self.__year = year

	# Getters
	def get_make(self):
		return self.__make

	def get_model(self):
		return self.__model

	def get_year(self):
		return self.__year

	# Setters
	def set_make(self, make):
		self.__make = make

	def set_model(self, model):
		self.__model = model

	def set_year(self, year):
		self.__year = year

class Motorbike(Vehicle):
	def __init__(self, make, model, year, engine_displacement):
		super().__init__(make, model, year)
		self.__engine_displacement = engine_displacement

	def get_engine_displacement(self):
		return self.__engine_displacement

	def set_engine_displacement(self, engine_displacement):
		self.__engine_displacement = engine_displacement

class Car(Vehicle):
	def __init__(self, make, model, year, num_doors):
		super().__init__(make, model, year)
		self.__num_doors = num_doors

	def get_num_doors(self):
		return self.__num_doors

	def set_num_doors(self, num_doors):
		self.__num_doors = num_doors

#creating an instance 

car1 = Car("Honda", "Honda Civic", 2018, 4)
vehicle1 = Vehicle("Ferrari", "Lambo", 2004)
motorbike1 = Motorbike("Porche", "i dont know any motorbike names", 2010, 4)

```

---

*To save, share and backup your work:*

```bash
git stage *this file*
git commit -m "task 1 completed"
git push
```


---

## TASK 2

Create a new class named `InternationalStudent` that inherits from your `Student` class. An **InternationalStudent** has a `fee_paid` property, a `nationality` property, and a `grade_expected_by_parent` property. Decide whether each property should be private, public, or protected.

---

**A:**

```python

class InternationalStudent:
	def __init__(self, fee_paid, nationality, expected_grade):
		self.__fee_paid = fee_paid
		self.__nationality = nationality
		self.__expected_grade = expected_grade
	
	def fee_setter(self):
		self.__fee_paid = fee_paid
		
	def nationality_setter(self):
		self.__nationality = nationality
	
	def expected_grade_setter(self):
		self.__expected_grade = expected_grade
	
	def fee_getter(self):
		return self.__fee_paid
	
	def nationality_getter(self):
		return self.__nationality
	
	def expected_grade_getter(self):
		return self.__expected_grade
	
	
student1 = InternationalStudent(100000, "Chinese", "A*")
print(InternationalStudent.fee_getter(student1))

```

---

*To save, share and backup your work:*


```bash
git stage *this file*
git commit -m "task 2 completed"
git push
```


---

## TASK 3

Instantiate three `InternationalStudent` objects and set their default properties.

---

**A:**

---

*To save, share and backup your work:*


```bash
git stage *this file*
git commit -m "task 3 completed"
git push
```

---

---

## TASK 4

The `find_necessary_tutors` method iterates through the student’s grades and compares each grade to `grade_expected_by_parent`, outputting whether a tutor is needed.

---

**A:**

---

*To save, share and backup your work:*

```bash
git stage *this file*
git commit -m "task 4 completed"
git push
```


---

## Polymorphism

**Polymorphism** allows objects to take on different forms or behaviours based on their underlying class. This is achieved using **method overriding**, where a child class modifies the behaviour it inherits from its parent. A polymorphic object typically has a mix of inherited and unique methods.

### Example

```python
class Motorbike:
	def __init__(self, make, model):
		self.make = make
		self.model = model

	def start_engine(self):
		print("Starting the motorbike engine.")

	def ride(self):
		return "Riding the motorbike."

class SportMotorbike(Motorbike):
	def ride(self):
		original_ride = super().ride()
		return original_ride + " at high speed."

class TouringMotorbike(Motorbike):
	def ride(self):
		original_ride = super().ride()
		return original_ride + " comfortably."

# Polymorphism in action
motorbike = Motorbike("Honda", "CBR")
sport_motorbike = SportMotorbike("Kawasaki", "Ninja")
touring_motorbike = TouringMotorbike("BMW", "R1250RT")
print(touring_motorbike.ride())
```

---

## TASK 5

Override the `calculate_gpa` method in the `InternationalStudent` class. The overridden method calls the base class's `calculate_gpa` but multiplies the result by the length of the international student's name divided by 100.

---

**A:**

---

*To save, share and backup your work:*

```bash
git stage *this file*
git commit -m "task 5 completed"
git push
```

---

## Composition & Aggregation

**Composition** and **aggregation** are "has-a" relationships. Composition implies a strong relationship where the associated object is owned by the container and cannot exist independently. Aggregation implies a weaker relationship where the associated object can exist independently and be shared among multiple containers.

```python
# Composition example
class _Wheel:
	def __init__(self, position):
		self.position = position

	def rotate(self):
		print(f"Wheel at position {self.position} rotating.")

class Car:
	def __init__(self):
		self.wheels = [ _Wheel(pos) for pos in range(4) ]

	def start_car(self):
		for wheel in self.wheels:
			wheel.rotate()
```

```python
# Aggregation example
class Department:
	def __init__(self, name):
		self.name = name

class Employee:
	def __init__(self, name, department):
		self.name = name
		self.department = department

	def get_department_name(self):
		return self.department.name
```

---

## TASK 6

Refactor the `Student` and `InternationalStudent` classes to use a `Subject` class. Each subject has `subject_name`, `current_grade`, and `target_grade`. Update the `calculate_gpa` and `find_necessary_tutors` methods accordingly.


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

## TASK 7: Aggregation Relationship Example

Create a new class that demonstrates aggregation.

```python
class Project:
	def __init__(self, name):
		self.name = name

class TeamMember:
	def __init__(self, name, project):
		self.name = name
		self.project = project
```


---

**A:**

---

*To save, share and backup your work:*

```bash
git stage *this file*
git commit -m "task 7 completed"
git push
```

---

## TASK 8: Class Relationship Diagram

Using the Mermaid Live plugin, create a class relationship diagram representing the relationships between the classes featured in the last two worksheets.

---

**A:**

---

*To save, share and backup your work:*

```bash
git stage *this file*
git commit -m "task 8 completed"
git push
```


---
