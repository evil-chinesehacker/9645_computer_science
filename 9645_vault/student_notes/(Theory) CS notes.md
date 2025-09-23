
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

| S   | R   | Q   | !Q  |
| :-- | :-- | :-- | :-- |
| 0   | 0   | Q   | !Q  |
| 1   | 0   | 1   | 0   |
| 0   | 1   | 0   | 1   |
| 1   | 1   | X   | X   |
!Q = logical inverse of Q

Flip-flops are physical and they depend alot on physics. To make them more stable (less invalid output: Q and !Q have to be different for this to happen for a valid output) use a clock. It makes the flipflop output the stored state only in response to the clock signal: more predictable.


D-type Flip-Flop: Uses an enabler to manage its stored state. if enabler is low, state wont change, but when enabler is high state will be modified. 
(insert truth table)