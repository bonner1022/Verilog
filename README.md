# Verilog Projects
This repository shows projects where we used Verilog to design hardware components.

## Multiplier
The first component that we design is a simple 3-bit multiplier. It takes two 3 bit inputs(_cand, plier_) and produces one 6 bit output(_prod_) and also a clock input. To facilitate the multiplication, we utilized registers to hold calculated values for later use and wires to store temporary data. The clock was used to provide a constant interval of time to perform calculations for simulation purposes. 

For the multiplier, we utilize a full adder that handles binary addition of 1 bit. The adder will take in 3 inputs: the bits that we are adding(_a, b_) and also a carryin(_cin_) bit. It will have 2 outputs: the sum of addition(_sum_) and also a carryout bit(_cout_). According to binary addition, the carryout bit is activated if 2 bits equal to 1. 

The full solution for the multiplier and adder is shown in the figure named **Multiplier.md_**. We also added a testbench file (**_MultiplierTB.md_** and simulation results(**_Simulation.png_**) to verify the logic. 


## Sequential Circuits
For another project, we designed sequential circuits, which are circuits that consists of various different inputs, outputs and states. Each state represents the current status of the circuit at any given time. We keep track of current state and use logic to determine the next state. These circuits also produce an output, depending on current state and other inputs. Using Verilog, we designed two different circuits, a Mealy machine and a Moore machine. A Mealy machine's output is dependent on both current state and the current input, while a Moore machine's output is solely based on current state. We completed state diagrams for each circuit. 

### Mealy Machine
We designed a circuit with 3 states represented by 2-bit parameters. The binary values for each state as follows: 00 as State0, 01 as State1 and 10 as State2. The circuit takes three 1-bit inputs(_clk, reset, ain_) where _ain_ represents user input, _reset_ will set the circuit back to state0 and the _clock_ keeps gives the circuit a timing feature. We have a 4-bit output(_count_) which represents a counter of how many times we change states, and 1-bit output(_yout_) as the output of the circuit. The circuit synchronously passes from State0 -> State1 -> State2 and starts over at State0 after State2, but can also asynchronously change state baseed on user input. This is a Mealy machine, so output at state0 and state1 depend on the current state, but output at state2 depends on what _ain_ is at the time. For the rest of the code We use 2-bit registers to represent _state_ and _nextstate_. The solution is shown in **_MealyMachine.md_** and the state diagram is shown in **_MealyState.png_**. We also created a testbench file(**_MealyTB.md_**) and the resulting simulation(**_MealySim.png_**).

### Moore Machine
For the Moore machine, we introduced six states represented by 3-bits with the following binary values: 000 as State0, 001 as State1, 010 as State2, 011 as State3, 100 as State4, 101 as State5 and 111 as State6. We keep track of current _state_ and _nextstate_ using 3-bit registers. We have the same 1-bit inputs(_clk_, _reset_) and output(_yout_) as with the Mealy Machine. However, this time we implement 2-bit user input(_ain_) to determine state changes. A case statement is used to determine next state dependent on current state. Output is calculated solely on current state and this is shown in the state diagram, **_MooreState.png_** and code shown in **_MooreMachine.md_**. We also created a testbench file(**_MooreTB.md_**) and the resulting simulation(**_MooreSim.png_**).
