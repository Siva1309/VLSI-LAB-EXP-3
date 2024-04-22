**SIMULATION AND IMPLEMENTATION OF MULTIPLIER** 

**AIM:**
 To simulate and synthesis multiplier using vivado.

**APPARATUS REQUIRED:**
vivado 2023.1 software.

**PROCEDURE:**

1. Open Vivado: Launch Xilinx Vivado software on your computer.

2. Create a New Project: Click on "Create Project" from the welcome page or navigate through "File" > "Project" > "New".

3. Project Settings: Follow the prompts to set up your project. Specify the project name, location, and select RTL project type.

4. Add Design Files: Add your Verilog design files to the project. You can do this by right-clicking on "Design Sources" in the Sources window, then selecting "Add Sources". Choose your Verilog files from the file browser.

5. Specify Simulation Settings: Go to "Simulation" > "Simulation Settings". Choose your simulation language (Verilog in this case) and simulation tool (Vivado Simulator).

6. Run Simulation: Go to "Flow" > "Run Simulation" > "Run Behavioral Simulation". This will launch the Vivado Simulator and compile your design for simulation.

7. Set Simulation Time: In the Vivado Simulator window, set the simulation time if it's not set automatically. This determines how long the simulation will run.

8. Run Simulation: Start the simulation by clicking on the "Run" button in the simulation window.

9. View Results: After the simulation completes, you can view waveforms, debug signals, and analyze the behavior of your design.
    
**Logic Diagram**

2 bit Multiplier

![image](https://github.com/navaneethans/VLSI-LAB-EXP-3/assets/6987778/7713750f-65e6-41c0-8082-5005eac4031c)

VERILOG CODE:
```
module ha(a,b,sum,carry);
input a,b;
output sum,carry;
assign sum=a^b;
assign carry=a&b;
endmodule

module multiplier2bit(a,b,c);
input [1:0]a,b;
output [3:0]c;
wire w1,w2,w3,w4;
and g1(c[0],a[0],b[0]);
and g2(w1,a[0],b[1]);
and g3(w2,a[1],b[0]);
and g4(w4,a[1],b[0]);
ha ha1(w1,w2,c[1],w3);
ha ha2(w3,w4,c[2],c[3]);
endmodule
```

OUTPUT WAVEFORM:

![image](https://github.com/Siva1309/VLSI-LAB-EXP-3/assets/166374356/5c829840-1928-4ae4-bffe-178e06862e84)


**4 Bit Multiplier**

![image](https://github.com/navaneethans/VLSI-LAB-EXP-3/assets/6987778/d95215dd-8cf1-4e08-93cc-96adfdd7fbdc)

VERILOG CODE:
```
module halfadder(a,b,s,c);
input a,b;
output s,c;
xor (s,a,b);
and (c,a,b);
endmodule

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

module mul(x,y,z);
input [3:0]x,y;
output [7:0]z;
wire [17:1]w;
and (z[0],x[0],y[0]);
ha ha1(x[1]&y[0],x[0]&y[1],z[1],w[1]);
fa fa1(x[2]&y[0],x[1]&y[1],w[1],w[5],w[2]);
fa fa2(x[3]&y[0],x[2]&y[1],w[2],w[6],w[3]);
ha ha2(x[3]&y[1],w[3],w[7],w[4]);
ha ha3(w[5],x[0]&y[2],z[2],w[8]);
fa fa3(w[6],x[1]&y[2],w[8],w[12],w[9]);
fa fa4(w[7],x[2]&y[2],w[9],w[13],w[10]);
fa fa5(w[4],x[3]&y[2],w[10],w[14],w[11]);
ha ha4(w[12],x[0]&y[3],z[3],w[15]);
fa fa6(w[13],x[1]&y[3],w[15],z[4],w[16]);
fa fa7(w[14],x[2]&y[3],w[16],z[5],w[17]);
fa fa8(w[11],x[3]&y[3],w[17],z[6],z[7]);
endmodule
```

OUTPUT WAVEFORM:

![image](https://github.com/Siva1309/VLSI-LAB-EXP-3/assets/166374356/7b863561-2e09-486d-bb38-cbf062e9d5c9)

Result: 
  Thus the simulation and synthesis of multiplier using vivado software is done successfully.



