# Mealy Machine

```
module mealy_sequ(
  input clk, reset, ain,        
  output reg [3:0] count,
  output reg yout
  );  
  reg [1:0] state, nextstate;            
  parameter S0=2'b00, S1=2'b01, S2=2'b10;      // output state representation

  always @ (posedge clk or posedge reset)      // next state running on clock
  begin
    if (reset)                        // reset to state0 on positive reset 
      state <= S0;
    else
      state <= nextstate;            // advance to next state on positive clock 
  end

  always @ (state or ain)              // next state depend on user input
  begin
    nextstate = S0;                // start at state0
    case(state)      
      S0: if (ain)
            nextstate = S1;        
          else
            nextstate = S0;
      S1: if (ain)
            nextstate = S2;
          else
            nextstate = S1;
      S2: if (ain)
            nextstate = S0;
          else
            nextstate = S2;
    endcase
  end

  always @ (posedge clk)          // activate yout if in state2
  begin
    case(state)
      S0: yout = 0;
      S1: yout = 0;
      S2: if (ain)
            yout = 1;
          else
            yout = 0;
    endcase
  end

  initial        // initialize counter and yout
  begin
    count = 4'b0;
    yout = 1;
  end

  always @ (posedge clk or posedge reset)    // increment counter on each state change
  begin
    if (reset)
      count = 4'b0000;
    else if (ain)
      count = count + 1;
  end
endmodule
```
