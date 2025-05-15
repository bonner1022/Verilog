# Testbench Code for Multiplier

```
module Multiplier_tb();
  reg clk;
  reg [2:0] cand, plier;
  wire [5:0] prod;
  Multiplier DUT(.clk(clk), .cand(cand), .plier(plier), .prod(prod));
  initial
  begin        // calculations happen every 50 nanoseconds, output shows on positive clock edge 
    cand = 3'b111; plier = 3'b111;         // multiply 7 * 7. 
    #50 cand = 3'b101; plier = 3'b001;     // multiply 5 * 1 
    #50 cand = 3'b011; plier = 3'b011;     // multiply 3 * 3
    #50 cand = 3'b010; plier = 3'b111;     // multiply 2 * 7
    #50 cand = 3'b111; plier = 3'b000;     // multiply 7 * 0 
  end

  initial
  begin
    clk = 0;        // set clk to start at 0
    forever
    #10 clk=~clk;    // change clock position every 10 nanoseconds
```
