# EXP.NO.04
# DATE:02/04/2024
# SIMULATION AND IMPLEMENTATION OF SEQUENTIAL LOGIC CIRCUITS
# AIM: 
 To simulate and synthesis SR, JK, T, D - FLIPFLOP, COUNTER DESIGN using Xilinx ISE.
# APPARATUS REQUIRED:
Xilinx 14.7
Spartan6 FPGA
# PROCEDURE:
```
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
```
**LOGIC DIAGRAM**
# SR FLIPFLOP
![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/77fb7f38-5649-4778-a987-8468df9ea3c3)
# CODE:
```
module srff(s,r,clk,reset,q);
input s,r,clk,reset;
output reg q;
always@(posedge clk)
begin
if(reset==1)
q =1'b0;
else 
begin
case({s,r})
 2'b00: q = q;
 2'b01: q = 1'b0;
 2'b10: q = 1'b1;
 2'b11: q = 1'bx;
 default:q = ~q;
endcase
end 
end
endmodule
```
# OUTPUT:
![image](https://github.com/THARUN729/VLSI-LAB-EXP-4/assets/161407766/6618db3f-a7fc-4968-a295-3df9f570202d)
# JK FLIPFLOP
![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/1510e030-4ddc-42b1-88ce-d00f6f0dc7e6)
# CODE:
```
module jk_ff(j,k,clk,reset,q);
input j,k,clk,reset;
output reg q;
always@(posedge clk)
begin
if(reset==1)
q =1'b0;
else 
begin
case({j,k})
 2'b00: q = q;
 2'b01: q = 1'b0;
 2'b10: q = 1'b1;
 2'b11: q = ~q;
 default:q =1'b0;
endcase
end 
end
endmodule
```
# OUTPUT:
![image](https://github.com/THARUN729/VLSI-LAB-EXP-4/assets/161407766/4615a6e3-dc9d-455e-97f3-5cf07cc72a40)
# T FLIPFLOP
![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/7a020379-efb1-4104-85ee-439d660baa08)
# CODE:
```
module tff(clk,rst,j,q);
input clk,rst,j;
output reg q;
always@(posedge clk)
begin
case(t)
1'b0:q=q;
1'b1:q=~q;
default=q=1'b0;
endcase
end
endmodule
```
# OUTPUT:
![image](https://github.com/THARUN729/VLSI-LAB-EXP-4/assets/161407766/90772a31-d97d-471c-80b9-c4fe8db5c70b)
# D FLIPFLOP
![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/dda843c5-f0a0-4b51-93a2-eaa4b7fa8aa0)
# CODE:
```
module dff(clk,rst,d,q);
input clk,rst,d;
output reg q;
always@(posedge clk)
begin
if(rst==1)
q=1'b0;
else
q=d;
end
endmodule
```
# OUTPUT:
 ![image](https://github.com/THARUN729/VLSI-LAB-EXP-4/assets/161407766/bd568e3d-b577-47a7-91cd-20a8683666a9)
# COUNTER
![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/a1fc5f68-aafb-49a1-93d2-779529f525fa)
# UPDOWNCOUNTER
![image](https://github.com/THARUN729/VLSI-LAB-EXP-4/assets/161407766/2ea9c353-b930-48ec-abfa-cec85326830c)
# CODE:
```
module updown(clk,rst,up_down,count);
input clk,rst,up_down;
output reg[3:0]count;
always@(posedge clk)
begin
if(rst==1)
count <= 4'b0000;
else if (up_down == 1'b1)
count <= count + 1'b1;
else
count <= count-1'b1;
end
endmodule
```
# OUTPUT:
![image](https://github.com/THARUN729/VLSI-LAB-EXP-4/assets/161407766/dda8def0-194d-4fd1-aa7a-4cb768e75aa2)
# MOD10COUNTER
![image](https://github.com/THARUN729/VLSI-LAB-EXP-4/assets/161407766/08dbfc93-3d87-427f-bf63-fc5f4037b732)
# CODE:
```
module mod(clk,rst,count);
input clk,rst;
output reg[3:0]count;
always @(posedge clk)
begin
if(rst==1 | count==4'b1001)
count <= 4'b0000;
else
count <= count +1;
end
endmodule
```
# OUTPUT:
![image](https://github.com/THARUN729/VLSI-LAB-EXP-4/assets/161407766/dffaeca3-94c4-4117-9985-28547dedff41)
# RIPPLECARRYCOUNTER
![image](https://github.com/THARUN729/VLSI-LAB-EXP-4/assets/161407766/01edb485-2400-46aa-9af1-6546f3de9069)
![image](https://github.com/THARUN729/VLSI-LAB-EXP-4/assets/161407766/b0fb1762-9942-4d2f-80e1-5c94d343dd64)
# CODE:
```
module ripplecounter(clk,rst,q);
input clk,rst;
output [3:0]q;
tff tff1(q[0],clk,rst);
tff tff2(q[1],q[0],rst);
tff tff3(q[2],q[1],rst);
tff tff4(q[3],q[2],rst);
endmodule
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
always@(posedge clk or posedge rst)
begin
if(rst)
q=1'b10;
else
q=d;
end
endmodule
```
# OUTPUT:
![image](https://github.com/THARUN729/VLSI-LAB-EXP-4/assets/161407766/a710fe32-7b6e-4d5e-8a9c-91b172cbb06c)
# RESULT:
Hence thus given To simulate and synthesis SR, JK, T, D - FLIPFLOP, COUNTER DESIGN using vivado


