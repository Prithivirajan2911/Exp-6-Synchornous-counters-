# Exp-6-Synchornous-counters - up counter and down counter 
## AIM: 
To implement 4 bit up and down counters and validate  functionality.
## Equipments Required:
HARDWARE REQUIRED: PC, Cyclone II , USB flasher
SOFTWARE REQUIRED:   Quartus prime
### THEORY 

## UP COUNTER 
The counter is a digital sequential circuit and here it is a 4 bit counter, which simply means it can count from 0 to 15 and vice versa based upon the direction of counting (up/down). 

The counter (“count“) value will be evaluated at every positive (rising) edge of the clock (“clk“) cycle.
The Counter will be set to Zero when “reset” input is at logic high.
The counter will be loaded with “data” input when the “load” signal is at logic high. Otherwise, it will count up or down.
The counter will count up when the “up_down” signal is logic high, otherwise count down

Since we know that binary count sequences follow a pattern of octave (factor of 2) frequency division, and that J-K flip-flop multivibrators set up for the “toggle” mode are capable of performing this type of frequency division, we can envision a circuit made up of several J-K flip-flops, cascaded to produce four bits of output.
The main problem facing us is to determine how to connect these flip-flops together so that they toggle at the right times to produce the proper binary sequence.
Examine the following binary count sequence, paying attention to patterns preceding the “toggling” of a bit between 0 and 1:
Binary count sequence, paying attention to patterns preceding the “toggling” of a bit between 0 and 1.

Note that each bit in this four-bit sequence toggles when the bit before it (the bit having a lesser significance, or place-weight), toggles in a particular direction: from 1 to 0.

Starting with four J-K flip-flops connected in such a way to always be in the “toggle” mode, we need to determine how to connect the clock inputs in such a way so that each succeeding bit toggles when the bit before it transitions from 1 to 0.

The Q outputs of each flip-flop will serve as the respective binary bits of the final, three-bit count:

Three-bit “Up” Counter

![image](https://github.com/Prithivirajan2911/Exp-6-Synchornous-counters-/assets/147020085/8133305f-8972-48ac-a00a-33c30756b3a7)


## DOWN COUNTER 

As well as counting “up” from zero and increasing or incrementing to some preset value, it is sometimes necessary to count “down” from a predetermined value to zero allowing us to produce an output that activates when the zero count or some other pre-set value is reached.

This type of counter is normally referred to as a Down Counter, (CTD). In a binary or BCD down counter, the count decreases by one for each external clock pulse from some preset value. Special dual purpose IC’s such as the TTL 74LS193 or CMOS CD4510 are 4-bit binary Up or Down counters which have an additional input pin to select either the up or down count mode.

3-bit Count Down Counter

![image](https://github.com/Prithivirajan2911/Exp-6-Synchornous-counters-/assets/147020085/85a5dc78-db4e-47ef-aa14-569619b9e47e)

### Procedure

1.	Create a New Project:


Open Quartus and create a new project by selecting "File" > "New Project Wizard."
Follow the wizard's instructions to set up your project, including specifying the project name, location, and target device (FPGA).


2.	Create a New Design File:

Once the project is created, right-click on the project name in the Project Navigator and select "Add New File."
Choose "Verilog HDL File" or "VHDL File," depending on your chosen hardware description language.


3.	Write the Combinational Logic Code:

Open the newly created Verilog or VHDL file and write the code for your combinational logic.


4.	Compile the Project:


To compile the project, click on "Processing" > "Start Compilation" in the menu.
Quartus will analyze your code, synthesize it into a netlist, and perform optimizations based on your target FPGA device.


5.	Analyze and Fix Errors:

If there are any errors or warnings during the compilation process, Quartus will display them in the Messages window.
Review and fix any issues in your code if necessary.
View the RTL diagram.


6.	Verification:


Click on "File" > "New" > "Verification/Debugging Files" > "University Program VWF".
Once Waveform is created Right Click on the Input/Output Panel > " Insert Node or Bus" > Click on Node Finder > Click On "List" > Select All.
 
Give the Input Combinations according to the Truth Table amd then simulate the Output Waveform.



## PROGRAM: 
### UP COUNTER
```
module Up_counters(clk,q1,q2,q3);
input clk;
output reg q1,q2,q3;
always@(posedge clk)
begin
q3=(q1&q2)^q3;
q2=q1^q2;
q1=1^q1;
end 
endmodule
```

### DOWN COUNTER
```
module Down_counter(clk,q1,q2,q3);
input clk;
output reg q1,q2,q3;
always@(posedge clk)
begin
q3=((~q2)&(~q1))^q3;
q2=(~q1)^q2;
q1=1^q1;
end
endmodule
```

## RTL LOGIC UP COUNTER AND DOWN COUNTER:

### UP COUNTER

![image](https://github.com/Prithivirajan2911/Exp-6-Synchornous-counters-/assets/147020085/57c83874-c00e-4c3b-b353-e973a72780f3)

### DOWN COUNTER

![image](https://github.com/Prithivirajan2911/Exp-6-Synchornous-counters-/assets/147020085/c0151702-8496-4f65-b1a1-bd1169fb14c5)

## TIMING DIGRAMS FOR COUNTER: 

### UP COUNTER
![image](https://github.com/Prithivirajan2911/Exp-6-Synchornous-counters-/assets/147020085/aaa2cbc0-7e6d-4c08-9005-82ce74bf01d1)

### DOWN COUNTER
![image](https://github.com/Prithivirajan2911/Exp-6-Synchornous-counters-/assets/147020085/7cb9fabb-a544-477d-ab7e-0ea1ef6f7eb0)

## TRUTH TABLE:

### UP COUNTER

![image](https://github.com/Prithivirajan2911/Exp-6-Synchornous-counters-/assets/147020085/671de2b2-187a-45aa-8965-dc1ceac66261)

### DOWN COUNTER

![image](https://github.com/Prithivirajan2911/Exp-6-Synchornous-counters-/assets/147020085/072c2a32-10e2-4930-8d47-0edfd4b65004)

## RESULTS 
By this we have verified the truth table of 3-bit up-counter and 3-bit down counter using Verilog. 
