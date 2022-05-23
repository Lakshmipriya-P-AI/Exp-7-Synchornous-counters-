# Exp-6-Synchornous-counters - up counter and down counter 
### AIM: 
To implement 4 bit up and down counters and validate  functionality.

### HARDWARE REQUIRED:
PC, Cyclone II , USB flasher

### SOFTWARE REQUIRED:
Quartus prime

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

The Q outputs of each flip-flop will serve as the respective binary bits of the final, four-bit count:

Four-bit “Up” Counter
![image](https://user-images.githubusercontent.com/36288975/169644758-b2f4339d-9532-40c5-af40-8f4f8c942e2c.png)

## DOWN COUNTER 

As well as counting “up” from zero and increasing or incrementing to some preset value, it is sometimes necessary to count “down” from a predetermined value to zero allowing us to produce an output that activates when the zero count or some other pre-set value is reached.

This type of counter is normally referred to as a Down Counter, (CTD). In a binary or BCD down counter, the count decreases by one for each external clock pulse from some preset value. Special dual purpose IC’s such as the TTL 74LS193 or CMOS CD4510 are 4-bit binary Up or Down counters which have an additional input pin to select either the up or down count mode.
![image](https://user-images.githubusercontent.com/36288975/169644844-1a14e123-7228-4ed8-81a9-eb937dff4ac8.png)

4-bit Count Down Counter
### Procedure
/* write all the steps invloved */



### PROGRAM 
/*
Program for flipflops  and verify its truth table in quartus using Verilog programming.
Developed by: P.Lakshmi Priya
RegisterNumber:  212221230053
*/
```
UP COUNTER
module ex06(input clk,input reset,output[3:0]counter);
reg[3:0]counter_up;
always@(posedge clk or posedge reset)
begin
if(reset)
counter_up<=4'd0;
else
counter_up<=counter_up+4'd1;
end
assign counter = counter_up;
endmodule 
```

### RTL LOGIC 
### UP COUNTER
<img width="574" alt="cdcup" src="https://user-images.githubusercontent.com/93427923/169741921-ca2a3d39-34be-441c-9d40-554a964eccd2.png">

### TIMING DIAGRAM
<img width="947" alt="ttcup" src="https://user-images.githubusercontent.com/93427923/169741939-50ea85a9-bee9-4fd2-bd68-4a5b2efac259.png">

### TRUTH TABLE
![upc](https://user-images.githubusercontent.com/93427923/169741946-59e2a013-e84a-445e-8e80-db8212ea6adb.jpg)


## DOWN COUNTER:
module ex06(input clk,input reset,output[3:0]counter);
reg[3:0]counter_down;
always@(posedge clk or posedge reset)
begin
if(reset)
counter_down<=4'hf;
else
counter_down<=counter_down-4'd1;
end
assign counter = counter_down;
endmodule 

### RTL DOWN COUNTER
<img width="476" alt="cdcdow" src="https://user-images.githubusercontent.com/93427923/169742023-7621f949-1da5-49c9-b3f9-71303237b94c.png">


### TIMING DIGRAMS FOR COUNTER  

<img width="943" alt="ttcdow" src="https://user-images.githubusercontent.com/93427923/169742032-55d4804f-1f6c-49b1-a035-b5468dd8efea.png">

### TRUTH TABLE 

![cdow](https://user-images.githubusercontent.com/93427923/169742037-69103d9c-6a87-45de-a4db-b3b6d922cba0.jpg)

### RESULTS 
4 bit up and down counters are implemented and its functionality is validated successfully.
