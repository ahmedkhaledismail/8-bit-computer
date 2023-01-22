# Clock module
The computer’s clock is used to synchronize all operations. The clock we’re building is based on the popular 555 timers IC.
Our clock is adjustable speed (from less than 1Hz to a few hundred Hz). The clock can also be put into a manual mode where you push a button to advance each clock cycle. This will be a really useful feature for debugging the computer later on. <br/><br/>
<div style="text-align:center"><img src="./schematics/clock%20module.png" height="400" width="600"/></div> 

## Clock module schematics
As there are 2 modes of operation for the clock module, we will have 3 schematics to build the clock module. 
### &nbsp;&nbsp;&nbsp;&nbsp;  1. astable 555 timer mode
   in that mode of operation, the 555 timer output will be alternating between the two states, i.e., ON and OFF states. <br/><br/>
   <div style="text-align:center"><img src="./schematics/astable%20mode%20LM555%20timer.png" height="400" width="600"/></div> <br/>
    
   <ul>
   <li> If the input positive terminal of the comparator(op-amp) is greater than the input of the negative terminal, the comparator produces 5 volts as output (switch ON). Otherwise, the comparator produces 0 volts as output (switch OFF).</li>
   <li> 0.01 microfarad capacitor is connected between pin5 of the LM555 timer and ground to reduce the noise of the signal received from the power supply.</li>
   <li> 0.1 microfarad capacitor is connected between power supply pins (common + and common -) to reduce the voltage overshoot that occurs when the LM555 chip tries to pull current.</li>
   <li> Pin 4 of the LM555 chip is connected to 5 volt to make sure that the reset signal of SR-latch will not be activated in case of noise or stray voltage. </li>
   </ul>

###  &nbsp;&nbsp;&nbsp;&nbsp; 2. monostable LM555 timer mode
   in that mode of operation, the LM555 timer output will be in the ON state whenever a button is pressed. for the rest of the time, the timer output will be in the OFF state. <br/><br/>
   <div style="text-align:center"><img src="./schematics/monostable%20L555%20timer.png" height="400" width="600"/></div> 

###  &nbsp;&nbsp;&nbsp;&nbsp; 3. bistable LM555 timer mode
   in that mode of operation, the LM555 timer is used to select the mode that the computer will be operating on, i.e., astable timer mode or monostable timer mode. Bistable timer mode will utilize a push button to switch between the two modes.<br/><br/>
   <div style="text-align:center"><img src="./schematics/bistable%20mode%20LM355%20timer.png" height="400" width="600"/></div> <br/>

   we can transfer the output clock frequency of the selected mode to be used in timing other peripheral operations using a simple AND OR logic circuit or by using a NAND based logic circuit to reduce the number of ICs needed.

### &nbsp;&nbsp;&nbsp;&nbsp; 3.1 AND OR control logic circuit <br/><br/>
<div style="text-align:center"><img src="./schematics/AND%20OR%20timer%20mode%20selector%20control.png" height="400" width="600"/></div> 

### &nbsp;&nbsp;&nbsp;&nbsp; 3.2 NAND control logic circuit <br/><br/>
<div style="text-align:center"><img src="./schematics/NAND%20timer%20mode%20selector%20control.png" height="400" width="600"/></div> 