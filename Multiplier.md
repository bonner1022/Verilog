# Multiplier Code

```
module multiplier(
  input clk,
  input [2:0] cand, plier,
  output [5:0] prod
  );

  reg [2:0] res1;            // temporary placeholder for addition rounds
  reg [3:0] res2;            // temporary placeholder for addition rounds
  reg [4:0] res3;              // temporary placeholder for addition rounds
  wire [4:0] temp;            // temporary output of first multiplication round
  wire [5:0] sec;            // temporary output of second multiplication round
  wire c0, c1, c2, c3, t0, t1, x0, x1, x2, x3, x4;      // output variables

  always @ (posedge clk)    // multiply first bit
    if (plier[0] == 1)
      res1 = cand[2:0];
    else
      res1 = 0;

  always @ (posedge clk)      // multiply second bit
    if (plier[1] == 1)
      res2 = {cand[2:0], 1'b0};
    else
      res2 = 0;

    full_adder F1(res1[0], res2[0], 1'b0, temp[0], c0);
    full_adder F2(res1[1], res2[1], c0, temp[1], c1);
    full_adder F3(res1[2], res2[2], c1, temp[2], c2);
    full_adder F4(1'b0, res2[3], c2, temp[3], c3);
    assign temp[4] = c3;

  always @ (posedge clk)          // multiply third bit
    if (plier[2] == 1)
      res3 = {cand[2:0], 2'b0};
    else
      res3 = 0;

    full_adder A1(temp[0], res3[0], 1'b0, sec[0], x0);
    full_adder A2(temp[1], res3[1], x0, sec[1], x1);
    full_adder A3(temp[2], res3[2], x1, sec[2], x2);
    full_adder A4(temp[3], res3[3], x2, sec[3], x3);
    full_adder A5(temp[4], res3[4], x3, sec[4], x4);
    assign sec[5] = x4;

  assign prod = sec;
endmodule  

module full_adder(
  input a, b, cin,
  output sum, cout
  );

  assign sum = cin ^ (a ^ b);
  assign cout = (a & b) | (a & cin) | (b & cin);
endmodule
```
