# Verilog Projects
This repository shows projects where we used Verilog to design hardware components.

## Multiplier
The first component that we design is a simple 3-bit multiplier. It takes two 3 bit inputs(_cand, plier_) and produces one 6 bit output(_prod_) and also a clock input. To facilitate the multiplication, we utilized registers to hold calculated values for later use and wires to store temporary data. The clock was used to provide a constant interval of time to perform calculations for simulation purposes. 

For the multiplier, we utilize a full adder that handles binary addition of 1 bit. The adder will take in 3 inputs: the bits that we are adding(_a, b_) and also a carryin(_cin_) bit. It will have 2 outputs: the sum of addition(_sum_) and also a carryout bit(_cout_). According to binary addition, the carryout bit is activated if 2 bits equal to 1. 

The full solution for the multiplier and adder is shown in the figure named **Multiplier.md_**. We also added a testbench file (**_MultiplierTB.md_** and simulation results(**_Simulation.png_**) to verify the logic. 
