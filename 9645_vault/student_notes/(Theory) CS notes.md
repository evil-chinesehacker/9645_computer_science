3
9/09/2025 

## Logic Gates

![[Screenshot 2025-09-09 at 2.18.11 PM.png|100]]
AND (.) = only TRUE if both inputs are TRUE
NAND = TRUE if one or both inputs are FALSE

OR (+) = TRUE if one or both inputs are TRUE
NOR = only TRUE if both inputs are FALSE

XOR (⊕) = TRUE if both inputs are different

(don't need to learn about XNOR)



12/09/2025

## Logic Circuits (INSERT IMAGES)

Operand = the data that is being manipulated by the "operator"

examples of an operator could be +, -, / , %, //... 

Half adder:
![[Pasted image 20250916144845.png]]

Full adder:
![[Pasted image 20250916144852.png]]
S = sum
C = carry

16/09/2025

##  more logic gates

There are 3 types of buses..

8 bit system = 8 bit CPUs use an 8 bit data bus (can access 8 bits of data in a single machine instruction: parallel processing) More bits = faster processing.

SR-type Flip-Flop: Has a set and reset function. Anytime a flip-flop is set, Q goes high. Anytime a flip-flop is reset, Q goes low. 

| S   | R   | Q   | !Q  |                                                                                                         |
| :-- | :-- | :-- | :-- | ------------------------------------------------------------------------------------------------------- |
| 0   | 0   | Q   | !Q  | Unstable state: Q can be 1 or 0 depending on the previous state (of the SR latch. more on that later.)  |
| 1   | 0   | 1   | 0   |                                                                                                         |
| 0   | 1   | 0   | 1   |                                                                                                         |
| 1   | 1   | X   | X   | X = can be 0 or 1                                                                                       |
!Q = logical inverse of Q
Q = holds its previous state
S = set
R = reset

(insert SR latch)


D-type Flip-Flop: Uses an enabler to manage its stored state. if enabler is low, state wont change, but when enabler is high state will be modified. *(only need to know this for exam)*

also its used to make memory. (volatile)

(im not sure if this truth table is correct. remake it later)

| Enabler | X   | Q   |
| :-----: | :-- | :-- |
|    0    | 0   | Q   |
|    0    | 1   | Q   |
|    1    | 0   | 0   |
|    1    | 1   | 1   |
X = input
Q = output

Flip-flops are physical and they depend alot on physics. To make them more stable *(less invalid output: Q and !Q have to be different for this to happen for a valid output)* use a clock. It makes the flipflop output the stored state only in response to the clock signal: more predictable.


26/09/2025
## im edging it 

![[Pasted image 20250926083049.png]]
Rising Edge pulse detector (3 nots, 1 and)

**Rising edge pulse**: a momentary pulse triggered by a signal, making it transition from 0 (low state) to 1 (high state). This signal is only activated for 1 "scan cycle" (the process the PLC follows to read inputs, execute the control program and update outputs)

**PLC**: Stands for 'Programmable Logic Controller', which is a programmable computing device used in repetitive tasks, such as manufacturing



Simplifying circuits is good because the longer current flows through wires/transistors/logic gates, the more heat it will generate. The more heat generated, the higher the electrical resistance. Makes the circuit slower.




weird circuit truth table


| A   | B   | OUTPUT |
| --- | --- | ------ |
| 0   | 0   | 0      |
| 0   | 1   | 1      |
| 1   | 0   | 1      |
| 1   | 1   | 0      |
(it is an xor!)


## boolean (what is a boolean)

They make solving logic gates faster.

| Name (law)       | And form                                                        | Or form                                                   | extra description                                                                                                                                |
| ---------------- | --------------------------------------------------------------- | --------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------ |
| Identity         | A . 1 = A                                                       | 0 + A = A                                                 | "A boolean variable remains unchanged when AND'd with 1 or OR'd with 0."                                                                         |
| Null             | 0 . A = 0                                                       | 1 + A = 1                                                 | "A boolean variable AND'd will always be 0. A boolean variable OR'd with 1 will always be 1."                                                    |
| Idepotent        | A + A = A                                                       | A . A = A                                                 | "A boolean variable OR-ed or AND-ed with itself remains unchanged."                                                                              |
| identity i think | $A$ . $\overline A$ = 0                                         | $A$ + $\overline A$ = 1                                   | "The order of operands does not matter for AND and OR operations."                                                                               |
| Commutative      | A . B = B . A                                                   | A + B = B + A                                             |                                                                                                                                                  |
| Associative      | (A . B) . C = A . (B . C)                                       | (A + B) + C = A + (B + C)                                 | grouping of variables in an expression doesn't matter for either the + or .                                                                      |
| Distributive     | A + (B . C) = (A + B) . (B + C)                                 | A . (B + C) = (A . B) + (A . C)                           | "Allows you to expand an expression by showing how AND and OR operations interact"<br><br>its like math (you do the things in the bracket first) |
| Absorption       | A . (A + B) = A                                                 | A + (A . B) = A<br>                                       |                                                                                                                                                  |
| DeMorgansLaw     | $\overline A.\overline B$ = $\overline A + \overline B$<br><br> | $\overline A + \overline B$ = $\overline A . \overline B$ | Change the sign, split the not                                                                                                                   |
order of operations apply: NOT comes first, then and (.) comes first, then or. (+)


### P1 questions (the 2-3 markers)

Algorithm: A sequence of steps that can be followed to complete a task and that always terminates.

Encapsulation: bundling data and methods within a class, hiding its internal condition from outside access (there MUST be a better definition for this)

**Purpose of a constructor method**: to define the initial values of instance variables **(instance variables are attributes defined in the constructor)**

**Describe the difference between an attribute that has a private/protected/public access modifier (3)

- Private attributes can only be accessed within the class they are defined in. They need getters/setters to be accessed/modified outside the class.

- Protected attributes are **INTENDED** to be accessed only within the parent class and its subclasses. They aren't meant to be accessed directly outside.

*(yes, they can be accessed outside the class similarly to a public attribute. this is bad programming and dunks on encapsulation.)*

- Public attributes can be accessed from anywhere: in and outside of the class they are defined in.