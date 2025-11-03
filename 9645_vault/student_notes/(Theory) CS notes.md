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

### The different types of algorithms (hw)

Can be seperated into two main types: searching and sorting.

*Searching: Linear and binary search*
*Sorting: merge and bubble sort*

#### Bubble Sort

1. compare first two values in dataset
2. if they're in wrong order (ascending order): swap them
3. compare next two values..
*Repeat step 2 and 3 untill end is reached*
4. If any swaps are made, repeat from beginning (all steps)
*else, stop: as list is in the correct order*

#### Merge Sort

1. divide dataset into smaller datasets by repeatedly splitting dataset in half
2. merge two halves into a singular, sorted array (by ascending order)
![[Screenshot 2025-11-03 at 6.12.03 PM.png]]
3. repeat step 2 until all elements are merged

#### Linear Search

1. Check the first value
2. If it is the value you're looking for, stop!
3. else move on to the next value and check
4. repeat until all values have been checked

#### Binary Search

1. identify the middle value and compare it to the value youre looking for
2. if its the value you're looking for, stop!
3. if middle value > wanted value, create new list with the values LEFT of the middle value
4. if middle value < wanted value, create new list with the values RIGHT of the middle value
5. repeat with new list

| Algorithm     | What is it for                        | Advantages                     | Disadvantages               |
| ------------- | ------------------------------------- | ------------------------------ | --------------------------- |
| Linear Search | Find a search term in a list or array | Can be used on any list        | Slow, in its worst case     |
| Binary Search | Find a search term in a list or array | Fast, even in its worst case   | list must be sorted         |
| Bubble sort   | Sort a list or array into order       | Needs no extra space in memory | slow, in its worse case     |
| Merge sort    | Sort a list or array into order       | Fast, even in its worst case   | needs extra spacei n memory |

"Big O values"

The maximum number of operations needed to complete an algorithm is called its **Big O** value. This value of an algorithm is expressed as a function of n, where n stands for the number of items that need to be processed.

| Algorithim    | Number of operations (time taken) | Extra Memory |
| ------------- | --------------------------------- | ------------ |
| Linear Search | n                                 | 1            |
| Binary search | log n                             | 1            |
| Bubble sort   | n^2                               | 1            |
| Merge sort    | n x log n                         | n            |
O(n) = linear time, execution time grows linearly with input. etc: iterating through every element in an array

O(log n) = Logarithmic Time, the execution time grows logarithmically (hence the name) as input size increases (often with algorithms that reduce the size of the problem by half each step)

etc. binary search

O(1) = Constant time, execution time doesn't change regardless of input size. etc: accessing an element in an array using its index

(others but im not quite sure. uh..)
O(N^x) 
O(x^n)

### Hardware (there is alot of acronyms)

At its core, computers are made up by a lot of transistors. Hardware components are like elements, and transistors are like little electrons and protons and neutrons...

##### CPU (central processing unit)

**Types of architecture**

There are two types of architecture, Harvard and Von Neumann.

In Harvard architecture, the CPU is connected with both the data memory (RAM) and program memory (ROM) separately. 
![[Pasted image 20251014143732.png]]
In Von Neumann architecture, there is no seperate data and program memory. 
![[Pasted image 20251014143828.png]]
(simplfiy later)

| Comparison            | Harvard                                                                                                                                                           | Von Neumann                                                                                                          |
| --------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------- |
| Hardware requirements | It requires more hardware since it will be requiring separate data and address bus for each memory.                                                               | In contrast to the Harvard architecture, this requires less hardware since only a common memory needs to be reached. |
| Space requirements    | This requires more space.                                                                                                                                         | Von-Neumann Architecture requires less space.                                                                        |
| Speed of execution    | Speed of execution is faster because  the processor fetches data and instructions simultaneously .                                                                | Speed of execution is slower since it cannot fetch the data and instructions at the same time.                       |
| Space usage           | It results in wastage of space since if the space is left in the data memory then the instructions memory cannot use the space of the data memory and vice-versa. | Space is not wasted because the space of the data memory can be utilized by the instructions memory and vice-versa.  |
| Controlling           | Controlling becomes complex since data and instructions are to be fetched simultaneously.                                                                         | Controlling becomes simpler since either data or instructions are to be fetched at a time.                           |

- Arithmetic Logic Unit (ALU)
- Control Unit (CU)
###### Registers

They are super small and fast memory located in the CPU: holds small amount of data required for fetch-decode-execute cycle.

There are 5 main registers:
- The Program Counter (PC)
- The Memory Address Register (MAR)
- The Memory Data Register (MDR)
- The Accumulator (ACC)
- Current Instruction Register (CIR)

*note: you MUST KNOW THE ACRONYMS FOR THIS*



##### - I/O controllers

##### - Bus (types)
- address bus
- data bus
- control bus

##### - RAM (random access memory)

##### - Motherboard
- ROM (read only memory)
   -Stores BIOS
- Clock
- 
##### - GPU (graphics processing unit)

##### - SSD (solid state drive)

##### - I/O controllers (input/output controllers)



### P1 questions (the 2-3 markers)

Algorithm: A sequence of steps that can be followed to complete a task and that always terminates.

Encapsulation: bundling data and methods within a class, hiding its internal condition from outside access (there MUST be a better definition for this)

**Purpose of a constructor method**: to define the initial values of instance variables **(instance variables are attributes defined in the constructor)**

**Describe the difference between an attribute that has a private/protected/public access modifier (3)

- Private attributes can only be accessed within the class they are defined in. They need getters/setters to be accessed/modified outside the class.

- Protected attributes are **INTENDED** to be accessed only within the parent class and its subclasses. They aren't meant to be accessed directly outside.

*(yes, they can be accessed outside the class similarly to a public attribute. this is bad programming and dunks on encapsulation.)*

- Public attributes can be accessed from anywhere: in and outside of the class they are defined in.