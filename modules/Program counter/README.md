# Program Counter module
The program counter (PC) counts in binary to keep track of which instruction the computer is currently executing.<br/>

<div style="text-align:center"><img src="./schematics/program%20counter.png" class="full-width"/></div> 

## Program Counter schematics

Flip flops are commonly used for building binary counters as they save their current output state as long as the power is ON and the input states do not change. Let's have look at the SR-latch and SR flip-flop truth tables to see if they might help in building a binary counter.

### &nbsp;&nbsp;&nbsp;&nbsp; SR-latch

<div style="text-align:center"><img src="./schematics/SR%20latch.png" class="full-width"/></div> 

### &nbsp;&nbsp;&nbsp;&nbsp; SR flip-flop

<div style="text-align:center"><img src="./schematics/SR%20flip%20flop.png" class="full-width"/></div> 

From the truth table above, it shows that the output state of both the SR-latch and SR flip-flop is all zeros when the two inputs are 1's. That does not make sense since the output signals are the inverse of each other. In real life, due to manufacturing methods, one gate will always win, but it's impossible to tell which it will be for a particular device from an assembly line. The state of S = R = 1 is therefore "illegal" and should never be entered. <br/>
We will use the JK flip-flop instead of SR flip-flop as it toggles its output whenever the input signals are all 1's.

### &nbsp;&nbsp;&nbsp;&nbsp; JK flip flop

<div style="text-align:center"><img src="./schematics/JK%20flip%20flop.png" class="full-width"/></div> 

JK flip flops are used for creating binary counters as its output state (Q) is toggling at half the speed of the clock when both inputs are 1's. Therefore, we can use 4 JK flip flops in cascade by connecting the computer clock to the first flip flop and the output of the first flip flop as a clock for the second flip flop and so on. In that way, we can use the output of the 4 JK flip flops as a 4-bit binary counter. We can use that 4-bit binary counter with an increment enable signal as a program counter for our computer. <br/>

A problematic side effect of our implementation of the JK flip flop is that it toggles many times for a single enable signal. That condition is commonly referred to as a race condition because Q output will toggle as long as enable is high, which makes the output of the flip-flop unstable or uncertain. The output of the JK flip-flop is shown in the purple timing diagram depicted below.

<div style="text-align:center"><img src="./schematics/JK%20flip%20flop%20race%20condition.png" class="full-width"/></div> 

Therefore, instead of using a JK flip-flop, we will use a master-slave JK flip-flop that guarantees to toggle the output of the JK flip-flop only once.

### &nbsp;&nbsp;&nbsp;&nbsp; Master-Slave JK flip-flop

<div style="text-align:center"><img src="./schematics/master-slave%20JK%20flip%20flop.png" class="full-width"/></div> 

After interfacing the program counter to our computer, the common bus will be something like this:

<div style="text-align:center"><img src="./schematics/common%20bus.png" class="full-width"/></div> 

