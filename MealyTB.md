# Mealy Machine Testbench Code
```
module Mealy_Sequ_tb();
  reg clk, ain, reset;
  wire yout;
  wire [3:0] count;
  mealy_sequ DUT (.clk(clk), .ain(ain), .reset(reset), .yout(yout), .count(count));

  initial
  begin
    ain = 0; reset = 0; clk = 0;      // initialize input values
    #40 ain = 1;                      // transfer to state1, increment count
    #20 ain = 0;
    #60 ain = 1;                      // transfer to state2, increment count
    #40 ain = 0;
    #20 ain = 1;                      // back to state0, increment count
    #15 reset = 1;                    // override circuit, reset count
  end

  initial
  begin
    clk = 0;
    forever
    #5 clk = -clk;              // oscillate clock every 5 ns
  end
endmodule
```
