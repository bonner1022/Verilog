# Full Adder Code

```
module full_adde(
  input a, b, cin,
  output sum, cout
  );

  assign sum = cin ^ (a ^ b);
  assign cout = (a & b) | (a & cin) | (b & cin);
endmodule
```
