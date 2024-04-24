# VLSI-LAB-EXP-4
## SIMULATION AND IMPLEMENTATION OF SEQUENTIAL LOGIC CIRCUITS

## AIM: 
 To simulate and synthesis SR, JK, T, D - FLIPFLOP, COUNTER DESIGN using Xilinx ISE.

## APPARATUS REQUIRED:

Xilinx 14.7
Spartan6 FPGA
  
## PROCEDURE:
STEP:1  Start  the Xilinx navigator, Select and Name the New project.
STEP:2  Select the device family, device, package and speed.       
STEP:3  Select new source in the New Project and select Verilog Module as the Source type.                       
STEP:4  Type the File Name and Click Next and then finish button. Type the code and save it.
STEP:5  Select the Behavioral Simulation in the Source Window and click the check syntax.                       
STEP:6  Click the simulation to simulate the program and  give the inputs and verify the outputs as per the truth table.               
STEP:7  Select the Implementation in the Sources Window and select the required file in the Processes Window.
STEP:8  Select Check Syntax from the Synthesize  XST Process. Double Click in the  FloorplanArea/IO/Logic-Post Synthesis process in the User Constraints process group. UCF(User constraint File) is obtained. 
STEP:9  In the Design Object List Window, enter the pin location for each pin in the Loc column Select save from the File menu.
STEP:10 Double click on the Implement Design and double click on the Generate Programming File to create a bitstream of the design.(.v) file is converted into .bit file here.
STEP:11  On the board, by giving required input, the LEDs starts to glow light, indicating the output.


## SR FLIPFLOP:

### Logic Diagram:

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/77fb7f38-5649-4778-a987-8468df9ea3c3)

### Verilog Code:

```
module srff(s,r,clk,rst,q);
input s,r,clk,rst;
output reg q;
always@(posedge clk)
begin
if(rst==1)
q=0;
else
begin
case({s,r})
2'b00:q=q;
2'b01:q=0;
2'b10:q=1;
2'b11:q=1'bX;
endcase
end
end
endmodule
```

### Output:

![image](https://github.com/Rakeshraki-007/VLSI-LAB-EXP-4/assets/161815387/e57631ff-b4fb-47c2-b54a-cbac7d344c45)



## JK FLIPFLOP:

### Logic Diagram:

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/1510e030-4ddc-42b1-88ce-d00f6f0dc7e6)

### Verilog Code:

```
module jkff(j,k,clk,rst,q);
input j,k,clk,rst;
output reg q;
always@(posedge clk)
begin
if(rst==1)
q=0;
else
begin
case({j,k})
2'b00:q=q;
2'b01:q=0;
2'b10:q=1;
2'b11:q=~q;
endcase
end
end
endmodule
```

### Output:

![image](https://github.com/Rakeshraki-007/VLSI-LAB-EXP-4/assets/161815387/c03ffd2a-459c-4c8d-9ede-eb8d70d736cc)



## T FLIPFLOP:

### Logic Diagram:

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/7a020379-efb1-4104-85ee-439d660baa08)

### Verilog Code:

```
module tff(clk,rst,t,q);
input clk,rst,t;
output reg q;
always @(posedge clk)
begin
if (rst==1)
q=1'b0;
else if (t==0)
q=q;
else
q=~q;
end
endmodule
```

### Output:

![image](https://github.com/Rakeshraki-007/VLSI-LAB-EXP-4/assets/161815387/9a479fd6-3923-4cd3-aef6-b93123b29af9)



## D FLIPFLOP:

### Logic Diagram:

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/dda843c5-f0a0-4b51-93a2-eaa4b7fa8aa0)

### Verilog Code:

```
module dff(d,clk,rst,q);
input d,clk,rst;
output reg q;
always @(posedge clk)
begin
if (rst==1)
q=1'b0;
else
q=d;
end
endmodule
```

### Output:

![image](https://github.com/Rakeshraki-007/VLSI-LAB-EXP-4/assets/161815387/6013e07d-d982-4e1d-b385-b9242806f063)

## COUNTER:

### Logic Diagram:

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/a1fc5f68-aafb-49a1-93d2-779529f525fa)

## Updown Counter:

### Logic Diagram:

![image](https://github.com/Rakeshraki-007/VLSI-LAB-EXP-4/assets/161815387/d90433a2-1e8c-4c29-8500-fba807b45891)




### Verilog Code:

```
module udc(clk,rst,updown,out);
input clk,rst,updown;
output reg [3:0]out;
always@(posedge clk)
begin
if (rst==1)
out=4'b0000;
else if(updown==1)
out=out+1;
else
out=out-1;
end
endmodule
```

### Output:

![image](https://github.com/Rakeshraki-007/VLSI-LAB-EXP-4/assets/161815387/41169089-0ed7-4da2-bec0-b794946dc108)


## Mod-10 Counter:

### Logic Diagram:

![image](https://github.com/Rakeshraki-007/VLSI-LAB-EXP-4/assets/161815387/70d78875-431f-4ec1-8ac8-0ed0be5d0485)




### Verilog Code:

```
module mod10(clk,rst,out);
input clk,rst;
output reg [3:0]out;
always@(posedge clk)
begin
if (rst==1 | out==4'b1001)
out=4'b0000;
else
out=out+1;
end
endmodule
```

### Output:

![image](https://github.com/Rakeshraki-007/VLSI-LAB-EXP-4/assets/161815387/4b7aee89-e4b2-4028-9e0e-7d5f33652e08)


## Ripple Carry Counter:

### Logic Diagram:

![image](https://github.com/Rakeshraki-007/VLSI-LAB-EXP-4/assets/161815387/d7b51766-9899-47e6-9c31-b11780754f9b)



![image](https://github.com/Rakeshraki-007/VLSI-LAB-EXP-4/assets/161815387/42665fce-6854-4b30-9fe1-3331a60b6954)




### Verilog Code:

```
module tff(q,clk,rst);
input clk,rst;
output q;
wire d;
dff df1(q,d,clk,rst);
not n1(d,q);
endmodule

module dff(q,d,clk,rst);
input d,clk,rst;
output q;
reg q;
always @(posedge clk or posedge rst)
begin
if (rst)
q=1'b0;
else 
q=d;
end
endmodule

module rcc(clk,rst,q);
input clk,rst;
output [3:0]q;
tff tf1(q[0],clk,rst);
tff tf2(q[1],q[0],rst);
tff tf3(q[2],q[1],rst);
tff tf4(q[3],q[2],rst);
endmodule
```

### Output:

![image](https://github.com/Rakeshraki-007/VLSI-LAB-EXP-4/assets/161815387/a572f811-3230-4f28-ad2e-d5a255659cf5)

## RESULT:
 Hence SR, JK, T, D - FLIPFLOP, COUNTER DESIGN are simulated and synthesised using Xilinx ISE.


