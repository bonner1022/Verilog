# Moore Machine
```
module moore_sequ(
  input clk, reset, 
  input [1:0] ain,        
  output reg yout
  );  
  reg [2:0] state, nextstate;            
  parameter S0=3'b000, S1=3'b001, S2=3'b010, S3=3'b011, S4=3'b100, S5=3'b101, S6=3'b111;   // output states 

  always @ (posedge clk or posedge reset)      // next state running on clock
  begin
    if (reset)                        // reset to state0 on positive reset 
      state <= S0;
    else
      state <= nextstate;            // advance to next state on positive clock 
  end

  always @ (state or ain)              // next state logic
  begin
    nextstate = S0;                // start at state0
    case(state)      
      S0: if (ain==2'b00)          // state0
            nextstate = S0;        
          else if (ain==2'b01)      // state1
            nextstate = S1;
          else if (ain==2'b10)      // state2
            nextstate = S2;
          else
            nextstate = S3;        // state3
      S1: if (ain==2'b00)          // state4
            nextstate = S4;        
          else if (ain==2'b01)
            nextstate = S1;
          else if (ain==2'b10)
            nextstate = S2;
          else
            nextstate = S3;
      S2: if (ain==2'b00)        // state6
            nextstate = S6;        
          else if (ain==2'b01)
            nextstate = S1;
          else if (ain==2'b10)
            nextstate = S2;
          else
            nextstate = S3;
      S3: if (ain==2'b00)      // state5
            nextstate = S5;        
          else if (ain==2'b01)
            nextstate = S1;
          else if (ain==2'b10)
            nextstate = S2;
          else
            nextstate = S3;
      S4: if (ain==2'b00)  
            nextstate = S0;        
          else if (ain==2'b01)
            nextstate = S1;
          else if (ain==2'b10)
            nextstate = S2;
          else
            nextstate = S3;
      S5: if (ain==2'b00)
            nextstate = S0;        
          else if (ain==2'b01)
            nextstate = S1;
          else if (ain==2'b10)
            nextstate = S2;
          else
            nextstate = S3;
      S6: if (ain==2'b00)
            nextstate = S0;        
          else if (ain==2'b01)
            nextstate = S1;
          else if (ain==2'b10)
            nextstate = S2;
          else
            nextstate = S3;
    endcase
  end

  initial 
    yout = 0;
  always @ (state or reset)        // output logic
  begin
    case(state)
      S0: if(reset)
            yout = 0;
          else
            yout = yout;
      S1: if(reset)
            yout = 0;
          else
            yout = yout;
      S2: if(reset)
            yout = 0;
          else
            yout = yout;
      S3: if(reset)
            yout = 0;
          else
            yout = yout;
      S4: yout = 0;
      S5: if(reset)
            yout = 0;
          else
            yout = 1;
      S6: if(reset)
            yout = 0;
          else
            yout = -yout;
    endcase
  end
endmodule
```
