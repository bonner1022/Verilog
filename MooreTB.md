# Moore Machine Testbench Code
```
module Moore_Sequ_tb();
  reg clk, reset;
  reg [1:0] ain;
  wire yout;

  Moore_Sequ DUT (.clk(clk), .reset(reset), .ain(ain), .yout(yout));

  initial
  begin
    reset = 1; ain = 2'b00;      // initialize input values, output = 0
    #20 reset = 0;                // state0 
    #20 ain = 2'b11;              // state3
    #10 ain = 2'b10;              // state2
    #10 ain = 2'b00;              // state6, output flips to 1
    #20 ain = 2'b10;              // state2, output stays constant
    #10 ain = 2'b00;              // state6, output flips to 0
    #10 ain = 2'b11;              // state3
    #10 ain = 2'b00;              // state5, output = 1
    #10 ain = 2'b01;              // state1, output stays constant
    #10 ain = 2'b00;              // state4, output =0
    #10 ain = 2'b10;              // state2, output stays constant
    #10 ain = 2'b11;              // state3, output stays constant
    #10 ain = 2'b00;              // state5, output = 1
    #10 reset = 1;                // state0, output = 0
    #10 reset = 0;                // stay in state0, output constant
    #10 ain = 2'b10;              // state2, output stays constant
    #30 ain = 2'b00;              // state6, output flips to 1
  end

  initial
  begin
    clk = 0;
    forever
      #5 clk = ~clk;              // oscillate clock every 5 ns
  end
endmodule
```
