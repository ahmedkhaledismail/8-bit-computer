# Random access memory (RAM) 
The random access memory (RAM) stores the program the computer is executing as well as any data the program needs. Our breadboard computer uses 4-bit addresses which means it will only have 16 bytes of RAM, limiting the size and complexity of programs it can run.<br/>

<div style="text-align:center"><img src="./schematics/ram%20module.png" class="full-width"/></div> 

## Random access memory (RAM) schematics

As the 1-bit register stores the data either as charges on the capacitor or as a state in a flip-flop. The capacitor needs to be refreshed continuously to maintain its charge, i.e., the value of that 1-bit register is 1. The flip-flop will maintain its data as long as the power is ON and the input states do not change. Using capacitors in building RAM modules is commonly known as Dynamic Random Access Memory (DRAM). While using flip flops in building RAM modules is known as Static Random Acess Memory (SRAM). The latter approach for building RAM modules is more expensive than the former one.

### &nbsp;&nbsp;&nbsp;&nbsp; 1-bit register

<div style="text-align:center"><img src="./schematics/1%20bit%20register.png" class="full-width"/></div> 

We will use 8 copies of the above circuit in cascade to get an 8-bit memory word, i.e., a 1-byte memory cell.

### &nbsp;&nbsp;&nbsp;&nbsp; 8-bit register

<div style="text-align:center"><img src="./schematics/8%20bit%20register.png" class="full-width"/></div> 

We will use 16 copies of the above circuit in cascade to build our 16-byte RAM module. The data lines will be common to all memory words as the memory address register will select the memory word to be read or written to.

### &nbsp;&nbsp;&nbsp;&nbsp; 16-byte RAM module

<div style="text-align:center"><img src="./schematics/16%20bytes%20RAM.png" class="full-width"/></div> 

We will use the following logic circuit as an address decoder for selecting the memory word to be accessed for reading or writing.

### &nbsp;&nbsp;&nbsp;&nbsp; address decoder

<div style="text-align:center"><img src="./schematics/address%20decoder.png" class="full-width"/></div> 

As we will have 2 modes of operation for memory addressing, i.e., reading memory addresses from a common bus or manually using dual in-line (DIP) switches. We will use the following logic circuit for selecting the mode of operation.

### &nbsp;&nbsp;&nbsp;&nbsp; 2 input 1 output selector control 

<div style="text-align:center"><img src="./schematics/2%20inputs%201%20output%20selector.png" class="full-width"/></div> 

Therefore, the memory address register will be as follows:

### &nbsp;&nbsp;&nbsp;&nbsp; memory address register

<div style="text-align:center"><img src="./schematics/memory%20address%20register.png" class="full-width"/></div> 
