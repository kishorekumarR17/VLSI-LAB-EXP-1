SIMULATE OF LOGIC GATES,ADDERS AND SUBTRACTOR

AIM: To simulate and synthesis Logic Gates,Adders and Subtractor using vivado.

APPARATUS REQUIRED: vivado 2023.1 software.

PROCEDURE: 

1. Open Vivado: Launch Xilinx Vivado software on your computer.

2. Create a New Project: Click on "Create Project" from the welcome page or navigate through "File" > "Project" > "New".

3. Project Settings: Follow the prompts to set up your project. Specify the project name, location, and select RTL project type.

4. Add Design Files: Add your Verilog design files to the project. You can do this by right-clicking on "Design Sources" in the Sources window, then selecting "Add Sources". Choose your Verilog files from the file browser.

5. Specify Simulation Settings: Go to "Simulation" > "Simulation Settings". Choose your simulation language (Verilog in this case) and simulation tool (Vivado Simulator).

6. Run Simulation: Go to "Flow" > "Run Simulation" > "Run Behavioral Simulation". This will launch the Vivado Simulator and compile your design for simulation.

7. Set Simulation Time: In the Vivado Simulator window, set the simulation time if it's not set automatically. This determines how long the simulation will run.

8. Run Simulation: Start the simulation by clicking on the "Run" button in the simulation window.

9. View Results: After the simulation completes, you can view waveforms, debug signals, and analyze the behavior of your design.

Logic Diagram :

Logic Gates:
![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/ee17970c-3ac9-4603-881b-88e2825f41a4)

Program:

module allgates(a,b,y1,y2,y3,y4,y5,y6,y7);
input a,b;
output y1,y2,y3,y4,y5,y6,y7;
and g1(y1,a,b);
or  g2(y2,a,b);
not g3(y3,a);
xor g4(y4,a,b);
xnor g5(y5,a,b);
nand g6(y6,a,b);
nor g7(y7,a,b);
endmodule

Output:

![image](https://github.com/Siva1309/VLSI-LAB-EXP-1/assets/166374356/a3bbc017-03fd-4174-84c6-806d07729564)


Half Adder:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/0e1ecb96-0c25-4556-832b-aeeedfdfe7b9)

VERILOG CODE:

module halfadder(a,b,s,c);
input a,b;
output s,c;
xor (s,a,b);
and (c,a,b);
endmodule

Output:

