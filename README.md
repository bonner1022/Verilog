# Verilog Projects
This repository shows projects where we used Verilog to design hardware components.

## Multiplier
The first component that we design is a simple 3-bit multiplier. It takes two 3 bit inputs(_cand, plier_) and produces one 6 bit output(_prod_) and also a clock input. To facilitate the multiplication, we utilized registers to hold calculated values for later use and wires to store temporary data. The clock was used to provide a constant interval of time to perform calculations for simulation purposes. 

For the multiplier, we utilize a full adder that handles binary addition of 1 bit. The adder will take in 3 inputs: the bits that we are adding(_a, b_) and also a carryin(_cin_) bit. It will have 2 outputs: the sum of addition(_sum_) and also a carryout bit(_cout_). According to binary addition, the carryout bit is activated if 2 bits equal to 1. 

The full solution for the multiplier and adder is shown in the figure named **Multiplier.md_**. We also added a testbench file (**_MultiplierTB.md_** and simulation results(**_Simulation.png_**) to verify the logic. 


## Sequential Circuits
For another project, we designed sequential circuits, which are circuits that consists of various different inputs and outputs(states). Each state represents the logic of each output are represented as previous, current or next. The current is output of current input, previous state is the state that we are leaving and the next state is dependent on current state and potential inputs. We design two different circuits, a Mealy machine and a Moore machine. A Mealy machine's next state is dependent on both current state and the current input, while a Moore machine changes state solely based on current state. 

### Mealy Machine
It changes state based on clock transitions but can also change asynchronously whenever current input changes. The design takes 3 inputs(_clk, reset, ain_) where _ain_ represents user input and _reset_ is an action that resets the circuit back to the first state. We have two outputs(_count, yout_) where _count_ represents a counter of how many times we change states, but turns to 0 if _reset_ becomes active. Output _yout_ becomes 1 only if current state is in the final state of the circuit and _ain_ is inputted as 1. We use 2-bit registers to represent _state_ and _nextstate_. Parameters are used to initialize the binary values for each state as follows: 00 as State0, 01 as State1 and 10 as State2. The circuit goes from State0 -> State1 -> State2 and starts over at State0 after we pass State2. The solution is shown in **_MealyMachine.md_**.   