![image](https://github.com/Siva1309/VLSI-LAB-EXP-1/assets/166374356/210b7dda-5a45-4a6e-9f65-8ab0cda1321d)
![image](https://github.com/Siva1309/VLSI-LAB-EXP-1/assets/166374356/78b136f9-9ffd-4ec5-86e9-3177ab8c5e2c)



Full adder:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/9bb3964c-438f-469d-a3de-c1cca6f323fb)

VERILOG CODE:

module fulladder(a,b,c,sum,carry);
input a,b,c;
output sum,carry;
wire w1,w2,w3;
xor g1(w1,a,b);
xor g2(sum,w1,c);
and g3(w2,a,b);
and g4(w3,w1,c);
or g5(carry,w3,w2);
endmodule

Output:

![image](https://github.com/Siva1309/VLSI-LAB-EXP-1/assets/166374356/c5b32b8c-5f60-4410-b511-e27c5a288e72)
![image](https://github.com/Siva1309/VLSI-LAB-EXP-1/assets/166374356/5adcb678-6dd7-48c5-9b61-bbfc1d4858e5)



Half Subtractor:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/731470b7-eb4e-49f8-8bb7-2994052a7184)

VERILOG CODE:

module hasub(a,b,difference,borrow);
input a,b;
output difference,borrow;
wire w1;
xor g1(difference,a,b);
not g2(w1,a);
and g3(borrow,w1,b);
endmodule

Output:

![image](https://github.com/Siva1309/VLSI-LAB-EXP-1/assets/166374356/d37902f0-6525-458c-87f6-918a8d50f558)
![image](https://github.com/Siva1309/VLSI-LAB-EXP-1/assets/166374356/188e2e75-27d7-4306-93e7-afac9e92fd9a)


Full Subtractor:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/d66f874b-c1f2-44b3-a035-7149b56430c1)

VERILOG CODE:

module fullsub(a,b,c,difference,borrow);
input a,b,c;
output difference,borrow;
wire w1,w2,w4,w5,w6;
xor x1(w2,a,b);
xor x2(difference,w2,c);
not n1(w1,a);
and a1(w5,w1,b);
not n2(w4,w2);
and a2(w6,w4,c);
or o1(borrow,w5,w6);
endmodule

Output:

![image](https://github.com/Siva1309/VLSI-LAB-EXP-1/assets/166374356/dbb730b5-01a8-464b-8c86-cd30b1bec59c)
![image](https://github.com/Siva1309/VLSI-LAB-EXP-1/assets/166374356/2c748dff-93a1-47c2-b94f-5caf6d658585)

4 Bit Ripple Carry Adder

VERILOG CODE:

module rippe_adder(S, Cout, X, Y,Cin);
input [3:0] X, Y;// Two 4-bit inputs
input Cin;
output [3:0] S;
output Cout;
wire w1, w2, w3;
  // instantiating 4 1-bit full adders in Verilog
fulladder u1(S[0], w1,X[0], Y[0], Cin);
fulladder u2(S[1], w2,X[1], Y[1], w1);
fulladder u3(S[2], w3,X[2], Y[2], w2);
fulladder u4(S[3], Cout,X[3], Y[3], w3);
endmodule
module fulladder(S, Co, X, Y, Ci);
 input X, Y, Ci;
 output S, Co;
 wire w1,w2,w3;
 //Structural code for one bit full adder
 xor G1(w1, X, Y);
 xor G2(S, w1, Ci);
 and G3(w2, w1, Ci);
 and G4(w3, X, Y);
 or G5(Co, w2, w3);
endmodule

Output:

![image](https://github.com/Siva1309/VLSI-LAB-EXP-1/assets/166374356/3d18b226-a0d7-41cd-9191-41366946886c)
![image](https://github.com/Siva1309/VLSI-LAB-EXP-1/assets/166374356/07ece7fd-bc63-40a5-9dc8-17ac56904848)



8 Bit Ripple Carry Adder

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/7385a408-40a5-4203-8050-b72818622d79)

VERILOG CODE:

module rca(a,b,cin,sum,carry);
input a,b,cin;
output sum,carry;
wire w1,w2,w3;
xor g1(w,a,b);
xor g2(sum,w1,cin);
and g3(w2,a,b);
and g4(w3,w1,cin);
or g5(carry,w3,w2);
endmodule

module ripplecarry(a,b,cin,sum,carry);
input [3:0]a,b;
input cin;
output [3:0]sum,carry;
wire c1,c2,c3;
rca g1(.a(a[0]),.b(b[0]),.cin(cin),.s(sum[0]),.carry(c1));
rca g2(.a(a[1]),.b(b[1]),.cin(c1),.s(sum[1]),.carry(c2));
rca g3(.a(a[2]),.b(b[2]),.cin(c2),.s(sum[2]),.carry(c3));
rca g4(.a(a[3]),.b(b[3]),.cin(c3),.s(sum[3]),.carry(cout));
endmodule

Output:

![image](https://github.com/Siva1309/VLSI-LAB-EXP-1/assets/166374356/27cace3a-114e-44e6-ac0d-1ee8441b9383)
![image](https://github.com/Siva1309/VLSI-LAB-EXP-1/assets/166374356/c7b84ee8-a997-4caa-87aa-cb06e456999c)


RESULT:
    Thus the simulation and synthesis of Logic Gates, Adders and Subtractor using vivado is simulated successfully.
